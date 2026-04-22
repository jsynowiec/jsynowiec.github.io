---
title: Apps With Boundaries
date: 2026-04-22 18:52:37 +0200
categories: ["Musings", "Privacy"]
description: Most mobile software assumes perpetual engagement and recurring revenue. This list catalogs the exceptions — applications built with defined scope, clear boundaries, and business models that do not depend on retention metrics. These applications operate on the assumption that user data belongs to the user, not the vendor.
tags: ["Privacy", "Mobile App", "iOS", "Data Portability", "Local-first"]
---

Most mobile applications operate on a model that treats **users and their data as a commodity**: gated features behind recurring subscriptions, mandatory account creation, comprehensive usage tracking, and data export either unavailable or deliberately crippled. The extraction, linkage, and subsequent profiling or sale of that information is the actual business model.

I have been cataloging iOS applications that reject this model in favor of privacy, local-first architecture, data portability, and lifetime ownership.

If you prioritize control over your data and want to minimize your digital footprint without sacrificing functionality, this list represents viable alternatives. Local-first architecture has one additional advantage: data that never reaches a server cannot be compromised in a breach aggregated by data brokers, or weaponized in targeted scams.

## Criteria

- Solves a specific problem and does it well
- 100% free or one-time purchase, including lifetime in-app option; no forced subscription model (optional subscriptions acceptable if they do not gate features)
- Ad-free, or ads removable through one-time purchase
- No data collection: no telemetry, diagnostics, or usage tracking, as indicated in the App Store privacy card
- No required signup; any account must be optional
- All data remains local, on-device
- Open source is not required
- Must be available on the App Store (no sideloading)
- Sync or backup functionality must be provided through Apple iCloud (CloudKit) or user-controlled service; preferably with E2E encryption before transmission
- If data is created in the app, the app must have an option to export it to open formats (Markdown, CSV)

## App List

- [Blood Pressure Analyser](https://apps.apple.com/pl/app/blood-pressure-analyser/id6745785851) provides a clean interface for tracking and analyzing blood pressure.
- [Book Tracker - Reading log](https://apps.apple.com/pl/app/book-tracker-reading-log/id1491660771) keeps track of e-books, physical books, and audiobooks.
- [Coffee Book: Brew Timer](https://apps.apple.com/pl/app/coffee-book-brew-timer/id1512681263) is a coffee brewing logbook for home baristas.
- [Comic Book Viewer](https://apps.apple.com/pl/app/comic-book-viewer/id957475715) displays CBZ-format comics and manga on iPad.
- [Consent-O-Matic](https://apps.apple.com/pl/app/consent-o-matic/id1606897889) a Safari extension that actively rejects optional cookies rather than hiding the prompts.
- [Dime: Budget & Expense Tracker](https://apps.apple.com/pl/app/dime-budget-expense-tracker/id1635280255) is a straightforward personal and home budgeting app.
- [Fresh Cards - Flashcards](https://apps.apple.com/pl/app/fresh-cards-flashcards/id1523398835) is Anki cards, refined.
- [GoodLinks](https://apps.apple.com/pl/app/goodlinks/id1474335294) provides an alternative when Readwise Reader feels like overkill or you prefer not to store content on third-party servers.
- [HealthFit](https://apps.apple.com/pl/app/healthfit/id1202650514) has replaced Strava and other fitness tracking apps for me.
- [Health Lens – CSV Exporter](https://apps.apple.com/pl/app/health-lens-csv-exporter/id6578440958) exports Apple Health data to CSV format for independent analysis.
- [Heart Analyzer: Pulse Tracker](https://apps.apple.com/pl/app/heart-analyzer-pulse-tracker/id1006420410) is the most comprehensive heart data analyzer, essential for monitoring HR, HR zones, and related metrics.
- [Hush Nag Blocker](https://apps.apple.com/pl/app/hush-nag-blocker/id1544743900) is an open-source Safari extension that blocks cookie prompts and tracking.
- [Kagi News](https://apps.apple.com/pl/app/kagi-news/id6748314243) is an AI-powered, curated newsfeed with minimal design.
- [Kagi Summarize](https://apps.apple.com/pl/app/kagi-summarize/id6748308326) is an AI summarizer that registers as a system share action. No account, no tracking. Free while in beta.
- [Liquid Apollo](https://apps.apple.com/pl/app/liquid-apollo/id6448019325) is similar to Locally AI but targets a different use case and connects to more capable models through custom backends or OpenRouter.
- [Locally AI - Local AI Chat](https://apps.apple.com/pl/app/locally-ai-local-ai-chat/id6741426692) is an offline LLM inference server and client that runs on iPhone, iPad, or Mac, keeping all data on-device.
- [Midori (Japanese Dictionary)](https://apps.apple.com/pl/app/midori-japanese-dictionary/id385231773) has not been updated in years but remains functional. Essential for Japanese learners or manga readers.
- [Mullvad VPN](https://apps.apple.com/pl/app/mullvad-vpn/id1488466513) is a zero-logs, privacy-focused VPN. It is an exception to the criteria: it requires an account, collects minimal telemetry, and charges monthly. However, the account is anonymous, the telemetry cannot be linked to you, and you are paying for the VPN service, not the app.
- [NFC Tag Info](https://apps.apple.com/pl/app/nfc-taginfo-by-nxp/id1246143596) is useful for checking NFC tags or Nintendo Amiibo figures.
- [Pass4Wallet](https://apps.apple.com/pl/app/pass4wallet-store-cards/id1423106610) creates custom Apple Wallet passes, tickets, and store cards. Particularly useful when venues do not offer digital wallet options.
- [WorkOutDoors](https://apps.apple.com/pl/app/workoutdoors/id1241909999) covers trail runs, hikes, and outdoor sports with mapping and navigation features on Apple Watch.

These applications share one additional characteristic. They are often developed and maintained by a single dedicated developer or a small team. The trade-off is worth noting. Smaller teams mean fewer resources for rapid feature iteration, but they also tend to produce software with tighter scope, clearer constraints, and more intentional design decisions.

If you value this model, the most effective way to sustain it is to buy some of these apps, use them, and leave reviews. Discovery is increasingly difficult in an ecosystem optimized for recurring revenue, digital invigilation and engagement metrics.

If you know of other mobile apps that meet these criteria, share them on Mastodon. Thanks!
