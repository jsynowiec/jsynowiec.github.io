---
title: "Side project: Duck.ai Tools"
date: 2026-05-08 13:46:19 +0200
categories: ["Sideproject"]
description: "A small side project I worked on this week: a set of tools to enhance data portability from Duck.ai, the private AI chat feature of DuckDuckGo."
tags: ["Side-project", "Tools", "DuckDuckGo", "Duck.ai", "AI Chat"]
---

If you are just looking for the tools, scroll down to the [#Source Code](#source-code).

---

[Duck.ai](https://duck.ai) is a private chat feature of DuckDuckGo that lets you chat with various AI models without sharing identifiable information like IP address, account metadata, or browser fingerprinting. Conversations are anonymized and your chat history stays local.

I've been recently using Duck.ai for most of my casual research, chats, and searches. It's simple, with a clean UI, and the subscription limits are generous. I haven't hit any yet, and I've been using Duck.ai *a lot*.

The biggest downside is that Duck.ai lacks an easy way to export and archive conversations, and the end-to-end encrypted sync option is exclusive to the DuckDuckGo web browser. While you can manually select and export chats, the resulting text files aren't user-friendly.

A quick check revealed that the Duck.ai web application uses an IndexedDB database, so exporting all conversations is straightforward. A few minutes in the console and I had a working JavaScript snippet. At this point I could either create a browser extension or a snippet. While it's harder for non-technical users to use a snippet, it's much easier to distribute for this size of code.

Next was reverse-engineering the schema. For that, I used OpenCode (currently my go-to coding agent harness) and it inferred two JSON Schema files, one for the export and one for the chats. Some parts of the latter are guesswork, but it's sufficient for this use case.

The last step was building something to browse the exported chats, preview them, and convert them to something friendlier to read offline. Again, I used OpenCode to *grill* me and build a PRD, a detailed plan with specific assumptions and requirements, and a list of tasks. After a few review iterations and small corrections, I let OpenCode build it while I got back to reading Starsight by Brandon Sanderson.

## Update: May 13, 2026

I moved to augmenting Duck.ai UI with extra features using user scripts. I considered building a browser extension but opted for user scripts as a simpler and faster way to iterate. A browser extension would have release and cross-browser compatibility overhead. With user scripts, I can focus on functionality and leverage existing, tested extensions like [Tampermonkey](https://www.tampermonkey.net/) or [Userscripts](https://itunes.apple.com/us/app/userscripts/id1463298887) to inject and run the scripts I create. This lets me focus fully on functionality.

So far, I've created three power-user features:
- a keyboard shortcuts cheat sheet and a keyboard shortcut to open Duck.ai settings,
- a locally-stored quick prompts picker,
- a Spotlight-style chat search and switcher.

These are geared toward power users and intended for people who prefer to use the keyboard and keyboard shortcuts for most interactions. The chat search and switcher greatly improves navigation over the chat history, while the prompt picker allows you to store and quickly insert your most frequently used prompts.

I'm using all these scripts myself, mostly in Safari, but they should work in other browsers too (I tested Firefox and Helium). All scripts are in plain JavaScript with no imports, build step, or external dependencies. They use standard DOM and browser keyboard APIs to remain compatible with Safari, Firefox, and Chrome.

## Screenshots

### HTML Export

<img src="assets/img/posts/20260508/duckai-tools-html-export.webp" width="45%" alt="A screenshot showing HTML transcript of an chat with an AI" />

### TUI

<div style="display: flex; gap: 10px;">
  <img src="assets/img/posts/20260508/duckai-tools-tui-list.webp" alt="A screenshot of a Terminal User Interface (TUI) app with a two-pane layout. The left column lists conversations, while the right pane shows a preview of the selected chat." />
  <img src="assets/img/posts/20260508/duckai-tools-tui-details.webp" alt="A screenshot of a terminal user interface (TUI) app displaying a Markdown preview of an AI chat." />
</div>

### Userscripts

#### Chat Quick Swithcer

<img src="https://github.com/jsynowiec/duckai-tools/raw/main/assets/quick-switch-userscript.gif" width="45%" alt='A screenshot of the Duck.ai interface displaying a search modal where the user has typed "moon", showing suggestions for "Moon distance from Earth" and "Moon count in the solar system"' />


#### Prompt Quick Picker

<img src="https://github.com/jsynowiec/duckai-tools/raw/main/assets/quick-prompt-userscript.gif" width="45%" alt="A screenshot of the Duck.ai interface showing a modal where the user selects a previously saved prompt to insert it into the prompt textarea"/>

## Source Code

The results are available under the MIT license on GitHub: [jsynowiec/duckai-tools](https://github.com/jsynowiec/duckai-tools/). The TUI can be sluggish with larger chats (100KB+) on my M1 MacBook Air, but it's functional, and I'm pleased with the results. It all took less than 40 minutes of total work.

I plan to add more tools and functionality to this repo and already have a few ideas.
