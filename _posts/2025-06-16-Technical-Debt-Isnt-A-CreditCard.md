---
layout: post
title: "Technical Debt Isn’t a Credit Card. It’s a Mortgage."
date: "2025-06-16 13:30:00-05:00"
updated: "2025-06-16 13:30:00-05:00"
permalink: "/2025/06/technical-debt-isnt-a-credit-card.html"
author: Stephen Wrighton
description: We talk about technical debt like it’s a credit card. But in reality? It’s a mortgage. Long-term, compounding, and quietly shaping every decision that follows. I wrote about reframing the metaphor, and how to have better conversations with leadership around the true cost of shortcuts
categories:
tags: [Technical Debt, Engineering Leadership, Modernization, Software Architecture, CTO]
---  


**Technical Debt Isn’t a Credit Card. It’s a Mortgage.**

In every engineering all-hands or architecture review, someone eventually invokes the metaphor of technical debt. And when they do, it often sounds like this: "We put it on the credit card. We'll pay it off later."

It’s a seductive analogy. A credit card implies agility, optionality. You can move fast now, and as long as you make the minimum payments, you stay in the game. Eventually, you clean it up. It’s just a matter of prioritization.

But in my experience -- from legacy .NET WinForms apps duct-taped to a modern CI/CD pipeline, to JavaScript monoliths screaming under the weight of abandoned dependencies -- technical debt rarely behaves like a quick fix. It doesn’t wait politely. It accrues interest, yes, but not the kind that shows up as a neat percentage in your backlog. It compounds in silence, woven into every new feature, every rushed bug fix, every exit interview where the dev says, "It was just too frustrating to work in that code."

So maybe it's time to retire the credit card metaphor. 

Technical debt is more like a mortgage.

### Mortgages Are Binding

Mortgages shape your future. They anchor you to a decision made years ago. Like that ORM someone chose because it was "easy to get started." Or the single, massive SQL stored procedure that handles billing, account creation, and password resets because "it was all in one place already."

A mortgage comes with terms. So does technical debt. And those terms get renegotiated, not by a bank, but by turnover, shifting product priorities, and evolving customer expectations. Suddenly, your decision to skip modularization in the interest of speed isn’t just a missed best practice, it’s a blocker to the next product launch.


### You Don’t Pay Off a Mortgage With Spare Change

Credit card debt has the illusion of flexibility. You can throw $20 at it this sprint. Maybe a little more next quarter. With mortgages, it doesn’t work like that.

Realistically addressing technical debt means planning. Budgeting. It means dedicating cycles not just to features, but to code stewardship. It might mean saying no to a roadmap item because the foundational work underneath hasn’t been serviced in years.

This is where the leadership conversation often breaks down. When you say, "We need two sprints to refactor this module," the response can be, "Can’t it wait? The feature is working, isn’t it?"

That’s when the metaphor matters. Because when leadership thinks of tech debt like a credit card, they imagine a few interest points, not a ballooning principal.

But reframed as a mortgage? Suddenly, it’s about long-term value. About protecting the asset. About making sure the thing you’re building doesn’t collapse because the foundation was rushed.

### Talking to Leadership: From Metaphor to Metric

Executives don’t lose sleep over code quality. They lose sleep over delivery risk, cost overruns, and reputational damage. So if you want to talk about your architectural debt, don’t show them a burndown chart. Show them what the debt is *costing*.

* How many developer hours are lost to brittle test suites?
* How many bugs originate from a known "legacy zone" of the codebase?
* How many features were de-scoped because the platform couldn’t support them without massive workarounds?

Translate those numbers into dollars. Into time. Into attrition risk. That’s the language of the executive team.

And when they ask, "How do we fix it?", don't promise a heroic rewrite. No one refinances a mortgage with a hammer. Propose a plan. Replatforming the billing engine? Great. What’s the yield? What dependencies get unblocked? What future innovations does this unlock?

### Intentional Debt Isn’t Bad. Unacknowledged Debt Is.

Not all technical debt is a mistake. Sometimes you *should* take on debt—to hit a critical deadline, to validate a risky idea, or to meet an integration need that may not exist in six months.

But intentional debt is documented. It comes with an agreed-upon plan to address it. It's visible. Like an amortization schedule. You don’t just hope it disappears when the market gets better.

It’s when the shortcuts are forgotten, when the workaround becomes canon, that the system starts to rot.

### In Closing

I’ve lived through system rewrites that took longer than the original builds. I’ve inherited platforms whose core logic no one could explain. I’ve seen teams burn out maintaining a thing they didn’t build, making only marginal improvements because no one would approve the real fix.

So yes, technical debt is a form of borrowing. But let’s stop pretending it's just about speed or tradeoffs you can clear with a few good sprints. The next time someone says, "We’ll pay it down later," ask: *What are the terms? What's the collateral?*

Because you’re not just borrowing time. You’re mortgaging your future.

And if you don’t plan for the payments, you’ll eventually lose the house.


