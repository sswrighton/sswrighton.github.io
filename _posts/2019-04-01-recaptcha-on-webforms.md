---
layout: post
title: "Recaptcha on WebForms"
date: "2019-04-01 19:00:00"
updated: "2019-04-01 20:05:00"
permalink: "/2019/04/recaptcha-on-webforms.html"
author: Stephen Wrighton
description: Implementing RECAPTCHA on a WebForms login screen
categories:
image:
   thumb: 201904letters.jpg
   path: "/images/201904letters.jpg"
   sourcename:  Amador Loureiro
   sourcelink:  https://unsplash.com/@amadorloureiroblanco
tags: [ASP.Net, WebForms, Google, reCaptcha]
---

We have a project that for years used a library named MSCaptcha  to generate a simple, 4 digit captcha on login, and other tasks where we need to verify that the person entering the data in the form is not a robot. Well, we are doing some work on that application, adding new features, and overhauling the layout, and the change control board has handed down the edict that they wished for Google's reCaptcha to be used in the place of our current captcha element. 

So, doing what every good programmer does for the change control board, I bowed low and exclaimed. "It shall be done!"

Or, I responded to the email, with an "Okay." 

Anyways, the MSCaptcha library worked well for our needs. Of course, we downloaded this thing in 2013, and never found an update to it. So, the code, since it was written in .NET still works, was old. And old usually means insecure.  Was it insecure? I don't really know.

MSCaptcha was originally created by Mondor Software, but is currently maintained by [Dmitry Kirsanov](http://kirsanov.net), but it doesn't appear that any movement has been made on it in since before I downloaded it. 

There is a NuGet package, but it's labelled "unofficial" and doesn't seem to have any real relationship with either the current maintainer nor the original creator company. 

Which means that I really did not have any reasons to not follow the change control board's edict. 

Thus, I went off to the Google site, hunting for the reCaptcha tool.  And ending up creating a new account for the client, so that I could register the web application 

Now, using reCaptcha means that you have to register the website with Google, who will then provide you a public and a private key.  

Which is very easy, and basically consist of these steps:

1. Login into the [reCaptcha Admin](http://www.google.com/recaptcha/admin) portal using your Google account
2. Select reCAPTCHA v2
3. Enter the website domain
4. Find the API keys on the API key page

The public key needs to be included in the html sent to the client, while the private key is used by the server to verify the reCaptcha response. 

Which means, basically, having this on the ASPX side of the page. 

{% gist be18f6c116f79df92876dccfb919372d %}

Of course, I would put the SCRIPT tag at the bottom of the page. Of course, with the ASYNC DEFER attributes on the script tag, that's not really that important, but it's the principle of the thing. 

But of course, without the Public/Private keys, that's not exactly useful for anything.  In the DIV above, you can see that I'm writing out a PublicKey property into the data-sitekey attribute.  

Which means, that I need to populate that property whenever the page is loaded.  Which can be seen here: 
 
{% gist b1487ed60924240cd05fce5fe883a406 %}

I do want to note that this is a perfect use for the [DataCache](/2019/03/aspnet-datacache.html) aspect of WebForms.  In my Page_Load method, I'm making a call to a 'GetAttributes' function.  Now, GetAttributes, is not technically an aspect of PAGE, but I do love my [Extension Methods](https://docs.microsoft.com/en-us/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods).

Anyways, GetAttributes queries the database for the PrivateKey. But since that's a value that effectively never changes, I can cache it for hours on end.  And that's what's happening inside that function. GetAttribute named value pairs exist in a rolling cache for 12 hours.  If at any time the value is not there, it's a simple database call away. 

The second aspect, is asking Google if the user has passed the reCaptcha test.  

Basically, this is done by asking Google. 

The way I did that, was by wrapping the required calls into a function that returns a Boolean.  Additionally, I've wrapped the expected response package into a private class. 

{% gist 7449581029433159437b4f0c20e77d74 %} 

Now, I call that method prior to validating the user's login credentials or any other task that I want a reCaptcha verification on (read: contact form!). 