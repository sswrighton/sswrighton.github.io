---
layout: post
title:  "SQL Server Index Management"
date: "2019-09-06 19:00:00"
updated: "2019-03-03 15:46:00"
permalink: "/2018/09/sql-server-index-management.html"
author: Stephen Wrighton
description: 
categories: 
tags: [SQL, SQL Server]
author: 
    name: "Stephen Wrighton"
    url: "https://github.com/sswrighton"
    image: "https://www.gravatar.com/avatar/53a4066fb888b4a54fa1e650945e34a8?s=64&d=identicon&r=PG"
---

SQL Server is a complex thing, and when Always On Availability Groups are applied, that complexity increases (IMO) exponentially.   Of particular note is that Indexes are harder to work with. Well, not harder, but there's a greater overhead for their creation, and subsequently their rebuilding.  You should try to reorganize them as often as feasible. 

Now, I have a client, and this client has a large database. I believe it was sitting at just shy of 500GB the other day. That in and of itself is not an issue, the issue is that this database churns.  This client has a couple of hundred branches, each of which has an instance of this database, which is synchronized back up to the home office. Now, I neither designed nor built this application, but I am helping to monitor the health of the SQL Server, but that churn, that constant moving of data from those 100 or so branches that they had actually added to the system up to the Main Office did horrible, horrible things to the Index Files.  

A reorganization that knocks an index down to 21% fragmentation can be back up to 97% in just a few days. 

What was worse was that a weekly index reorg command was consistently failing.  Likewise, moving it to a nightly even, still caused it to fail. Or sometimes it wouldn't fail, it would just run all week until the weekly server reboot would force kill it.   Which is a terrible thing to happen to an index operation. 

So, I went and found Ola Hallengren's scripts (https://ola.hallengren.com/sql-server-index-and-statistics-maintenance.html) and placed them on the server.  And the behavior still occurred.  I cranked it up so that nothing would be done unless the fragmentation was 95% or greater, and it was still failing. 

And as this was going on, the system was becoming more and more unusable.  Queries were ending in minutes not seconds. 

Now, there were very few things I could impact in this situation. I could not change the database structure. I could not change the replication/synchronization methods. I could not change how the applications accessed data.  My hands were well and truly tied.  The only thing I could impact is the index maintenance task itself.  My solution was to add intelligence into the index maintenance.  

First,  I built a query which every couple of hours went out and gathered the physical statistics of the indexes and stored them in a table. Next I made a stored procedure which would add some intelligence into how it was determining which indexes needed to be reorganized. The logic followed these paths: 

	1. **Time Limit for Runs.** If the procedure has been running for more than 5 hours, end with success  This was done because we decided that fixing five indexes tonight and a different five the next night, is better than never completing. 
	2. **Ranking of Indexes.**  A big part of the logic is building the list of indexes, and then ranking them.  The system includes all of the indexes
		1. *Avg. Fragmentation.*  The value had to be greater than 0, and each index has an expected "start point" for consideration as an index to be reorged.  The first aspect of this is to be higher than the expected start off.  Then a higher rank is given to those with a higher difference between the start point and the Average Fragmentation.   For example, if Index 1 has a Start Point of 40 and an Avg Fragmentation of 60 and Index 2 has a Start Point of 80 and an Avg Fragmentation of 85, then Index 1 would have a greater rank since the difference is 20, verses Index 2's difference of 5. 
		2. *Priority.*  Some indexes are more important than others.  Basically, a table that is used more often in joins and look-ups, we just care more about its indexes than a history table that is only queried every second day. 
		3. *Pages.*  Items with more than a 1000 pages are given a higher rank, as we're less concerned with fragmentation when an index can be spread over a small number of pages. 
		4. *Age.*  If an index hasn't been reorganized in 30 days, then we increase its rank exponentially for every day pass 30.
	3. **Running.**  The system takes the ranked list, and walks it, issuing a reorg command for an explicit single index.


And in general, this worked beautifully.  Over the course of two months, I was able to slowly walk my Starting Point down from 80% to most have a Starting Point of 30%, while a few priority indexes have it set at 15%. 

Then a few days ago, I got a message from the client asking about a specific index that had apparently been escaping notice from the maintenance tasks.  So I started looking, and the first thing I discovered was that the historical logs recorded a 0% as the Average Fragmentation. Now, the database was clearly showing a 97.7% fragmentation, so I knew that there had to be something at issue with my script. 

So, I went and got the Object_ID for the table, and the Index Id for the index, and ran the Physical Statistics function (sys.dm_db_index_physical_stats) for the index in question. 

Which returned me 3 rows. 

I can admit I was not expecting that.  I had not really looked at the documentation for the query, and every index I had checked manually while building the query which performs the checks only returned one row.   Cognitive bias strikes again.  I had seen a behavior in my results sets, and had assumed that the behavior was only possible result set. 

So, off to Microsoft Docs I went (https://docs.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql?view=sql-server-2017).

Anyways, with the three distinct rows, the relevant differential was the alloc_unit_type_desc column.   According to MS Docs, that particular column can have 3 possible values:
- IN_ROW_DATA
- LOB_DATA
- ROW_OVERFLOW_DATA 

The IN_ROW_DATA is the one that all the tables have. And it's the 'important' one for what I was doing.  The other two dealt with large objects, and data from columns that have been pushed off-row (https://blogs.msdn.microsoft.com/sqlserverstorageengine/2006/12/13/more-undocumented-fun-dbcc-ind-dbcc-page-and-off-row-columns/). 

Now, how does this ties into the 0% Average Fragmentation that I was logging? Well its simple. I was  executing the command to get the statistics, and log those values atomically, and explicitly.  In other words, I logged each index in turn. 

Now, when looking at the query results from the Physical Stats function, I was storing the relevant values into a single variable prior to insert those values into my log.  Which means that I was keeping the last row returned.  Which was the LOB_DATA row, and thus had a 0% Average Fragmentation while the first row (IN_ROW_DATA) had the 97.7%.

A quick WHERE clause solved the issue, and my index maintenance once again started humming along nicely.