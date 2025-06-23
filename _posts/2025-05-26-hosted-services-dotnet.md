---
layout: post
title: "The Quiet Workers: Hosted Services in .NET Web Applications"
date: "2025-05-26 13:30:00-05:00"
updated: "2025-05-15 13:30:00-05:00"
permalink: "/2025/05/hosted-services-dotnet.html"
author: Stephen Wrighton
description: Not everything that matters in software makes noise. Some of the most important things our applications do happen quietly. In the background. Polling. Syncing .Cleaning up. Keeping the lights on without ever blocking a user request or lighting up a dashboard.
categories:
tags: [dotnet, Software Engineering, Code Quality, Software Architecture]
---  

There’s a beauty in code that just works—quietly, predictably, without fanfare. The kind of code that sits beneath the surface and hums along whether anyone’s watching or not. In the world of ASP.NET Core, Hosted Services fit that role perfectly.

I stumbled into Hosted Services while modernizing an older batch-processing system. The legacy version used a Frankenstein mix of scheduled tasks and console apps duct-taped to the Windows Task Scheduler. It worked. Until it didn’t. A missed dependency here, a server restart there, and the whole thing came crashing down.

.NET Core gave us a better way. Not louder. Just smarter.

## What Are Hosted Services?
In simple terms, a Hosted Service is a background task that lives alongside your ASP.NET Core application. They’re ideal for recurring jobs, background queues, polling tasks—anything that doesn’t need to block a user request but still needs to get done.

They implement the `IHostedService` interface and integrate with the ASP.NET Core generic host, giving them lifecycle hooks to start and stop cleanly with the application.

And that matters. Because production systems don’t forgive sloppiness, not anymore. If you’re working in healthcare, finance, or anything even adjacent to compliance, background workers need to be first-class citizens.

The Core Interface: `IHostedService`
Here’s the skeleton:

    public class MyWorker : IHostedService
    {
        public Task StartAsync(CancellationToken cancellationToken)
        {
            // Start background logic here
        }
        public Task StopAsync(CancellationToken cancellationToken)
        {
            // Gracefully shut down logic here
        }
    }
For most scenarios, you won’t stop there. You’ll also want `BackgroundService`, an abstract base class that gives you a managed `ExecuteAsync()` loop and built-in support for cancellation:

    public class TimedWorker : BackgroundService
    {
        protected override async Task ExecuteAsync(CancellationToken stoppingToken)
        {
            while (!stoppingToken.IsCancellationRequested)
            {
                // Do your work
                await Task.Delay(10000, stoppingToken);
            }
        }
    }
It’s simple. Intentionally so. But under the hood, you get proper cancellation handling, dependency injection support, and clean startup/shutdown behavior—all the things you’d otherwise be duct-taping together yourself.

## When to Reach for a Hosted Service
Hosted Services aren’t for everything. But they shine in a few key areas:

 * **Polling External APIs** – checking every few minutes for new messages, events, or metrics.
 * **Background Processing Queues** – dequeueing and processing jobs outside the HTTP request cycle.
 * **Scheduled Jobs** – periodic cleanup tasks, database pruning, cache refreshes.
 * **Long-Running Workers** – services that do a little bit of work all the time.

In one project, we replaced a brittle integration that ran as a separate Windows Service. By moving it into a BackgroundService, we deployed and monitored it alongside the rest of the app—no separate CI pipeline, no extra VM, no special permissions.

## The Threading Trap
But here’s the catch: just because you can run code in the background doesn’t mean you should do it without thinking. ASP.NET Core runs on a thread pool. If your background task is CPU-bound or long-running without yielding, you’ll starve the main app of threads.

That’s why `async/await` is so important here. Always yield. Always respect CancellationToken. Don’t block threads unless you absolutely have to—and if you do, isolate it with Task.Run.

## Integration Done Right
What I appreciate most about Hosted Services is how they participate in the application's lifecycle. They start when the app starts. They shut down when the app does. They have access to the same DI container, logging infrastructure, and configuration system.

That integration isn't just convenient -- it's clean architecture in practice.

It reminds me of the quiet operators on a well-run team. Not loud. Not flashy. But always delivering. And always dependable.

## Want to Dive Deeper?
The Microsoft docs do a good job of covering the full implementation details here: [Microsoft Learn: Background tasks with hosted services in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-9.0&tabs=visual-studio)

If you’re building something in .NET Core and you find yourself writing a new service just to "run in the background," chances are you don’t need a new service. You just need a Hosted Service.

And honestly? That’s a win.

