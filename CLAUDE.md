# Agent Wiki Schema

## Purpose

This wiki is built for agents, not humans. It compiles operational knowledge from daily updates into structured articles. Agents read this wiki before pulling live data.

## Owner

<!-- CUSTOMIZE: Replace with your information -->
Your Name, Your Role, Your Company. Location.
Primary source channel: YOUR_CHANNEL_ID

## Article format

Every article must start with YAML frontmatter:

```yaml
---
summary: one sentence
status: Active | Stale | Resolved | Monitoring
last_updated: DD.MM.YYYY
---
```

Then content. Then a **Backlinks** section at the bottom listing related articles.

## Content rules

* Write decisions, not discussions. If something was discussed but not decided, mark it [OPEN].
* Write in present tense for current status, past tense for decisions already made.
* Include numbers wherever they appear in the source (utilization %, revenue, CPA, etc).
* Every person mentioned in an article gets a backlink to their people/ article.
* Every experiment mentioned gets a backlink to its experiments/ article.

## Ingest workflow (for updates)

1. Read index.md to understand current wiki state.
2. Read latest source messages (last 1-2 days from your primary channel).
3. Identify 2-5 articles that need updating based on new decisions, resolved items, or status changes.
4. Update each article. Append to log.md. Update index.md if new articles were created.

## Staleness rule

Articles not updated in 7+ days: add [STALE] tag to their entry in index.md.

## What belongs here

Decisions made (not just discussed). Experiment outcomes with numbers. People: ownership areas, open items, working patterns. Workstream status: current state, blockers, next step. Metric definitions and benchmarks.

## What does not belong here

Raw meeting transcripts. Day-by-day operational logs (those stay in your source channels). Live metrics that change daily. Credentials or secrets.
