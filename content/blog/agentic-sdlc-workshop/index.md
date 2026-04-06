---
title: "Okay Fine, I'll Let the Robots Help"
date: 2026-04-05
description: "What I learned building two projects with AI agents — from Multiverse School workshops to shipping real code."
draft: true
---

Hey — are you drowning in the AI noise too? Same. There's a firehose of content out there and I had zero idea where to begin. Worse, I felt morally tangled up in all of it. But I'd been following [Liz](https://www.lizthe.dev/) on socials, vibed with their politics, and figured if anyone was going to teach this stuff without the techbro energy, it'd be them. So I signed up for the [Agentic SDLC workshop](https://themultiverse.school/classes/193) at [The Multiverse School](https://themultiverse.school/). Turns out it was the on-ramp I'd been looking for — hands-on, welcoming, zero judgment. I'm eyeing their [Intro to Agents: 1-Day Intensive](https://themultiverse.school/classes/192) next.

### > Workshop #1

Brain: overloaded. So much to process — and honestly most of the friction was between my own ears. Can I actually trust these agents? Is this going to go sideways? But then... it just moved. Fast. Before I'd even finished second-guessing myself, the agents were writing code.

### > Workshop #2

Came back for round two — lifetime access, so why not. This time I showed up with the Claude Code Max plan (bit the bullet on that $200) and a lot less fear. Everything clicked differently. That same day I started building my first Android app, [Khushu](https://github.com/fat0/khushu).

### > Notes to Self (and You)

A few things that hit different after building with agents...

- How you set up a project matters a lot. Tools like [OpenSpec](https://github.com/Fission-AI/OpenSpec/) and [Superpowers](https://github.com/obra/superpowers) help you lay that groundwork before the agents start going brrr.
- The tooling moves terrifyingly fast. What you learned yesterday might already be outdated. Get cozy with that feeling.
- Your first draft will look like spaghetti — and that's totally fine. Refactoring is cheap now. Let the agents get you to a working MVP, then worry about making it efficient, resilient, scalable, clean... later.
- That said — guard your secrets like your life depends on it. Tell your agents upfront: no credentials in git, ever. Bake security in from day zero, not as an afterthought.
- Before your first commit: Tell your agent not to co-author your commits. Rewriting git history later is no fun (even with agents).
- You are the bottleneck. I found this out the hard way juggling two projects at once. The agents kept pace. My brain did not. Turns out context switching is still very much a human problem.
- Pro tip: when Claude gets stuck, tell it to add debug logging and walk you through the code step by step. Half the time it finds the bug before it even finishes explaining.
- Want to go full swarm mode? Tools like [Paperclip](https://github.com/paperclipai/paperclip) let you orchestrate multiple agents working in parallel. Fair warning though — I found it overwhelming at first. My advice: start with one agent, get comfortable, build some muscle memory. Then go multi-robot.

Shoutout to [Liz](https://www.lizthe.dev/) and all the awesome humans keeping [The Multiverse School](https://themultiverse.school/) alive. From teaching folks how to resist big tech fascism that's tearing at the fabric of human existence, to sliding-scale workshops and free classes, to building spaces that are genuinely inclusive while the world gets more hostile toward the most marginalized — their tagline nails it: *"Unhinged Education for an Unhinged World."*
