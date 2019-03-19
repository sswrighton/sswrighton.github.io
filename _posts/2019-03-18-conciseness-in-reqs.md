---
layout: post
title: "3 C's: Conciseness in Requirements"
date: "2019-03-18 19:00:00"
update: "2019-03-18 20:14:00"
permalink: "/2019/03/conciseness-in-requirements.html"
author: Stephen Wrighton
description: Part two of 3 important concepts of software requirements.
image:
    thumb: 201903threec.jpg
    path: "/images/201903threec.jpg"
    sourcename: bonneval sebastien
    sourcelink: https://unsplash.com/@gentlestache
categories:
tags: [software requirements, writing]
---

A bit ago, I started an article on the "3 C's of Software Requirements."  With the first part being a discussion on [clarity](/2019/03/3-c-of-software-requirements.html) in requirements.

And those Cs were:

1. Clear
2. Concise
3. Consistent 

This time, I'm discussing conciseness.

While clarity tends to be verbose, and adding words to ensure that any given phrase can only have one meaning, conciseness attempts to bring that back under control and basically use as few words as possible. 

And attempts to ensure that those words are "smaller" words. 

[Dictionary.com](www.Dictionary.com) defines concise as 

> giving a lot of information clearly and in a few words; brief but comprehensive

That's a goal for all writing, but in specific for technical writing. 

This is something near and dear to me, because I read a lot. 

In fact, I'm averaging roughly 2 million words per month, just for leisure reading. That's not counting the emails, specifications, contracts, books and journals that I read as part of my job and further learning efforts.

But reading that much means that I can either re-read books multiple times, or I can read fan-fiction in addition to published books. Which does a world of good for my book budget, even if I'm sometimes cringing at how the English language can be tortured. 

And I brought that up, because a lot of fan-fiction writers will use odd or old words because they sound "cool" in the context of the story. My biggest pet-peeve is the use of the word tome.  Sure it's defined as a 'big, heavy, scholarly book' but no one really uses it. 

I mean, I'm not wondering around my office, and asking "Hey, has anyone seen my tome on software requirements?"

And that particular book meets the definition requirements. It's scholarly. Big. And I use it as a door stop so it's heavy. 

The point is, is that it's not concise. It's using a 'big' word, when a "smaller" one would do just as well, and not be jarring to the reading experience.  

>Plain, simple language, short words and brief sentences. That is the way to write English--it is the modern way and the best way. Stick to it; don't let fluff and flowers and verbosity creep in."
> - Mark Twain

Being concise means using the minimum value of words to convey a concept.  And this applies to writing technical documents, emails or even giving presentations.  Conciseness minimizes confusion, and ends up with a smaller document, which saves time.  

Which is something that goes against the training of English Comp I and II in college with its minimum word counts. You were encouraged to write longer papers, even if those papers were mostly fluff. 

But technical writing shouldn't suffer from fluff (neither should non-technical writing, but that's a discussion for another day). 

And there's a number of things that can be done to achieve conciseness. 

The first way we're going to look at is to avoid using unnecessary 'wordy' phrases. Word phrases are phrases which can often be replaced by a single word without changing the meaning of the sentence.

Compare this sentence: 

>Take into consideration the price when you compare Azure and AWS.

With this one: 

>Consider the price when comparing Azure and AWS. 

Both sentences say the same thing. They convey the same concept. But one is wordier than the other. And while that wordiness does not make the original sentence unclear, removing it keeps the clarity that is the number one goal for technical writing. 

The following table displays a list of common wordy phrases, and what they can be replaced with. 

| Wordy Phrase | Replacement |
| --- | --- |
| a number of | some |
| a majority of | most |
| based on the fact that | because |
| due to the fact that | because |
| give consideration to | consider |
| hold a meeting | meet  |
| has the ability to | can |
| in a clear way | clearly |
| last but not least | finally |
| per annum | annually |
| regardless of the fact that | although |
| take into consideration | consider |
| until such time | until  |
| whether or not | whether  |

Most of these wordy phrases are little things which pepper our speech, and used in Comp II to artificially inflate our papers. Or they are things which we've seen a writer that we respect use in a situation, and so we add it to our documents in places that are similar to where we originally seen it. 

Basically, the concepts that you're attempting to do away with in Wordy Phrases are: cliches, qualifiers, redundant phrases and stock phrases. 

And don't forget that there is a definition section for a reason. Use it. Don't keep defining words in your sentences. 

Consider this sentence: 

>The orders will be aggregated daily at 0200, by a list of commands that are processed in sequence without the requirement of user input.

Now, if we generate this definition:

>**Batch Job** A list of commands processed in sequence without requiring user input or intervention. Usually on a schedule.

Then we can change that above sentence into this aone: 

>A batch job will aggregate the orders daily at 0200.

We don't have to explain what a batch job is in that sentence, because we put that definition into the Definitions section. It's already defined, so both reader and author will know exactly what is meant. The sentence keeps the important bits (what the batch job is doing, and when) and shuffles off the extraneous fluff into the definitions section.  

This becomes even more important if you're using the term that was defined multiple times.  

Another consideration to enhance conciseness is to avoid a passive voice when writing.  

Which is something that I struggle with, because it was not something that I was told needed to be avoided when I was in school. In fact, I had to rewrite my second sentence about batch jobs three times before I had it out of passive voice.  

And I feel the need to define Passive Voice here, since I had no clue what MS Word was talking about the first time that it pinged me on it during a grammar check:

>A verb is in the passive voice when the subject of the sentence is acted on by the verb. For example, "the ball was thrown by the pitcher,"  the ball (the subject) receives the action of the verb, and was thrown is in the passive voice.

So, with that definition in mind, we consider the sentence: 

>The login form is submitted by the user.

"Login form" is the subject, and it is being passively acted upon by the user. The form itself (which is the subject of the sentence) is not actually doing something. Changing it to active voice, generates this sentence:

>The user submits the login form. 

Here there is direct action. The user does something.  

And while the meaning stays the same, it uses two less words.  Which does not sound like a lot. It's just two words. 

But when you're a document that has roughly 5,000 sentences and the author is able to remove two words for 80% of those sentences that removes 8,000 words.

And that's the point of conciseness. 

We're trying to describe an idea, a product, and we need to do it as cleanly as possible. Clarity is a big part of that, but so is not using five words, when two will do. 
