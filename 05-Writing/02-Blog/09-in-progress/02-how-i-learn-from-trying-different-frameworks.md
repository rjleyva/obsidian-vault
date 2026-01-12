---
title: How I Learn from Trying Different Frameworks
description: My unconventional approach to learning web development—embracing framework hopping, learning through comparison, and using experimentation to understand tools deeply.
tags:
  - framework-hopping
  - learning-methodology
  - comparative-learning
  - experimentation
  - tool-selection
  - react
  - astro
  - web-development
created: 2025-12-22
updated: 2026-01-04
---

Hi it's RJ, and today I want to share how I learn from trying different frameworks—not as a tutorial, but as someone who's been through the messy process of framework hopping and come out with genuine understanding.

## What Drives My Framework Exploration

Every time a new framework emerges, it shines like a freshly polished tool in a crowded workshop. Its simplicity, elegance, and promise of quick mastery can easily lure beginners like me. I've felt that pull, the temptation to dive in headfirst simply because it looks easy to use.

But I've learned to pause. Instead of chasing novelty for its own sake, I ask myself: What tangible benefits does this bring? Which problems does it truly solve compared to my current workflow? Why choose this path over another? And—most importantly—when does it make sense for the project I'm building?

This approach turns learning from a superficial sprint into a deliberate, meaningful journey. It's less about following trends and more about understanding purpose.

## From React to Astro to SvelteKit: A Case Study

To illustrate this comparative learning approach, here's how it played out in my own development journey. In August 2025, I hit a wall trying to fetch and render local markdown files in React. The documentation focused on API calls, not local file handling, and I was stuck for weeks, feeling like an imposter.

**The Astro Detour**
Frustrated, I jumped to Astro. "If React can't handle markdown well, maybe Astro can," I thought. Within two weeks, I built a working blog and discovered `import.meta.glob`—the magical Vite function for importing multiple files at once. Suddenly, markdown processing felt possible.

**The SvelteKit Experiment**
Instead of returning to React immediately, I tried SvelteKit after seeing a tutorial. There I found mdsvex and shiki—powerful tools for markdown processing and syntax highlighting. I didn't fully understand them, but I knew they were pieces I needed for my React project.

**The Return with Knowledge**
Armed with `import.meta.glob`, mdsvex concepts, and shiki, I returned to React. Suddenly, the original problem wasn't impossible anymore. The "detours" weren't wasted time—they were essential learning steps that gave me the perspective I needed.

This case study demonstrates comparative learning in action. For the full story of how this approach shaped my entire 2025 frontend journey—from tool obsession to deployment—you can [read](What%202025%20Taught%20Me%20as%20a%20Frontend%20Developer.md) my year-end reflection on what 2025 taught me as a frontend developer.

## Learning the Patterns Through Comparison

When I dive into a new framework, one of the first things I notice is the syntax—the patterns, the way pieces fit together. As a beginner, logic often feels like a foreign language. I've learned that it's okay to feel lost at the start. That confusion, frustrating as it can be, is also the part that makes the journey thrilling: the puzzle of picking up tiny fragments of information and slowly connecting them into something meaningful.

I've accepted that there's no shortcut. When I get stuck, I turn to ChatGPT, asking it to explain things in beginner-friendly ways, often with analogies I can relate to. I don't shy away from the "dumb" questions: What is a React hook? Why do some YouTubers use Zustand? Can I skip React hooks and jump straight to Zustand?

Sure, my questions reveal my confusion—but over days, the pieces start to click. I begin to see why Zustand is not a replacement but an essential tool, and why Zustand becomes valuable when managing complex state, like comments and reactions on my blog. Simple tasks like theming still suit useState, but when coordination grows tricky, a tool like Zustand turns chaos into clarity. Slowly, I begin to understand what "complicated" really means in the context of code—and why learning the basics matters before chasing the next shiny tool.

## We Humans Are Not Perfect (And That's Okay)

Another crucial part of my learning journey is embracing imperfection. I've learned that it's not enough to simply jot down solutions—I need to capture the confusion, the "why" behind each step, and the thoughts that swirl around my head as I try to make sense of it all.

This is where [Inkdrop](https://www.inkdrop.app/) comes in. It's a note-taking app that doesn't distract me, doesn't pull me away from the flow of learning. Instead, it gives me focus. It allows me to write freely, to explore my thoughts, and to slowly connect the dots at my own pace. Less friction, more space for curiosity—and more time to truly understand.

## Applying Comparative Learning to Your Journey

When you're considering a new framework, ask yourself these questions:

- What specific problem am I trying to solve that my current tools don't handle well?
- What would success look like with this new framework?
- How does this compare to alternatives in terms of learning curve, ecosystem maturity, and long-term maintenance?
- When should I explore versus deepen my current knowledge?

## The Power of Intentional Detours

Framework hopping might seem chaotic, but when done intentionally, it builds deeper understanding than following a straight path ever could. Learning from great developers who solve different problems across the web ecosystem gives you a toolkit of approaches—not just one way of thinking.

It's not about knowing every framework; it's about understanding which tools excel at which problems, and having the wisdom to choose the right one for your current challenge.

This comparative learning approach has taught me that the most valuable skill isn't framework mastery—it's knowing how to evaluate, experiment, and adapt. The frameworks will change, but this way of learning endures.
