---
layout: post
title: "Teaching SQL to a New Generation or How to Make Data Click"
date: "2025-06-30 13:30:00-05:00"
updated: "2025-06-20 13:30:00-05:00"
permalink: "/2025/06/teaching-sql-to-new-gen.html"
author: Stephen Wrighton
description: Teaching SQL to new devs is part art, part cautionary tale. I wrote about that moment when it clicks—when they stop writing loops and start thinking in sets. Includes metaphors, cross join disasters, and a little data poetry.
categories:
tags: [SQL, Engineering Leadership, Mentoring, Tech Leadership, Career Growth]
---  


There’s a moment I always look forward to when teaching SQL. That shift behind the eyes when someone stops treating SQL like it’s a loop and starts treating it like it’s a language. Not a language in the way JavaScript is a language, but a language in the way *set theory* is a language. 

Declarative. 
Elegant. 
...And occasionally unforgiving.

I’ve had the chance to mentor a few interns and junior devs over the years. Bright minds, eager to learn, but often trained in procedural paradigms. They’re used to instructing the computer what to do, step by step. So when you ask them to “write a query that joins customer orders with their most recent payment,” you’ll sometimes see a C-style for-loop in their eyes. It makes sense. That’s how most modern programming is taught. One item at a time.

Row, by *agonizing* row.

But SQL doesn't work that way.

Well you can make it work that way, but it doesn't want to work that way. 

I usually tell them that SQL is the art of *slamming multiple books together and having a fully formed book pop out*. It’s not “go grab every page, match it, and glue it.” It’s “define your sets, describe how they intersect, and let the engine do the heavy lifting.”

**Set-Based Thinking**

That metaphor, books slamming together, tends to stick. It reframes the mental model. Tables aren’t lists to loop through. They’re complete volumes of information. A `JOIN` isn’t a function call; it’s a Venn diagram crashing into itself and making something new.

So we start there. With the idea that the *FROM* clause is your canvas, and everything after it, your `JOIN`, your `WHERE`, your `GROUP BY`, are the filters and frames. We talk about how a `SELECT` is a request, not an instruction. It’s not "do this"; it’s "give me a view where this is true."

And then… we run into the first real-world gotcha.

**The Cross Join Surprise**

There’s nothing quite like the day they forget their `ON` clause.

It usually goes something like this:

```sql
SELECT *
FROM customers
JOIN orders;
```

And then they wait.

And wait.

And the CPU fans spin a little louder.

Because what they’ve written isn’t a relational join. It’s a Cartesian product. Every customer matched to every order; a combinatorial explosion. Thousands of customers × thousands of orders = millions of rows.

The lesson hits home: SQL will *do* what you *ask*, not necessarily what you *mean*.

That’s where I pause and draw it out on the whiteboard. Two tables, two clouds of data. “What happens when we tell SQL: ‘Just mash them together’?” And suddenly the abstract becomes visible. The concept of a *cross join* isn’t just syntax anymore. It’s a cautionary tale.

They laugh. And they remember.

**Building Muscle Memory**

Beyond metaphors and mishaps, the key to making SQL stick is practice with purpose. Not rote repetition, but real use-cases: cleaning up CSVs from marketing, analyzing support ticket trends, tracking bug counts per release.

We talk about `NULL`s. The sneaky kind of nothing that breaks your logic if you're not paying attention. We dive into `LEFT JOIN`s versus `INNER JOIN`s and what it really means when one side disappears. We look at how aggregation changes the shape of data. And then we revisit performance: why indexes matter, when subqueries become slow, and how understanding the *shape* of your data can save you hours of frustration.

**The Bigger Picture**

What I’ve come to realize is that teaching SQL isn’t about syntax. It’s about thinking. It’s about unlearning step-by-step logic and replacing it with a map. One where relationships, intersections, and sets define the world.

And maybe, just maybe, it’s about finding the poetry in structure.

Because when you get it, when it clicks, SQL becomes more than a tool. It becomes a way to *see* data.

And the best part? They never do forget their first accidental cross join.
