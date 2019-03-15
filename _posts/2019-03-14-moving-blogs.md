---
layout: post
title: "Moved Blog Hosts"
date: "2019-03-18 19:00:00"
permalink: "/2019/03/moved-blog-hosts.html"
author: Stephen Wrighton
description: My switch from Blogger to github pages.
image:
    thumb: 201903changeblog.jpg
    path: "/images/201903changeblog.jpg"
    sourceName: Aaron Burden
sourceLink: "https://unsplash.com/@aaronburden"
categories:
tags: [blog, writing]
---

Well, I switched out the underlying engine for this blog, moving it away from Blogger and over to Github pages. 

It's been an interesting experience to say the least

Truthfully, it's been a while coming. I was an avid user of the old Live Writer software which allowed for publishing my blogs and when it died, quite frankly so did my blogging.  

I tried a few times over the years, but I just did not like using the web interface for it.  It just didn't work like I expected. It didn't work they way I wanted it to. 

And I can admit, that there are some things that I still need to deal with in Github pages. After all, it's a static site concept. There's no database. There's no tag aggregation. There's no comments. While I'm not missing the database, as markdown files do what I need, I'm still wanting the tag pages. It's just odd to me to have a blog without them.

But, it's fast.  

<figure class='oncenter'>
<img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7" data-src="{{"/images/lighthouse-home.jpg" | relative_url }}" alt="Lighthouse Audit of my blog home page" />
<figcaption>Lighthouse Audit of my blog home page</figcaption>
</figure>

And it passes the lighthouse audits with what are effectively flying colors.  Compare those values with the ones from where I was reviewing a potential client's website for re-write. 

<figure class='oncenter'>
<img src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///yH5BAEAAAAALAAAAAABAAEAAAIBRAA7" data-src="{{"/images/lighthouse-business.jpg" | relative_url }}" alt="Lighthouse Audit of a random business website" />
<figcaption>Lighthouse Audit of a random business</figcaption>
</figure>

That said, Blogger actually did a good job on performance for blog pages. It was static html files as well, but it doesn't perform quite as well on the accessibility audit which is something I've always tried to do as well as possible. 

It wasn't the performance, or the desire to pass random audits that made me want to move. 

And to be honest, a secondary part of moving the blog was just to get a bit more comfortable with a CI/CD pipeline. It's an interesting experience, especially when I fat-finger some of the liquid syntax which the static site generate [Jekyll](https://www.jekyllrb.com) uses.

And the tag thing I can work around, or ultimately overlook. 

In fact, the only thing that I really dislike about things, is the lack of scheduled publishes. 

But even that I could technically work around by creating a branch, and submitted pull requests that I then accept whenever I want the post go live. I could technically do it on a schedule by having an automated task that accepts appropriate named pull requests. 