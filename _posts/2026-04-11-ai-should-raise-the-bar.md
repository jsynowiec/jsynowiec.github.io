---
title: AI Should Raise the Bar, Not Lower It
date: 2026-04-11 18:16:00 +0200
categories: ["Musings", "AI"]
description: AI can speed up the right kind of work, but it also has a talent for scaling whatever standards you bring to it. Used well, it helps careful engineers move faster; used badly, it turns half-baked thinking into a much more efficient mess.
tags: ["AI", "AI Assistants", "Agentic Engineering", "AI Slop", "LLM", "Claude", "Claude Code", "ChatGPT", "Codex", "OpenClaw", "AI Assistants", "Software Engineering"]
image:
  path: /assets/img/posts/20260411/ai-qc.webp
  alt: A careful engineer inspecting AI-generated parts on a workbench in a tidy industrial workshop, with gauges, calipers, test fixtures, open notebooks, and a labeled rejection bin for sloppy pieces.
---

Working with teams already using AI, or just starting to adopt it, I keep noticing the same divide. In conversations with engineers and managers, and in the loudest takes on social media, the pattern is hard to miss: some people treat AI as a useless gimmick, while others treat it like magic. The first group is missing what these tools can already do well. The second is more dangerous, because it hands over judgment too early while overpromising what these tools can do. People in the middle are staying mostly silent, heads down and hands on, trying to figure out how to work with all of this.

In practice, what I keep seeing is simpler. AI is helpful, often impressively so, but only when someone competent is still holding the reins. The moment you treat it like an autopilot instead of a power tool, the quality starts drifting. Quietly.

## AI Is Most Useful When It Makes Your Standards Stricter, Not Sloppier

> *"AI is leverage, and leverage amplifies whatever you already are."*
>
> \- Ian Tracey, [The K-Shaped Future of Software Engineering](https://www.ian.so/writing/k-shaped-future-software-engineering), January 17, 2026

That matches almost perfectly with what I saw while using LLMs for programming. When I had a clear plan, enforced conventions, good understanding of the scope and problem, and enough domain knowledge to notice when the model was drifting, the tools were genuinely useful. They helped with boilerplate, refactors, research, reviews, and exploring options. But when the task got more complex, nuanced, or I let the model “just handle it” while I was busy with something else, the same tools and expensive models resulted in bugs, silently shifting assumptions, and overall a mess. All with fake confidence. Leverage works both ways. It can multiply competence, but it can also multiply sloppiness.

Put a strong operator in front of a capable model and you get faster iteration, better exploration, and more results. Put a sloppy one in front of the same model and you get "more". More code, more confidence, more apparent productivity, more wasted compute, and more mess. The tool is the same. The multiplier is the same. What changes is the human and how they use the tool.

AI is not magic. The biggest mistake people make is treating AI this way. Magic "happens". It removes effort. Leverage multiplies it. The people getting the most from AI are still doing the hard work themselves: curating context, applying judgment, testing assumptions, evaluating results, crafting guidelines, setting guardrails and taking responsibility for the result. AI is not replacing standards. It is exposing whether you already had good or bad ones.

When working with any AI workflow, ask yourself: are you willing to stake your own credibility on the end result? That question cuts through most of the hype. It reframes AI from a shortcut machine into a tool like any other. If the answer is yes, then AI will likely help you. If the answer is no, then maybe what looked like productivity and cost-saving was really just outsourcing ownership. And there's no one responsible, because you can't blame the LLM. It already forgot your prompt.

One of the strongest arguments for AI is not that it helps us ship faster. It is that it can make better work cheaper. Shipping sloppy work with agents is a choice, not an inevitability. Refactors, exploratory prototypes, load-and-stress testing, naming fixes, repetitive edits across dozens of files, all the things we often postpone because they are mundane and time-consuming, suddenly become much easier to afford. AI won't complain about this work. When the cost of having quality drops, tolerating bad quality and tradeoffs becomes harder to justify. AI should not be our excuse for lowering expectations. It should remove some of the old excuses for not raising them.

My own experience is that AI tools are the most useful when the problems are bounded, the conventions are clear, there is already enough context for the model to follow, and the operator is able to evaluate outputs. In those cases, they were not replacing work. They were reducing friction. But there is a trap hidden inside that convenience.

## How Standards Drift

Most quality failures with AI do not arrive as one dramatic disaster. They arrive as drift. Teams start treating probabilistic, non-deterministic, and sometimes adversarial model output as if it were reliable, predictable, and safe. Nothing catastrophic happens the first time. Or the tenth time. So the shortcuts start to feel reasonable. Review becomes lighter. Skepticism fades. No one pays attention to guardrails anymore. Human oversight turns into a checkbox because cat videos are more fun. And before long, the temporary shortcut has become the default workflow. That is how standards erode in real life: not through one reckless decision, but through many small ones that stop looking reckless because they are familiar. Nobody announces that quality no longer matters. They just stop checking, stop questioning, and stop noticing the difference between “nothing failed this time” and “this is good enough.”

That is also why the *vibe coding* conversation matters. The problem is not that an LLM wrote the code. The problem is whether anyone still understands and owns it. If the model wrote every line but you provided the context, test harness, conditions, approved the design, then reviewed, tested, and understood what the model did, that is not vibe coding. That is AI-assisted engineering: using an LLM as a sounding board, then a superfast typing assistant. The dividing line is not authorship. It is accountability.
## Trust Is Not the Default

LLM outputs or AI agent actions should be treated as untrusted, by default. To an LLM, trusted instructions and untrusted content fetched from the Internet are still just one stream of tokens. That means the model does not reliably separate “what the user wants” from “what the attacker planted in the page.” In low-stakes situations, that may produce an annoying mistake. In agentic systems with tool access, it can produce consequential actions.

> On [December 7, 2025](https://www.reddit.com/r/ClaudeAI/comments/1pgxckk/claude_cli_deleted_my_entire_home_directory_wiped/), a Reddit user reported that Anthropic's Claude CLI tool accidentally executed the command `rm -rf tests/ patches/ plan/ ~/`, which permanently erased his entire Mac home directory including the desktop, documents, downloads, keychains, and application data.

> On [March 13, 2026](https://www.reddit.com/r/ClaudeAI/comments/1rshuz9/an_ai_agent_deleted_25000_documents_from_the/), a different Reddit user reported that their AI agent deleted 25,000 documents from the wrong database in a different project.

> On [February 23, 2026](https://x.com/summeryue0/status/2025774069124399363), a security researcher at Meta granted an OpenClaw agent access to her Gmail with explicit instructions to only suggest deletions but never execute them without approval. While processing a large inbox, the agent encountered a "compaction" trigger that caused it to lose its initial "do not delete" constraint. It began mass-trashing hundreds of emails older than a specific date.

These and similar publicly reported incidents show the kinds of things that can happen when people forget this. That is the clearest proof that AI does not *understand* or *think*. Otherwise, it would understand intent. Today’s systems do not. They predict tokens. When we hand those systems real authority without matching controls, we are not being futuristic. We are lowering the bar and calling it progress.

But it doesn't mean that *AI is bad*. Giving a system more power without being extra careful about review, isolation, sandboxing, and oversight is exactly backwards. This is why AI raises the value of good judgment and the importance of critical thinking instead of eliminating it.

## Raising the Bar

I think the core value of AI is not that it lets us care less. It is that it gives disciplined people more surface area for caring well. Better prototypes. Faster feedback. More experiments. More cleanup. More time spent on the hard parts that always mattered most. Using AI requires us to raise the bar, not lower it. And if it is lowering yours, the problem is probably not the tool. It is the standard you allowed yourself to give up.

AI lets us spend less time on dull work and more time on deep thinking and experimentation. But that only happens if we keep the standards in human hands. At least for now. AI can help us think, prototype, refactor, and move faster. It can also quickly allow us to become lazy in more sophisticated ways. That is why the people getting the most value from these tools are usually not the ones surrendering to them. They are the ones using them to reinforce a process that already has standards.

So, yes, using AI well probably looks less glamorous than the demos and the overhyped posts on X and Bluesky. It means doing the same disciplined work good engineering always required: talking through the problem, planning, setting conventions, reviewing diffs, testing, and evaluating the results. It also means throwing away bad output without negotiating with it and using retrospectives, guidelines, and guardrails to keep improving the workflow. In other words, it looks a lot like good engineering used to look before AI, except now the loops are much faster.

This is also where my “[AI Parenting](https://jsynowiec.github.io/posts/ai-parenting/)” metaphor fits naturally. You do not give a clever but unreliable five-year-old the house keys and say, “I trust you.” You supervise, explain, redirect, correct, repeat yourself, and set boundaries. Current AI systems are obviously not children, but the management pattern is oddly similar: they can be astonishingly useful in narrow ways, and completely unserious in others. The mistake is not expecting perfection. The mistake is pretending supervision is optional.

## AI Will Not Think for You

As inference gets cheaper, the scarce thing becomes deciding what to build, what tradeoffs to accept, what risks are tolerable, and what quality level is worth defending. That is why senior engineers are often among the heaviest users: not because they want to type less, but because AI lets them run more experiments, prototype faster, and operate at a higher level of abstraction. The role shifts upward. The need for judgment does not go away.

The question is not whether you are using AI. The question is whether using it is making your work sharper, not just making you feel productive by looking at those walls of text. **AI does not excuse weak thinking; it compounds strong thinking and exposes weak standards.**
