---
title: "AI Agents Have Goals. DRIs Have Consequences."
date: 2026-07-13 16:44:31 +0200
categories: ["Musings", "AI"]
description: AI agents can pursue goals, coordinate work, and operate with increasing autonomy. But until they can own the consequences, the DRI still has to be human.
tags: ["AI", "DRI", "Ownership", "Automation"]
---

I’ve recently seen a few posts and discussions asking whether an AI agent can be a DRI. The argument is usually this. If an autonomous agent can pursue a goal, coordinate work, make decisions, and report results, why shouldn’t it be treated as the Directly Responsible Individual?

As I understand it, a **Directly Responsible Individual (DRI)** is the one named person who owns every outcome for a specific goal. Not a task assignee, but a frontline leader who accepts accountability for everything that happens within that scope. The DRI owns the results, including failures caused by bad assumptions, weak communication, missed dependencies, or decisions made elsewhere. That ownership may have practical limits, of course, since nobody controls everything. But the defining word is still **accountability**.

The DRI operates across two interdependent dimensions.

- The **work itself** involves structuring the work, keeping it on track, and stopping it when it no longer makes sense. This part can be understood by looking at how the work was done.
- The **people side** involves influencing without formal authority, building trust across teams, and dealing with competing interests. This part is harder to measure, but equally critical.

Every DRI must keep adjusting between competing needs, which Willink and Babin call the Dichotomy of Leadership[^1]. Extreme ownership must be balanced with delegation, or it turns into micromanagement. Standard operating procedures and written artifacts must be balanced with flexibility, or discipline becomes bureaucracy. Aggressive prioritization must be balanced with wider awareness, or focus becomes target fixation. Close collaboration must be balanced with putting the goal ahead of personal loyalties, or loyalty becomes favoritism. These aren’t switches. They’re dials, and the useful setting changes with context.

A crisis may require more direct control and less delegation. A mature initiative may require less direct involvement in the work and more trust in the people doing it. Getting that calibration wrong is often how a well-intentioned DRI becomes either a bottleneck or a name in a project tracker.

In remote-first and async contexts, the DRI carries an additional burden. The people side is harder because the ambient trust-building signals of co-located teams, such as shared meals, coffee breaks, body language, and hallway presence, are mostly absent or replaced by virtual prosthetics. Slack reactions can do many things, but recreating a five-minute conversation over coffee isn’t one of them. The DRI must compensate by deliberately building trust through proactive one-on-ones, explicit appreciation, and patience across time zones.

Owning problems before they become failures becomes essential in a remote-first context. The DRI must verify that handoffs are clear, confirm that async updates reached the right people, and check dependencies before deadlines arrive. The goal is to prevent failures that might otherwise have been caught through proximity, informal conversation, or someone noticing a worried face across the room.

This is the person who ensures that strategic bets become team objectives, that accountability includes behavior rather than only KPI reporting, and that teams don’t quietly drift back toward old habits once the offsite deck has been archived and forgotten.

The DRI’s name is on the bet. They report not only what happened, but how the team is operating. They shield the team from distractions, absorb interference, and protect its focus so the strategy becomes something the team actually does, not a document produced at an annual offsite.

Which brings us back to AI agents.

An LLM-powered agent may plan work, call tools, coordinate tasks, inspect outputs, and escalate failures. Depending on the context, it can send emails, write documents, write code, execute payments, and do much more. It may perform many parts of *the work* extremely well. In some cases, it may even perform them more consistently than a human.

But accountability can’t be reduced to successful task execution.

As long as an agent cannot meaningfully accept consequences, make its own judgment about what is right and appropriate, or own an outcome of its own volition, I don’t think it can be considered a DRI.

It can support one, true. It can act on behalf of one, and it may perform much of the visible work. But the name on the bet still has to belong to someone who can answer for it.

Even before we get to the people side.

> *A computer can never be held accountable, therefore a computer must never make a management decision.*
>
> \- IBM Training Manual, 1979 via [bumblebike](https://x.com/bumblebike/status/832394003492564993)

## Sources

- **Jocko Willink & Leif Babin**, *Extreme Ownership: How U.S. Navy SEALs Lead and Win* (2015), *The Dichotomy of Leadership* (2018)
- **Jocko Willink**, *Leadership Strategy and Tactics* (2023)
- **Mickey Mantle & Ron Lichty**, *Managing the Unmanageable: Rules, Tools, and Insights for Managing Software People and Teams* (2019)
- **Will Larson**, *An Elegant Puzzle: Systems of Engineering Management* (2019) and *Crafting Engineering Strategy* (2025)
- **Michael Lopp (Rands)**, "Become the Consequence" (2025) [link](https://randsinrepose.com/archives/become-the-consequence/)
- **Richard Rumelt**, *Good Strategy Bad Strategy* (2011)

[^1]: The Dichotomy of Leadership is the meta-principle that appears in Extreme Ownership, The Dichotomy of Leadership and Leadership Strategy and Tactics. Every leadership quality exists in tension with an opposing quality, and effective leadership requires continuous calibration. For example, aggressive but not overbearing; calm but not robotic; close with troops but not so close that one person becomes more important than the mission.
