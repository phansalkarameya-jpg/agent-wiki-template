# Agent Wiki Schema

## Purpose

This wiki is built for agents, not humans. It compiles operational knowledge from daily updates into structured articles. Agents read this wiki before pulling live data.

## Owner

Ameya Phansalkar, Associate Director of Growth Marketing. Dubai.
Primary source: Slack personal profile / daily notes (U05M607LRFD)
Secondary channels (Slack):
- #team-digital-marketing (C05QB6E9284)
- #marketing-bi (C0780239ABA)
- #team-marketing (CLQRQUTSN)
- #marketing-managers (C02A9FUNC5R)
- #team-crm (C052UAZHF19)
- #eda-daily (C0AQB5S8K60)
- #yana-daily (C0APS3SR163)
- #satpal-ishika-daily (C0AQLET0WDP)

People DMs (read via user ID):
- Baris Kocdur (U2T0ZR6SZ)
- Rupa Antony (U027VCHJ01Y)
- Zeynep Guney (U07NFKYF62H)
- Bilge Hasekioglu (UE977F9FB)
- Yana Bautista (U02ENFZDQHY)
- Ishika Prabhakaran (U09GSMRHA7K)
- Sabhyata Dubey (U06012AB8QJ)
- Satpal Singh (U041HL41GNT)
- Eda Cesmebasi (U045T4NM0JW)

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

## Channels

The eight marketing channels tracked in this wiki:

* `channels/paid-social` — Meta Ads, TikTok Ads, Snapchat
* `channels/paid-search` — Google Ads
* `channels/seo` — Organic search
* `channels/crm-email` — CRM email via CleverTap
* `channels/crm-whatsapp` — CRM WhatsApp via CleverTap
* `channels/crm-push` — Push notifications via CleverTap
* `channels/crm-sms` — SMS via CleverTap
* `channels/affiliate` — Affiliate marketing

## Key metrics

Always include these metrics where they appear in source data:

* **CPA** — Cost per acquisition
* **CPA/LTV** — CPA relative to lifetime value
* **Conversion rate** — % of users who complete a booking
* **Install volume** — Number of app installs
* **CPI** (Cost per install)
* **Bookings** — Total bookings driven
* **YoY growth** — Year-over-year growth %

Attribution tracked via **Adjust**. Analytics via **GA4**.

## Content rules

* Write decisions, not discussions. If something was discussed but not decided, mark it [OPEN].
* Write in present tense for current status, past tense for decisions already made.
* Always include spend, CPA, ROAS, installs, or booking numbers wherever they appear in the source.
* Every person mentioned in an article gets a backlink to their people/ article.
* Every experiment mentioned gets a backlink to its experiments/ article.
* Every channel article should state platform (e.g. Meta Ads, Google Ads) and attribution source (Adjust / GA4).

## Ingest workflow (for updates)

1. Read index.md to understand current wiki state.
2. Read latest Slack messages (last 1-2 days from primary channel).
3. Identify 2-5 articles that need updating based on new decisions, resolved items, or status changes.
4. Update each article. Append to log.md. Update index.md if new articles were created.

## Staleness rule

Articles not updated in 7+ days: add [STALE] tag to their entry in index.md.

## What belongs here

Decisions made (not just discussed). Experiment outcomes with numbers. People: ownership areas, open items, working patterns. Channel status: current state, spend pacing, blockers, next step. Metric definitions and benchmarks.

## What does not belong here

Raw meeting transcripts. Day-by-day operational logs (those stay in Slack). Live metrics that change daily. Ad creative assets. Credentials or secrets.
