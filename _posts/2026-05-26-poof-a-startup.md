---
title: Poof. A Startup.
date: 2026-05-26 18:25:18 +0200
categories: ["Musings", "AI"]
description: Vibe-coded apps are everywhere, and most fall apart the moment they meet a real user. AI hasn't killed software discipline. It's just made ignoring it effortless. An observation on scope creep in the age of AI, and why infinite capacity might be the worst thing to happen to software.
tags: ["Scope Creep", "Productivity", "AI", "Vibe Coding"]
image:
  path: /assets/img/posts/20260526/poof-a-startup.webp
  alt: A cheerful Lego-style unicorn, haphazardly assembled with its horn attached to its tail and one leg upside down, falling apart mid-pose with colorful plastic bricks scattered around it. A frappuccino cup sits nearby. Pastel gradient background, soft lighting, isometric view.
---

Recently, I've been exploring the abundance of Markdown editors. This type of app seems to be today's new "To-Do List" project, the kind everyone was building a few years ago. Multiple such applications are vibe-coded in Rust, Zig, and Swift every few days, each claiming to be the most awesome. Fast, native, and feature-complete. Unfortunately, 9.5 out of 10 are glued together using mostly the same underlying components and similar UI patterns. Then, when exposed to real-life use cases (my notes vault has hundreds of files varying in length and complexity, often pushing what Markdown can do to its limits), they break. I've seen apps packed with _hype_ features like AI integrations, built-in LLM wikis, fancy RAG pipelines, and automated filing and tagging. But these apps often don't get the basics right, from incorrect rendering, to missing viable edge cases like wikilink pipe aliases in a Markdown table, to outright overwriting or deleting notes due to bugs.

Before the AI slopanza, we were deliberate and thoughtful about what and how we built. Time and resources were finite, so we had to be disciplined, carefully picking the right challenges and constantly reconsidering what to focus on. Managing scope creep was a core responsibility at every level.

Now, AI allows us to stretch the *finite resources* and build everything we can think of, and more. It's a godsend for creative professionals. You just type (or speak) what you want and it "magically" happens. Poof. You have a new 1-million unicorn ready while grabbing a frappuccino at Starbucks. (Yes, that's sarcasm.) We're having a great, dopamine-fueled time building 3-5-10 things in parallel while tokenmaxing. Iterating, redesigning, rebuilding the same thing over and over. Often reinventing the wheel and documenting decades-old software engineering principles in Markdown files. Don't get me wrong, there's real joy in this. I'm having fun myself, and in some areas I am actually more productive. But with everything happening at once, what's the point? What's the goal? Because it's definitely not the fake productivity.

The deeper danger is that we lose focus, distracted by each new shiny thing the army of AI agents creates. Some people do ship. Some even make money, sometimes a lot. Most, however, don't. Instead, we only _feel_ productive and end up with thousands of lines of code, but overall, we're in the same place.

Then there's the product quality problem I started this post with. If 101% of the code is built by agents from a two-sentence prompt, that "product" will, sooner rather than later, break under real use cases. Sure, you can _fix_ it with another prompt, but that won't repair the broken contract or restore the trust lost when others depend on your software. There's also [Hyrum's Law](https://www.hyrumslaw.com/). Every feature you release to the public becomes a contract with unintended consequences. Backward compatibility and managing [leaking interfaces](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/) were tricky long before GenAI. Now it's close to being impossible when it's the AI making up, and breaking, the abstractions.

So, discipline — keeping sight of the goal and deliberately moving toward it while _getting things done_ — matters more now than it did five to ten years ago. Ship the smallest thing that moves you toward your goal. Do one thing great at a time instead of three things poorly.
