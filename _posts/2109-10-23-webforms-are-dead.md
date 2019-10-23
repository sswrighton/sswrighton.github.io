---
layout: post
title: "Webforms Are Dead"
date: "2019-10-23 10:00:00"
permalink: "/2019/10/webforms-are-dead.html"
author: Stephen Wrighton
description: Thoughts and considerations regarding ASP.Net WebForms.
image:
    thumb: 201910hourglass.jpg
    path: "/images/201910hourglass.jpg"
    sourcename: Aron Visuals
    sourcelink: https://unsplash.com/@aronvisuals
categories:
tags: [.Net Framework, ASP.Net, WebForms, .Net Core]
---

Microsoft has effectively killed ASP.Net WebForms. 

In truth, this makes me sad, I loved WebForms. They worked in a way that made sense to me, especially as I was effectively a thick client programmer who was just getting started in this wild world of web application development back in 2003. Though, I can understand; most developers want MVC, Razor Pages or  WEB API and a JS Framework for their new efforts. Microsoft has to adapt; they have to give developers what they want. 

Worse for me, Microsoft is removing VB.Net from being able to be used to create new ASP.Net applications once .NET Core becomes .Net 5.0. Again, VB.Net just worked for me. I preferred its syntax and coding style over C#'s. And again, I can understand. The most vocal developers out there, bad mouth VB.Net constantly. I remember at the start of this year, when VB.Net suddenly appeared on the programming lists, that the .NET podcasters went crazy; and not in a good way.  Again, this is just Microsoft producing what they believe developers want; though in this case there is also some coupling with their cross-platform initiative associated with .Net Core. 

But as always, we advance, and we adapt. I'm in I.T. and have to do so; and as the person in charge of my companies development efforts, direct the company and guide my employees in doing so.

But this also means, that all those WebForms applications (both the VB.Net ones and the C# ones) out there, are quickly running to their end of life. They need to be uplifted and changed from WebForms to a new technology such as Razor pages.

Above and beyond that, there are a lot of "gotchas" in WebForms. Things that a developer can do with them, to make them more efficient, and basically work around all the headaches which most developers complain about regarding them.  The problem with this, is that if you're not familiar with those work arounds or tricks, then a developer won't understand what's actually happening.  Which means that the resulting new code, could produce things you're not expecting (i.e. bugs!). 

This is doubly the case if your WebForms application happens to be in VB.Net. After all, VB.Net is an underserved market, with most new developers not learning the language. And again, not knowing the depths of the language means that efficiency tricks could be missed or misinterpreted when moving the code to C#. 

I'm not sure if this is ultimately a good thing or bad thing from an overarching point of view. But in the end, we have to learn and adapt.  

And change our code to suit.