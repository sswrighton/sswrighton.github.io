---
layout: post
title: "ASP.Net DataCache"
date: "2019-03-11 19:00:00"
updated: "2019-03-11 19:15:00"
permalink: "/2019/03/aspnet-datacache.html"
author: Stephen Wrighton
description:
categories:
tags: [ASP.Net, IIS, Data, Cache]
---

I had to learn this particular technology under fire, because I had basically hosed something in the production version of an application. This particular application has rather tight release controls, and as such we have a DEV, STAGE and PRODUCTION versions running at all time.  

With that many versions of the code running, I needed quick, immediate, and highly visual ways of knowing exactly which version I am looking at at any time. So, back in 2014 when we were initially building it, we came to a decision to modify the header banner color based upon the location of the code at the time. So three CSS files, and a database flag, later I have custom colors (and banner images) based upon which database is getting connected to. 

Fast forward to late 2018. 

I'm working on the code to implement an important new feature as well as updating the general layout of the site, so I decided to touch a few things to help improve the user experience in general.

One of the things I decided needed help was the database call to get the selected style sheet for the header banner color.  

Now, the original code was done as a basically last minute addition, under the crunch to release, so we did it fast and dirty, and just made the call to the database on every request. And yes, this was an ASP.Net application, so that was every GET and every POST. 

So, instead of that, I just threw in a quick and dirty fix. And I can admit that I did not put in a whole lot of effort or brain power behind it, rather I just implemented the first thought that popped into my head. 

A rather bad habit at times. 

Anyways, my idea was to just add a global variable, and toss the value into that when the application starts up the first time, and thus I would no longer need to call the database every page request, becuase the value was just hanging out there in memory.. 

And it worked beautifully in DEVELOPMENT. 

And it worked quite well in TEST. 

And then it made it to PROD. 

At first, it worked as expected, and all was good. That change, and a few other optimizations shaved at least a second or so on every page request. 

But then it came time for a maintenance cycle and we restarted the various servers involved in the application. 

Including the IIS and SQL Servers. 

In theory, that should not have been an issue even then. After all, the maintenance cycle occurred in a time frame in which we don't typically get visitors to the site. But the system is monitored, and part of that monitoring is an automated system which visits the site on a schedule to verify that it's still up. 

And of course, this scheduled visit occurred while the SQL Server was switching nodes in the Always On Availability Group from a node's reboot.

Which meant that it couldn't read the database for the CSS file to use.  

So it used the default value. 

And that default value would not expire until the next time IIS restarted, because it was a global variable.

And that default value just happened to be the STAGE site's CSS File. 

Which meant that when I arrived to work on that Monday morning, I had the support staff and the Network Engineering staff confused and bewildered because the PRODUCTION website was serving what appeared to be the TEST website. They were tearing through firewall and switch code and the load balancer configuration trying their best to discover just how the wrong site was being served.

Well, I quickly restarted the IIS servers, allowing them to read the database for the correct value, and began trying to figure out just how I could stash that value after reading it from the DB, but not do so so permanently. 

And in my reading I stumbled across the [Web.Caching.Cache](https://docs.microsoft.com/en-us/dotnet/api/system.web.caching.cache?view=netframework-4.7.2) class on the Microsoft Docs pages. 

Which fit exactly what I needed to do. I could stash a value into the cache for either a static amount of time or a rolling time window. 

Even better, I didn't need to roll out a full fleshed out data caching solution for all the data that passes through the system. I could target it to specific values, explicitly things that I would typically just read over and over again from the SQL Server but didn't change overly often. 

So, I threw together a simple module which exposed a number of helper methods to perform the tasks I was interested in.   

{% gist 0af5527a9f22b9ae70d0ec91547d5c8b %}

For example, a user would have an icon on their user menu which shows the number of items eligible to be cancelled.  

{% gist 1e54842ae35d856b4c50ff960c2b3a72 %}

This is data that changes, but not overly fast. So, having it on a 30 second cache means that the system saves on database calls while the user navigates the various screens, but if they take the time to submit the request I can invalidate that aspect of the cache, but more than likely, they would have spent more than 30 seconds there, meaning the cache would be invalidated automatically.

And that just works. 

And I always get the proper CSS files after maintenance cycles now.