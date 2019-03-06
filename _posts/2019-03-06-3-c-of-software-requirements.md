---
layout: post
title:  "3 C's of Software Requirements"
date: "2019-03-06 15:40:00"
updated: "2019-03-03 15:46:00"
permalink: "/2019/03/3-c-of-software-requirements.html"
author: Stephen Wrighton
description: 
categories: 
tags: [Programming, Software Requirements]
author: 
    name: "Stephen Wrighton"
    url: "https://github.com/sswrighton"
    image: "https://www.gravatar.com/avatar/53a4066fb888b4a54fa1e650945e34a8?s=64&d=identicon&r=PG"
---

I have a tendency to want everyone around me to be able to write effective requirements documentation. I don't necessarily know why I'm like this, but I use those skills constantly in an effort to more or less train people in how they think, write and talk. 

Recently though, I've taken to proactively training our support staff person in how to write requirements.  

He interacts directly with the end users for one of our products, and as such often takes in the initial requests in relation to bugs, issues, and changes.  

Having him know how these items should be documented, as well as how to ask questions of the end-users, can only help with how those items are built, can only be a good thing in my opinion. 

Additionally, since he's intimately aware of both the production system, as well as the support systems, he has a good idea of how things need to change conceptually, even though he lacks in the programmatic knowledge in which those changes would be carried out.

And I sometimes wonder if that wouldn't help those who write software requirements, but I digress. 

Recently though, he had an idea on an improvement for the support system he uses, in which he would desire to make it easier to move work items from one user to a different user.  

So, while bleeding on his documents using the track changes functionality from MS Word, I told him about the three C's of Software Requirements.  In my opinion, these are the most important concepts to remember while defining requirements no matter the detail levels (Originating versus system versus detailed design) or even problem domain.  

	1. Clear
	2. Concise 
	3. Consistent 

Clear writing is the number one need for  requirements documents.  

This is because any ambiguity in the specification leads to confusion, and unexpected results in the generated software. Clear writing is the ability to choose the words used to ensure that they are the least ambiguous phrasing possible. 

Let's consider the phrase: 
> The system will allow a user to log into the system. 

On first glance that's a clear statement. It's short, simple; the user does an action.  And in something like a user story, it could be changed to something like "the user logs into the system" and then would be a perfectly acceptable description of what the user did. 

Unfortunately, when discussing software requirements, there is so little clarity in that sentence as to be useless. 

First, it tells us nothing about how the authentication is processed. Is it AD? Is it a JWT? Or a forms/cookie authentication scheme? Or is it a certificate? 

We don't know because the requirement is unclear as to the specifics. 

So for that first issue, we need to have the phrase: 
> The system shall authenticate the user using forms-based authentication. 

This explicitly tells us that we're expecting to authenticate the user using a specific technology and process. 

But, it also fails to convey the entire concept which the original statement held.  And lack of information is just as lacking in clarity as ambiguous statements.  

So, we need to add a few additional lines
> - The user shall be able to enter their credentials into the login form
> - The login form shall allow for the entry of the username and password 
> - The system shall compare the provided credentials with the credentials data store for a validation match
> - The system shall send a good/bad response to the client when the user submits their credentials based on the user credential validation match
> - If the system response is good, the user shall be authenticated for a rolling 10-minute period
> - If the system login response is bad, the system shall display an error message, and the user shall not be authenticated 

These additional statements give details of the action of logging in.  It tells us we're going to have a login form, into which the user will be able to supply a username and password. 

Additionally, after submitting that data, it gives a clear view of what is going to happen next.  We know we need to validate the provided credentials, and then either work with the user as authenticated or tell the user that they had an issue with their credentials. 

But then, it's also more than just providing specific details.  

To be clear in your writing, you also need to have a good understanding of who your intended audience is, so that the words you use are words the reader will understand. 

Which also ties in nicely with the fact that, any domain specific words as well as any abbreviations that are used, need to be included in a definition and acronyms section.  Every specification document I write, I have this section within it, and believe that it is one of the most important sections in any document. You cannot be clear, unless everyone is on the exact same page in regards to the meanings on specific words. 

I have a current project, and the stakeholders for this project, have a word that they can use in a sentence 4 times, and each time the word has a different meaning based upon the context of where it resides in the sentence and in relation to the other uses of the word. 

The same word. 

As can be expected this made discussions on requirements for the software being built be... interesting.  The first thing I did, was created a definition section, and started using specific words to describe specific concepts, and got buy-in from the stakeholders for that.   

Sure, I had to be more verbose, and because I stripped context from the word, I had to use three or four additional words, but I was clear in my meaning, and could be so without the context, and repeatedly. 

Which is why the definitions section is so important. 

FInally, here are a few tips that help with creating clear documents:
- Limit commas. 
- Prefer short, sentences where each sentence has a single purpose
- Lists are better than paragraphs 
- Simplify statements
- Remain consistent in styling 


Next time, I'll discuss the need for conciseness in requirements writing.