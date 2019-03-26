---
layout: post
title: "Consistency in Requirements"
date: "2019-03-25 19:00:00"
permalink: "/2019/03/consistency-in-requirements.html"
author: Stephen Wrighton
description: Part 3 of 3 important concepts of software requirements.
image:
    thumb: 201903consistent.jpg
    path: "/images/201903consistent.jpg"
   sourcename: Alvaro Reyes
   sourcelink: https://unsplash.com/@alvaroreyes
categories:
tags: [software requirements, writing]
---

A bit ago, I started an article on the "3 C's of Software Requirements."  With the first part being a discussion on [clarity](/2019/03/3-c-of-software-requirements.html) in requirements, and the second part a discussion on [Conciseness in Requirements](/2019/03/conciseness-in-requirements.html).

And those Cs were:

1. Clear
2. Concise
3. Consistent 

Remember, the purpose of technical writing, and this is not just software requirements, but any technical or educational writing, is to convey how to do something, and to do so in ways that minimize confusion and enhance understanding. 

We've already discussed the need for clarity and conciseness, now the third of these elements is consistency.

There are a number of definitions for consistency, but the one that I'm actually interested in is thus:

> agreement or harmony of parts or features to one another or a whole

The reason that this is a big deal, is because requirements need to be consistent when written. 

Humans love patterns. We look for them, and find them, everywhere. 

And patterns help us consume, and internalize data easier. They form frameworks upon which we can hang expectations and theories. They help us to plan, estimate and even help us to minimize risk. 

That means it should be a goal in writing requirements to generate those patterns. Or basically, do anything that helps with the consumption of the document. 

A technical writer must remember that technical documents are not fiction. They are not creative writings, designed to entertain. 

A technical writer is not supposed to be finding the most unique way of saying something. 

In fact, in technical writing, repetition is good.  

Repeating elements in your writing helps with understanding, and with consistency. 

And the first of these helpers for consistency we're going to discuss is styles. 

Software such as MS Word offers us hundreds of fonts out of the box, and millions more are just a web search away.  Modern word processors allow us to customize any variable of the writing process, from the height of the characters, spacing of paragraphs, and even to the colors of individual characters. 

And for a technical document, most of those fonts and colors should never be used.

You don't want to use different fonts. 

You don't want to randomly change font sizes. 

You don't want to have words in a hundred different shades of color.  

What you're aim for is a document that mostly looks the same.  Word after word. Paragraphs easily distinguishable. Every level two header looks like every other level two header.

You want your paragraphs to look the same.  

You want the titles to look the same.  

Because in the (very) few times you don't use the same styles for something, that instantly makes that content jump out at the user.

Probably the best thing which the person who trained me in writing requirements documents did was forced me to get to know the styles system in Word. 

And then forced me to use them. 

This is because styles can enforce the necessary sameness. They ensure that your paragraphs always look the same. They even ensure that when you're calling out something specific, that the highlighted information looks the same as every other time you call out specific facts.

They help with the building of table of contents, and tables of figures and a host of other useful things that just make creating documents easier and of course, more consistent. 

And they save time. 

Imaging trying to produce and maintain a table of contents in a reasonable sized document. Such a thing would take hours. For every change made.  While with properly used styles, it takes a key press to update and maintain.

Another thing which I do, which makes all of this infinitely easier is to have a base document template. 

My base document is set up so that I have the styles that I will actually use in it already defined, and waiting.  I've given it the headers and footers that I like to always have. 

I also put in common boiler plate that I use in almost every document.  

For example, the company I work for is named Software Consulting Services, LLC., but it is commonly referred to as SCS in our documents. So my base document template has the 'Definitions and Abbreviations' section already created with SCS already entered as an abbreviation.

And then I have a style that formats my definitions and acronyms in specific ways using tabs and a hanging indent.

The important part though is that I have this template built, and defined, and things that I always use already setup and waiting as a base.

Think about what that means for the documents that are created using this base.

My section headers always look the same. My paragraphs are always styled the same. My tables and images are always captioned in the same color, and fashion (for the record, tables are captioned above, images captioned below, and the caption contains; [Table/Figure] [Counter] [Description]). 

What this means is that my documents are not only internally consistent, but also consistent across work items. And in general consistent over time.

It means that I always know what the documents are going to look and feel like. 

Just like my boss will.

And just like my co-workers will. 

And just like my long-term clients will. 

Now don't think that this means I expect how documents are formatted never changes. 

That's not the point. Or the purpose.  As in everything, you should constantly ask "how can I improve this?" after you finish a project. 

I've had my base document for a decade now. 

And it has changed over that time. I switch from Times New Roman to Calibre as the base font. I shifted my section headers from black font to a blue. 

And about three years ago,  I added an entirely new section which breaks down my estimates in a way that I believe is clearer to everyone involved.

But those changes don't happen in mid-document.  

Change, growth, over time is good; while consistency in a single work item is necessary. 

And for how important a consistent look and feel for the document is, consistency in the content is probably more so. 

This cannot be reiterated enough; in technical writing use the same words. And the same sentence structure.  

My functional requirements looks like a very homogeneous document.  The structure is a series of simple sentences, that each explain a single thing.  And they all look the same. 

X shall Y. 

For example: 

> The change password form shall contain a username entry field 
> The change password form shall contain a current password entry field 
> The change password form shall contain a new password entry field 
> The change password form shall contain a confirm password entry field 
> The change password form shall contain a submission command
> The change password form shall verify that the values entered in the new password entry field equals the confirm password entry field 

You can see the pattern as it repeats itself.  X shall Y.  

It's a consistent repetition. We know that X shall Y. 

And I continue that pattern. Keeping the same name for a particular concept. Using shall over and over again. 

Being repetitive in a way that would horrify a creative writing instructor. 

I do it because it works. It creates that pattern, that consistency, which helps with the consumption of what I'm trying to say. 

Finally, it's not just sentence structure that we need to focus on. 

Anything inconsistent can take away clarity and as such slow down the consumption of the content. 

Serial comma use. Capitalization. Digits or words for numbers. 

The proper, and consistent uses for these do wonders for understanding and consuming the content.  While inconsistently changing something breaks the reader's concentration, making them think harder to come to a full understanding.  

For example:

> Success messages shall be displayed in the Active Messages section of the template 
> Success messages shall have a green background 
> Success messages shall have a hunter green font color
> Warning messages shall be displayed in the Active Messages section of the template 
> Warning messages shall have a yellow background 
> Warning messages shall have a goldenrod font color
> Error messages shall be displayed in the Active Messages section of the template 
> Error messages shall have a #FFCCCC background 
> Error messages shall have a dark red font color

The hex based color definition stands out. It's inconsistent. It's different to the point that a reader can be unsure what is being said. Leaving them questioning if their understanding for the other colors is correct, and if so, why is that one color important enough to call out so explicitly.

It hampers the consumption of the content.

And all of this is about consuming the content. 

Because if no one consumes it, if no one understands the content, what's the purpose of writing it?
