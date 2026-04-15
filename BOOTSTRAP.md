# Bootstrap Prompt

Copy everything below the line into Claude Code to generate your wiki from your Slack history.
Customize the sections marked with `<!-- CUSTOMIZE -->` before running.

---

You are doing a one-time bootstrap job. You will populate this growth marketing wiki with structured knowledge based on Slack history.

**Owner:** Ameya Phansalkar, Associate Director of Growth Marketing, Dubai.

## STEP 1 — CONFIGURE

<!-- CUSTOMIZE: Set your Slack channel ID and date range -->
**Primary source:** Slack channel `YOUR_CHANNEL_ID`
**Date range:** Fetch all messages from `YYYY-MM-DD` onwards
**Source type:** Daily marketing updates, campaign performance, decisions, experiments

## STEP 2 — CREATE FOLDER STRUCTURE

```bash
mkdir -p channels people experiments decisions metrics
```

## STEP 3 — FETCH SOURCE MATERIAL

Use the Slack MCP tool to read channel `YOUR_CHANNEL_ID`. Fetch all messages using pagination until you have everything from your start date onwards. These are your source of truth.

Do not invent or assume anything not explicitly stated in the messages. If a metric is mentioned without a value, note it as [OPEN].

## STEP 4 — CREATE ARTICLES

### Channels

Create one article per channel below. For each, extract: current performance status, CPA, CPI, installs, bookings, conversion rate, YoY growth, active campaigns, blockers, open items, and owners. Include the platform and attribution source.

**channels/paid-social.md** — Meta Ads, TikTok Ads, Snapchat. Include: spend pacing, CPA by platform, install volume, booking numbers, active creative tests, audience changes, blockers.

**channels/paid-search.md** — Google Ads. Include: spend pacing, CPA, Quality Score trends, keyword changes, campaign structure updates, blockers.

**channels/seo.md** — Organic search. Include: traffic trends, ranking changes, content initiatives, technical issues, YoY growth.

**channels/crm-email.md** — CRM email via CleverTap. Include: open rate, CTR, conversion rate, active journeys, A/B tests, segment changes, blockers.

**channels/crm-whatsapp.md** — CRM WhatsApp via CleverTap. Include: delivery rate, open rate, CTR, conversion rate, active campaigns, opt-out trends, blockers.

**channels/crm-push.md** — Push notifications via CleverTap. Include: delivery rate, open rate, CTR, conversion rate, active journeys, blockers.

**channels/crm-sms.md** — CRM SMS via CleverTap. Include: delivery rate, CTR, conversion rate, active campaigns, blockers.

**channels/affiliate.md** — Affiliate marketing. Include: active partners, commission structure, attributed installs and bookings, CPA, payout status, open items.

### People

**people/[name].md** — For each person mentioned in the source: role, channels they own, open items assigned to them, delivery patterns, bandwidth flags.

Be sure to create **people/ameya-phansalkar.md** as the primary owner article.

### Experiments

**experiments/[name].md** — For each A/B test, creative test, audience test, or channel experiment mentioned. Include: channel, platform, hypothesis, mechanic, results with numbers (CPA, CPI, installs, bookings, conversion rate), status, next step.

### Decisions Log

**decisions/log.md** — Format every entry as:

```
## DD.MM.YYYY

**Decision title**
What was decided, one to three sentences max. Channel affected. Source: [which message].
```

Extract every clear decision from all source messages in chronological order.

### Metrics

**metrics/definitions.md** — Define each metric as used at this company. For each: name, definition, how it's calculated (formula + data source — Adjust or GA4), current benchmark or target.

Metrics to define: CPA, CPA/LTV, Conversion Rate, Install Volume, CPI, Bookings, YoY Growth.

**metrics/weekly-benchmarks.md** — Extract every number mentioned as a target or threshold. Format as a table:

| Metric | Channel | Target | Actual | Source | Date |
|---|---|---|---|---|---|

## STEP 5 — CREATE INDEX

Write `index.md` as a full catalog of every article created:

```markdown
# Wiki Index

Last updated: [today's date DD.MM.YYYY]
Source: Slack channel [YOUR_CHANNEL_ID], [date range]

## Channels
* [[channels/paid-social]] - [one-line status] | Active
* [[channels/paid-search]] - [one-line status] | Active
* [[channels/seo]] - [one-line status] | Active
* [[channels/crm-email]] - [one-line status] | Active
* [[channels/crm-whatsapp]] - [one-line status] | Active
* [[channels/crm-push]] - [one-line status] | Active
* [[channels/crm-sms]] - [one-line status] | Active
* [[channels/affiliate]] - [one-line status] | Active

## People
* [[people/name]] - [role summary] | Active

## Experiments
* [[experiments/name]] - [hypothesis summary] | [status]

## Decisions
* [[decisions/log]] - Chronological log of all decisions

## Metrics
* [[metrics/definitions]] - CPA, CPA/LTV, CVR, Installs, CPI, Bookings, YoY Growth
* [[metrics/weekly-benchmarks]] - Current targets and thresholds by channel
```

## STEP 6 — CREATE LOG

Write `log.md`:

```markdown
# Wiki Log

## [today's date] bootstrap

Initial wiki created from Slack channel [YOUR_CHANNEL_ID], covering [date range].
Articles created: [count per folder]. Source messages processed: [count].
```

## STEP 7 — COMMIT AND PUSH

```bash
git add .
git commit -m "bootstrap: initial wiki from Slack [date range]"
git push origin main
```

## STEP 8 — FINAL OUTPUT

After pushing, print:
1. GitHub repo URL: `https://github.com/phansalkarameya-jpg/agent-wiki-template`
2. Article count per folder
3. Any gaps where source data was thin or missing
4. The Step 0 line to add to your agent prompts:

> Before taking any action, read the wiki index at `https://raw.githubusercontent.com/phansalkarameya-jpg/agent-wiki-template/main/index.md` and fetch any articles relevant to this task.
