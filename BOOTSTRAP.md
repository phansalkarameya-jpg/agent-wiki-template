# Bootstrap Prompt

Copy everything below the line into Claude Code to generate your wiki. Customize the sections marked with `<!-- CUSTOMIZE -->` before running.

---

You are doing a one-time bootstrap job. You will populate this repo with a structured knowledge wiki based on my operational history.

## STEP 1 — CONFIGURE

<!-- CUSTOMIZE: Set your data source -->
**Primary source:** Slack channel `YOUR_CHANNEL_ID`
**Date range:** Fetch all messages from `YYYY-MM-DD` onwards
**Source type:** Daily briefings / standup updates / operational notes

<!-- CUSTOMIZE: If not using Slack, replace Step 3 below with your data source.
Examples:
- "Read the last 30 messages from my Apple Notes"
- "Read the Google Doc at [URL]"
- "I'll paste my meeting notes below: [paste]"
-->

## STEP 2 — CREATE FOLDER STRUCTURE

```bash
mkdir -p workstreams people experiments decisions metrics
```

## STEP 3 — FETCH SOURCE MATERIAL

Use the Slack MCP tool to read channel `YOUR_CHANNEL_ID`. Fetch all messages using pagination until you have everything from your start date onwards. These are your source of truth. Do not invent or assume anything not explicitly stated in these messages.

<!-- CUSTOMIZE: If using a different source, replace this step. The key requirement is that you end up with a chronological record of decisions, updates, and context. -->

## STEP 4 — CREATE ARTICLES

For each category below, extract everything relevant from the source history and write structured articles. Use only what appears in the source. Be specific. Include real numbers. Every article must have YAML frontmatter, content body, and a Backlinks section.

### Workstreams
<!-- CUSTOMIZE: List your workstreams. Examples: -->

**workstreams/[name].md** — Include: current status, active campaigns or initiatives, key metrics, blockers, open items. Key people involved.

<!-- Add one entry per workstream. Be specific about what to extract:
workstreams/product-launch.md — Include: launch timeline, feature list, blockers, go/no-go criteria, QA status. Key people: [names].
workstreams/growth.md — Include: channel performance, CAC by channel, active experiments, weekly targets. Key people: [names].
workstreams/partnerships.md — Include: active deals, pipeline status, revenue share terms, open negotiations. Key people: [names].
-->

### People
<!-- CUSTOMIZE: List the people to track. Examples: -->

**people/[name].md** — Include: role, ownership areas, all open items assigned to them across all source messages, delivery patterns (items carried over multiple days), bandwidth flags.

<!-- Add one entry per person:
people/alice.md — Include: role (engineering lead), ownership areas (API, infrastructure), open items, sprint commitments vs delivery.
people/bob.md — Include: role (product manager), ownership areas (roadmap, stakeholder comms), open items, decision patterns.
-->

### Experiments
<!-- CUSTOMIZE: List any active or recent experiments. Examples: -->

**experiments/[name].md** — Include: hypothesis, mechanic, result (with numbers), status (Active / Resolved), next steps.

<!-- Add one entry per experiment:
experiments/pricing-test-q1.md — Include: hypothesis (higher price = same conversion), variant details, conversion numbers, revenue impact, decision made.
experiments/onboarding-flow-v2.md — Include: hypothesis (shorter flow = higher activation), funnel metrics, drop-off rates, status.
-->

### Decisions Log

**decisions/log.md** — Format every entry as:

```
## DD.MM.YYYY

**Decision title**
What was decided, one to three sentences max. Source: [which message/meeting].
```

Extract every clear decision from all source messages in chronological order.

### Metrics

**metrics/definitions.md** — Define every metric mentioned across all source messages. For each: name, definition as used at your company, current benchmark or target.

**metrics/weekly-benchmarks.md** — Extract every number mentioned as a target or threshold. Format as a table: Metric | Target/Threshold | Source | Date mentioned.

## STEP 5 — CREATE INDEX

Write `index.md` as a full catalog of every article created:

```markdown
# Wiki Index

Last updated: [today's date DD.MM.YYYY]
Source: [your source description]

## Workstreams
* [[workstreams/name]] - [one-line summary] | [status]

## People
* [[people/name]] - [one-line summary] | Active

## Experiments
* [[experiments/name]] - [one-line summary] | [status]

## Decisions
* [[decisions/log]] - Chronological log of all decisions

## Metrics
* [[metrics/definitions]] - Metric definitions and benchmarks
* [[metrics/weekly-benchmarks]] - Current targets and thresholds
```

## STEP 6 — CREATE LOG

Write `log.md`:

```markdown
# Wiki Log

## [today's date] bootstrap

Initial wiki created from [source description], covering [date range].
Articles created: [count per folder]. Source messages processed: [count].
```

## STEP 7 — COMMIT AND PUSH

```bash
git add .
git commit -m "bootstrap: initial wiki from [source] [date range]"
git push -u origin main
```

## STEP 8 — FINAL OUTPUT

After pushing, print:
1. GitHub repo URL
2. Article count per folder
3. Any gaps where source data was thin or missing
4. The raw base URL for fetching articles: `https://raw.githubusercontent.com/USERNAME/REPO/main/`
5. The Step 0 line to add to your agent prompts, with the real index.md URL
