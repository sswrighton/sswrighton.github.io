---
layout: post
title: "Using AI in Production: Lessons from the Real World"
date: "2025-07-14 13:30:00-05:00"
updated: "2025-07-14 13:30:00-05:00"
permalink: "/2025/07/using-ai-in-production.html"
author: Stephen Wrighton
description: The first time I used GPT to scaffold code, it felt like cheating. Fast-forward a few sprints, and I found myself staring at confident code that silently dropped data in production. AI can be a force multiplier -- or a quiet liability.  In this piece, I share where LLMs shine, where they stumble, and why responsibility should always remain human.
categories:
tags: [AI, Software Engineering, LLM, Leadership, Ethical Tech]
---  

The first time I used GPT to scaffold code, it felt like cheating.

Not in the bad way, but in the *power tool* kind of way. Like I’d traded in my socket wrench for an impact driver. Suddenly, spinning up boilerplate, generating API specs, and even sketching test cases wasn’t a chore. It was a conversation.

And it worked… Until it didn’t.

The promise of generative AI in software development is seductive: ask for what you want, get it, iterate, ship. But after a few sprints of letting a LLM guide the way, you start to see it for what it is: a brilliant mimic, not a mindful architect. Beneath the surface lies something brittle.

## From Helper to Hallucination

I’ve watched developers, myself included, feed ChatGPT a vague spec and get back something that *looks* right. Interfaces that compile. Services with unit tests. Documentation with a confident tone.

But dig deeper, and the cracks appear. Implementation logic is half-baked. Test coverage is shallow. And worst of all, the code assumes its own correctness.  Even when it’s dead wrong.  Possibly, especially, when it's dead wrong. 

There’s a particular kind of AI bug that doesn’t throw an exception or crash your app. It just quietly fails to do what you meant. And that’s the most dangerous kind. You think you’re making progress, building toward a goal -- but not the *business* goal you set out to solve.

I remember a case where a developer used GPT to build out an ETL pipeline. It passed sample tests in dev, looked clean on review, and deployed without complaint. But in production, it dropped rows with null foreign keys, and did so silently. No errors. No logs. Just vanished data. GPT had hallucinated a rule, inferred logic that wasn’t there, and implemented safeguards no one asked for.

## A Tangle of Good Intentions

The second failure mode is slower. It’s architectural.

A team lets GPT “help” for a few weeks. A snippet here. A config there. Soon, the codebase balloons: abstract factories where none are needed, over-engineered services, unnecessary patterns, deeply nested logic.

You get spaghetti with Swagger annotations. Code that *works*, technically, but is human-hostile. No one can explain *why* it’s structured the way it is. Least of all the AI.

It’s like giving a toddler a loaded IDE and asking them to “make it enterprise.” The result isn’t elegant. It’s verbose, fragile, and built on misplaced confidence.

## The Human Cost of Over-Reliance

Then there’s the ethical side.

GPT will write your documentation. Your test plans. Your vendor emails, even when the issue wasn’t actually on their end. And in doing so, it nudges us toward a subtle, dangerous kind of laziness.

Not the kind that drives automation and optimization. The kind that abdicates responsibility.

I’ve seen teams copy-paste AI output directly into production workflows, only to find that it referenced non-existent fields, made legally inaccurate claims, or introduced “optimizations” that undercut security or compliance.

GPT doesn’t know your customer contracts. It doesn’t understand your regulatory boundaries. But it will confidently pretend it does.

## Hiding the Power

Of course, it’s not all doom and gloom. There’s power in LLMs. And real, practical usefulness too.

This article? GPT edited it for me. Helped restructure a few transitions. Smoothed out the grammar. Caught a tone shift I hadn’t noticed. The end result still sounds like me, because I reviewed and reworked every suggestion. But it got me there faster.

I use LLMs extensively. Not just for writing, but for development tasks that fall into well-scoped, clearly-defined buckets. The kind of things that benefit from pattern matching, memory recall, and patient repetition.
Here are a few areas where GPT shines for me:

 * **Editing for tone, clarity, and grammar.** A second set of eyes that doesn’t get tired.
 * **Generating class or DTO definitions from SQL schemas or API specs.** The sheer hours saved on writing boilerplate classes. 
 * **Troubleshooting function logic.** When I describe what should be happening vs. what is, GPT often surfaces edge cases or overlooked conditionals.

But there’s a critical distinction in how I use it: I define the task. I provide the constraints, the expectations, the purpose.

My prompts are deliberate:
 * *“Review the following for tone, grammar, and ensure it retains a 9th grade reading level.”*
 * *“This function is expected to return X, but I’m seeing Y. Review and suggest possible causes.”*
 * *“Summarize this document, and highlight potential pain points or assumptions.”*

What I’m not doing is saying “write me a solution” and walking away. The AI isn’t acting as the architect, the manager, or the QA reviewer. It’s a high-speed assistant with an encyclopedic memory and zero context for what actually matters unless I supply it.

It’s a better Google. A smarter linter. A collaborative scratchpad. And in the right hands, with the right questions, it’s a valuable partner.

But only when we stay in charge of the questions.

## Augment, Don’t Automate

Used well, GPT is a force multiplier. It can clarify thoughts, unblock syntax-level hurdles, and jumpstart creative work. But it cannot, must not, be the final authority.  The tool may generate, but intent must come from us.

You wouldn’t let Clippy write your audit report. Don’t let GPT write your security model.

This all reminds me of an old IBM training slide I saw early in my career:
 > “A computer can never be held accountable. Therefore, a computer must never make a management decision.”

We’d do well to remember that.

AI can assist. It can advise. But only humans can be accountable.

Because when things go wrong, you don’t blame the wrench. You blame the hand that used it
