# AI-Orchestrated Content Operations System
### A self-built system for content strategy, production tracking, and data-driven decision-making — designed and operated for L2Lifestyler

---

## Context

I run L2Lifestyler, a DMV-based lifestyle/fashion content brand for the GenX/50+ audience (54.3K followers, ~655K monthly views across Instagram, TikTok, and Threads), alongside a separate AI Strategy Consulting practice. Managing both — content calendar, production pipeline, performance analysis, and brand-partnership readiness — by hand didn't scale. I designed and built an AI-orchestrated operations system to run it instead.

This is not a hypothetical or classroom project. It's the live system I use to run a two-sided creator/consulting business, built and iterated on through direct collaboration with Claude (Anthropic).

## System Architecture

**Core orchestration:** Claude, connected via MCP (Model Context Protocol) to a set of production tools, acting as an operator across the full content lifecycle — not just a drafting assistant.

**Integrations:**
- **Notion** — primary data backend: structured content calendar and a separate job-search tracker, each with custom schemas (status fields, date logic, relational properties, performance-tracking fields)
- **Slack** — team/collaborator coordination
- **Gmail** — correspondence handling
- **Google Calendar** — scheduling and reminders
- **Google Drive** — asset storage and retrieval

**Data model design decisions:**
- Status fields constrained to a fixed enum (`Not started` / `In progress` / `Done`) with all other context pushed to free-text notes, to keep the database queryable and prevent status-field sprawl
- A recurring, embedded reminder pattern for conditional follow-ups (e.g., "decide fate of long-cut asset once short-cut is marked Done") in the absence of native trigger fields
- Two-step record creation pattern (create shell record → populate properties) after discovering batch creation with full properties failed against the Notion API

## Key System Features

**1. Trial-Reel Experimentation Framework**
A structured test-and-hold methodology for content: new formats are flagged as trial content, tested against retention/reach benchmarks from historical top performers, and diagnosed before a hold/release decision is made — hypothesis → test → metric → decision, not gut instinct. Example: a rage-bait format reel underperformed on retention; root-cause analysis (via benchmarking against a historical high-retention reel) isolated the cause to a slow, low-retention opening 2 seconds rather than the content concept itself, and the piece was held rather than released as-is.

**2. Dual-Brand Architecture**
Two distinct identities — a consumer lifestyle brand and a B2B AI consulting practice — run through the same system with separate positioning, voice constraints, and content pillars, without cross-contamination. Each brand's guardrails (voice rules, monetization category focus, do-not-use language) are encoded as standing operating instructions rather than re-specified each session.

**3. Production Pipeline**
Script → teleprompter formatting → shot list → structured database update → publish → closeout with full asset log (script, overlays, caption, hashtags, delivery notes) written back to the record. Designed so that any piece of finished content is fully reconstructable from its database record alone.

**4. Performance Tracking & Portfolio Discipline**
Every post is tracked against Views, Unique Viewers, Avg Watch Time, Follows-from-Post, and a Performance Tier classification (Hit / Solid / Underperformed), so pattern recognition (what hooks retain, what formats convert) is based on logged data rather than memory.

## Real Outcomes

- **655K** combined monthly views, **5.4%** average engagement rate across three platforms (Instagram, TikTok, Threads)
- Reel performance benchmarking identified a **~4x platform-average watch time** on a Storytime-format piece, informing which formats get prioritized going forward
- Trial-reel diagnostics correctly isolated a hook/retention problem (vs. a content problem) on an underperforming test, preventing a flawed format from being scaled before the fix
- Built out full monetization-readiness infrastructure (media kit, partnership playbook, structured outreach materials) generated and maintained through the same system
- Backfill and audit workflows designed to reconcile months of pre-system content into the structured database via bulk export rather than manual entry

## Tech / Tools

`Claude (Anthropic)` · `Model Context Protocol (MCP)` · `Notion API` · `Slack API` · `Gmail API` · `Google Calendar API` · `Google Drive API`

---

*This system is actively in use, not a demo. Happy to walk through the live database structure, a trial-reel diagnostic in progress, or the reasoning behind any specific design decision.*
