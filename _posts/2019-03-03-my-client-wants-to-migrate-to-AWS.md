---
layout: post
title:  "My Client Wants to Migrate to AWS"
date: "2019-03-03 13:22:00"
updated: "2019-03-03 15:30:00"
permalink: "/2019/03/my-client-wants-to-migrate-to-aws.html"
description: "Wonderings About
categories: [blog, AWS]
tags: [hosting, AWS, Cloud]
author: 
    name: "Stephen Wrighton"
    url: "https://github.com/sswrighton"
    image: "https://www.gravatar.com/avatar/53a4066fb888b4a54fa1e650945e34a8?s=64&d=identicon&r=PG"
---

I'm not going to lie, I'm not fond of AWS or other cloud providers as a general rule. In truth, there's an aspect of trust which I lack in these large providers. Sure, they have their place, and can perform certain tasks better than a hosted solution; especially when it comes to elements such as machine learning. And I believe that what it should be doing is extending the application from your infrastructure out to the cloud services.  But at heart, I believe solutions should have dedicated hardware and purpose built environments; and this is how we typically quote our solutions.

And we now have a client who wishes to transition from a privately hosted solution to the cloud. 

Actually, the 'cloud' is a misnomer in this scenario.  They're wanting to implement against AWS as an IaaS (Infrastructure as a Service) provider.  There is no cloud in this situation, as the cloud is a conglomerate of hardware and software that's not hosted here, where "here" is wherever the someone happens to be.  The software in question here exists. My boss and I built it. The concern is where is the software going to live.  Thus, IaaS, which is a subset of NIST's definition of Cloud Computing. 

AWS is the biggest IaaS provider on the block. They got in first, and early. To the point that IBM is still trying to catch up, while Microsoft has done a pretty good job of doing so actually. 

And probably at the worst of all of this, is that desire to go to AWS is not being prefaced by a detailed study of the best provision. Rather, it's a desire to go to AWS. 

But I digress, the backstory here is that we built a system for the client. At the highest level, the system is a website. That's what people see. That's what people interact with. That's what all the infrastructure and other bits and bobs are there to support. Without the website, none of the other things would exist or even matter.

Now, the infrastructure is that there's a DMZ hosting three load-balanced servers for IIS and an FTP Server alongside a firewall, and IPS appliance, followed with the protected area.  Inside the protected area is the SQL Server, Exchange Server, Domain Controller, an application server and a UAT Server. All of this is hosted on a mixture of physical and virtual devices and designed for fail-over from a primary site to a geographically dispersed secondary site. 

As for the software, like I said there's a website.  

That's the big thing.  

Of course to support this website there are the two SQL Server instances, chained together in an AlwaysOn Availability Group.   Can't have a website without data.  

But then there are all the other little services and widgets which support this website. There's a service which communicates with an external data feed to gather the data that we consume, process and present to users. There's the service that deals with slow payment types (i.e. ACH) and securely moving those files from our infrastructure to the relevant bank. There's the service which generates reports for users, and pushes them to the FTP Server for later consumption.  There's the Exchange server for sending and receiving emails.  Then there's the "support" intranet, inaccessible from outside the network's firewall, but containing the tools needed to manage the system, configure user and system data, and in general allow the help desk to do their job. 

But hey, it's just a website. 

We've been hosting this thing in a private cloud for the client for nearly five years now, and have managed thousands of transactions, and ushered millions of dollars in and out of the system, and all of that with at least a 99.9% up-time. 

So, it's been nearly five years, and it's getting close to contract renewal time, and the client starts talking about AWS.  And how they want to "save money" by switching to AWS.  

First off, the software wasn't built for AWS or any IaaS provider.  And while it can just be tossed onto a virtual server running on EC2, that's not saving the client money. That's not building a system that works with its infrastructure or any actual IaaS provider infrastructure. And sure, while the upfront costs my be lower with AWS in that scenario, you're still going to pay about the same, if not more, over the life of the five year contract. And as an Enterprise solution, there's going to have to be a multi-year contract. 

Actually, that's probably not true. We amortize the costs of the hardware over the life of the contract, so even that is spread out for them. So, for my company there's a potential cost saving up front, but the client would still feel that particular pinch, as the client isn't buying the hardware, rather renting use of it from us. 

There's a certain level of cost associated with the quality and performance profiles of the hardware we build for our solutions.  That cost has to be paid somehow.  And it will.  The only difference is if that cost has a large balloon up front, a large balloon at the end or if its amortized over the life of the contract.  You've still got to pay it, and you still have to pay for the operations. For the IPS. For the bandwidth. For the backups. For the monitoring.  These things don't go away. They exist and continue to exist whether you have a private infrastructure or use IaaS.  Sure, when we as a systems solution provider have to pay these elements changes, but since we already amortize these costs out for the client, they're not really impacted in any meaningful cost-savings way.

The thing is that AWS' biggest success is not its IaaS tools or services. It's not the fact that it's the biggest IaaS provider in the land. AWS' biggest success is the fact that it has marketed itself as a low-cost, ultra-reliable and easy-to-use provider of infrastructure. 

Because whether or not it's true, my clients believe it. 

***Ease of Use ***

The best example for ease of use is I took an icon quiz regarding the AWS dashboard (https://docs.google.com/forms/d/e/1FAIpQLSdnEEo0o2JgnIt8VOGffhkcYj-C2h9m5_NFzM0Q1AU-P8d0zA/viewform). I got a 2.  Now, I know that I'm not the smartest person around and I don't typically interact with cloud provider solutions, but I have been doing this for 15 years professionally. I've been programming off and on since the fourth grade; which is more years than I really want to consider right now. And I got a 2.  All I have to say is that you best hope that dashboard comes with tool-tips, as there is an order of magnitude difference in the costs between some of the services hiding behind these icons; ones that look eerily the same. 

The other thing is try to use their price calculator. You have to spend hours researching to determine the specific infrastructure/services you need to host your solution. I think I did it right to emulate an existing infrastructure for an application (website + 65 databases for each geographically zoned user base), but that ended up with an estimated $125,000/month bill.  And yes, that's a comma with three zeroes after it.  I'm still not certain if I did it right (or if there was a better way) or not. Let me rephrase: what I configured in the estimator would work, but I don't know if there could be a better configuration. That's not exactly an ease-of-use concept there. And all of that is just estimating and working with the tools; not actually doing anything. 

***Ultra-Reliable ***

This gets me.  AWS has a lot of claims about reliability. You see a lot of discussion about 11 9's and 4 9's.  My favorite is that 11 9's one. Their claim is that they had a storage durability of 99.999999999%. 

>“If you store 10,000 objects with us, on average we may lose one of them every 10 million years or so. This storage is designed in such a way that we can sustain the concurrent loss of data in two separate storage facilities.”
>http://aws.typepad.com/aws/2010/05/new-amazon-s3-reduced-redundancy-storage-rrs.html –Jef;

Which is a massive claim, and in the 6 years since that claim was made, it's been reiterated but never validated. They do not tell you how they got those numbers, nor the assumptions.  That said, performing the math on the thought that two cheap (consumer grade) disk drives, in two distinct locations, will both fail simultaneously, and that both of those failures are catastrophic to the point of 0 byte data recovery, then yeah, you get eleven 9's.  of course it's just as easy to say that it's good unless the world dies in an fiery cataclysm as a comparison. I get my 11 9's that way to.  Of course, you also need to go look at what "durability" means in that particular claim. It's hard to find the definition but it's there. Basically, they say that the file will be stored somewhere in Amazon's infrastructure.  That said, there is no claim to the user being able to access and retrieve that data. 

But that's storage. Their claims about availability is for four 9's (99.99%).  At least that's the marketers. Legal says that AWS users can't complain (and won't receive financial breaks) until reliability drops beneath two 9's.  I mean those 2 extra 9s are the difference between 9 seconds of downtime per day and 15 minutes of downtime per day.  But even their availability isn't perfect (https://www.readitquik.com/articles/cloud-3/top-7-aws-outages-that-wreaked-havoc/). They have outages, and because they are the biggest IaaS provider on the block, their outages effect many more businesses and consumers. 

***Low cost ***

Of course we need to consider the cost of things here.  And frankly, I despise phrases like low-cost.  They are so imprecise, and ultimately meaningless without any surrounding context. For example, if I'm stuck on a train track, and there's a train coming. I would consider losing a foot a low-cost for evading the train.  By the same token, if I step on a nail, get an infection and lose that foot, that's not a low-cost to stepping on a nail.  Context is important. 

And AWS is right. They are a low-cost bandwidth provider. Take a simple, non-dynamic website, and compare the month 1 cost of hosting it privately versus the month 1 cost of hosting it on AWS, and AWS is going to win. Let's be honest, I host my blogs in the cloud.  I don't have an infrastructure for them, I don't want to have one. I'm okay with losing a day here or there for the cloud provider to do necessary maintenance, or even a random natural occurrence like Azure's recent lightning strike (https://redmondmag.com/articles/2018/09/04/azure-office-365-down-in-texas.aspx). if I lose a post, that's okay. I have it saved somewhere and can repost it. But there's a caveat there, an important consideration that has to be considered: I'm not running a blog to make money. I mean, a decade or so ago, I ran two blogs steadily for five years before life managed to get in the way, and did so with rather consistently large viewers, and managed to gather $60 in ad revenue in that time frame. Like I said, I'm not here for the money.  

My clients are though. Kind of. It's complicated.  Anyways, their system deals with money, lawyers and government officials. This is not the place where you can accept downtime and the concept of "aren't really overtly concerned with always being there" is a non-starter.  It's not a place where data loss is acceptable. In fact it would be better to describe it as catastrophic. To everyone involved.  We are dealing with lawyers and government officials after all. 

The thing is that that context on costs are always important. Short term, yes. AWS would always be the way to go. If you're taking your site down after a few weeks or months. Then definitely. AWS or some other cloud provider.  It's the long term that gets you. You provision a server, and it runs. AWS will keep that server running even as they shift hardware about underneath you. And they will keep that cost growing, and at some point having a private cloud will make more financial sense, and its even possible that building your own data centers (i.e. the physical building hosting their servers) will ultimately make more financial sense.  It did for Moz (https://www.geekwire.com/2014/heres-startup-dumped-amazon-web-services/).

The other thing to consider is that this low cost, has costs. Storage costs on the GB level (1000\*1000\*1000) while data transfer costs on the GiB level (1024\*1024\*1024). There's costs associated with licensing and backups. There's costs associated with storage both of primary data files for the database, as well as the backup files of the database. Which is different than the costs of storage for the data files for the website or the cost of storage of the billions of log files generated by the AWS system, services and compute devices.  There's costs with IOPS, and compute cycles.  There's costs for the data sitting idle.  And AWS is making Amazon money hand-over-fist.  The last number I saw was a 101% profit.  That means for every dollar they spent in infrastructure, labor, and marketing, they charged $2.01 for it.

And let's not even start about the cost of support, which for businesses starts at 10% of your monthly bill or $100 whichever is greater. Or the Enterprise level support starts at 10% of your monthly bill or $15,000 whichever is greater. 

***The Bottom Line ***

AWS is not the evil bogeyman.  It does a good job at what it does.  But if you have a system that's working, doing its job and doing it successfully. If your system is not even being phased by the thousands of attacks committed against it monthly. If your system is up consistently and when expected. If you are getting quick, efficient support at a phone call as part of your hosting package. Then maybe, just maybe, you shouldn't consider switching. 

That fact is doubled, when you're switching to a specific provider just because that provider is the biggest name out there, not because it's the best or most reasonable solution provider. 

