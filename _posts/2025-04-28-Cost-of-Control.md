---
layout: post
title: "The Cost of Control: Why your Coprorate Network Isn't Ready for the Way We Work Now"
date: "2025-04-28 13:30:00-05:00"
updated: "2025-04-28 13:30:00-05:00"
permalink: "/2025/04/Cost-Of-Control.html"
author: Stephen Wrighton
description: We had the developer. The timeline. The budget. What we didn’t have was a network that could handle an outsider. One week, six provisioning tickets, and an Office 365 license later, we gave up. Not because the work wasn’t needed, but because our infrastructure couldn’t flex. That project should’ve been a win. Instead, it became a lesson.
categories: 
tags: [Strategy, Management, Business Goals, Leadership]
---  

We had the perfect developer for the job. A specialist in the legacy tech stack, available immediately, and experienced with short-cycle delivery.

All we needed to do was bring him into the project.

That should have been easy. But it wasn’t.

To access the codebase, he needed to connect to our internal DevOps server, which lived behind the corporate firewall. And to get through the firewall, he needed VPN access. But our VPN required an Active Directory account, and our group policies didn’t play well with machines outside the domain.

So we gave him an AD account. Then we added an Office 365 license so he could receive email and MFA prompts. We stood up endpoint protection, created a shared OneDrive folder, and added him to Teams so he could join the daily stand-up.

By the time we were done, we had spent more time provisioning access than it would have taken to build the first sprint. And he still couldn’t fully function. Build scripts broke. Authentication failed. Nobody could agree on whether he needed admin rights or not.

We pulled him from the project a week later.

That moment stayed with me. Not because it was unusual, but because it happened far too often.

## The Legacy of the Inside-Only Network
Most corporate networks were never built for flexibility. They were designed to protect internal assets, enforce strict controls, and keep the outside world out. If you were inside the building, you were trusted. If you weren’t, you weren’t.

But the way we work has changed.

Hybrid is the default. Remote is a constant. And more companies are relying on external contributors, contractors, and off-site partners to scale fast without adding permanent headcount.

Unfortunately, our networks still operate like they did fifteen years ago.

Authentication is tied to on-prem Active Directory. File access depends on mapped drives and internal shares. Source control lives behind the firewall. Identity and provisioning are locked into systems that assume everyone is a full-time, badge-carrying employee.

That rigidity creates friction. And friction kills momentum.

## Building a Network That Reflects Modern Work
Modernizing your network is not just a technical project. It is a foundational shift in how your company supports its people, no matter where they are or how they work.

1. **Decouple identity from employment:** Access shouldn’t require an Exchange inbox. Embrace identity providers like Azure AD or Okta that allow guest accounts and federated sign-ins. Your developer doesn’t need a mailbox. He needs scoped access to the code and tools that let him contribute securely.

2. **Use role-based, time-bound access:** Zero Trust works because it aligns with how people contribute today. Access should follow policy, not guesswork. Provide just enough permission, for just long enough, and audit everything.

3. **Get your developer tools outside the firewall:** If a VPN is the only way to clone a repo or run a build, your tools are stuck in the past. Use GitHub, GitLab, or Azure DevOps in the cloud. Adopt CI/CD platforms that support ephemeral build runners and secure deployment keys. Let access be controlled by code and policy, not manual setup.

4. **Let communication flow with the contributor:** External collaborators need to be part of the conversation. Tools like Slack Connect, Teams Guest Access, and shared docs make it possible to work together without dragging someone through your internal onboarding maze. What matters is getting questions answered and decisions made without delay.

## Why It Matters
The companies that will succeed in the next decade are not the ones with the biggest internal headcount. They’re the ones that can adapt quickly, plug in the right contributors, and keep projects moving without a three-week provisioning process.

If your infrastructure can’t support a skilled outsider for a short-term assignment, it’s not secure.

It’s just inflexible.

And in today’s world, inflexibility is what makes good teams walk away.