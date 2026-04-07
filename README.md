# Agent Wiki

A structured knowledge base built for AI agents, not humans. Clone this repo, connect your data sources, and run one bootstrap prompt to generate a living wiki from your operational history.

## What this is

Most teams run on Slack, meetings, and scattered docs. Knowledge lives in people's heads and disappears when threads scroll past. This template gives you a framework to compile that knowledge into structured articles that an AI agent can read, reference, and update.

The wiki is designed to be:
- **Read by agents** as context before they do work (briefings, analysis, planning)
- **Updated by agents** as new decisions are made
- **Auditable by humans** when they need to check what was decided and when

## How it works

```
Your data sources (Slack, meetings, notes)
        ↓
  Bootstrap prompt (one-time, run with Claude Code)
        ↓
  Structured wiki (this repo)
        ↓
  Agent reads wiki at Step 0 before pulling live data
        ↓
  Agent flags articles that need updating
        ↓
  Ingest workflow keeps wiki current
```

## Quick start

### 1. Clone this repo

```bash
git clone https://github.com/bkocdur/agent-wiki-template.git my-wiki
cd my-wiki
rm -rf .git && git init
```

### 2. Configure your sources

Edit `CLAUDE.md`:
- Replace the owner block with your name, role, and company
- Replace the Slack channel ID with your briefing or operations channel
- Adjust the article format if needed (the default works for most teams)

### 3. Customize the bootstrap prompt

Open `BOOTSTRAP.md`. This is the prompt you'll paste into Claude Code to generate your wiki. You need to fill in:

- **Your Slack channel ID** — where your daily updates, briefings, or standup notes live
- **Date range** — how far back to go
- **Workstreams** — what your team works on (projects, verticals, products)
- **People** — who to track (direct reports, key stakeholders, cross-functional partners)
- **Experiments** — any tests, pilots, or A/B experiments you're running
- **Metrics** — what numbers matter to your team

The bootstrap prompt will read your source messages, extract decisions and context, and write every article.

### 4. Run the bootstrap

Open Claude Code in your wiki directory and paste the contents of `BOOTSTRAP.md`. The agent will:

1. Fetch your source messages (Slack, or any connected MCP tool)
2. Create all articles with YAML frontmatter, content, and backlinks
3. Build the index and decision log
4. Commit and push to GitHub

### 5. Connect to your workflows

Add this as Step 0 in any agent prompt that needs operational context:

```
Step 0 — Wiki context: Fetch https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_WIKI_REPO/main/index.md
and read it. For any workstream, person, or experiment relevant to today's task,
fetch their article from the same base URL. Use wiki context to identify what has
changed vs. last known state.
```

## Folder structure

```
agent-wiki-template/
├── CLAUDE.md              # Agent schema — rules for reading and writing articles
├── BOOTSTRAP.md           # One-time bootstrap prompt — customize and run
├── index.md               # Article catalog with status tags (auto-generated)
├── log.md                 # Update log (auto-generated)
├── workstreams/           # What your team works on
├── people/                # Who does what, open items, delivery patterns
├── experiments/           # Tests and pilots with hypotheses and results
├── decisions/             # Chronological decision log
├── metrics/               # Definitions and benchmarks
└── templates/             # Example articles to reference
    ├── workstream.md
    ├── person.md
    ├── experiment.md
    └── metric.md
```

## Article format

Every article follows the same structure:

```markdown
---
summary: one sentence
status: Active | Stale | Resolved | Monitoring
last_updated: DD.MM.YYYY
---

# Title

Content body — decisions, numbers, current state.

## Backlinks

- [[related/article]]
```

## Keeping it current

### Manual updates
Edit articles directly when decisions are made. Update `index.md` if you add new articles. Append to `log.md`.

### Agent-powered updates (recommended)
The ingest workflow in `CLAUDE.md` tells agents how to update the wiki:

1. Read `index.md` to understand current state
2. Read latest source messages (last 1-2 days)
3. Identify 2-5 articles that need updating
4. Update each article, append to `log.md`, update `index.md` if new articles created

You can run this manually ("update the wiki from today's briefings") or automate it on a schedule.

## Staleness rule

Articles not updated in 7+ days get a `[STALE]` tag in `index.md`. This surfaces when context is aging and may no longer be accurate.

## Content rules

- **Write decisions, not discussions.** If something was discussed but not decided, mark it `[OPEN]`.
- **Write in present tense** for current status, past tense for decisions already made.
- **Include numbers** wherever they appear in the source (percentages, dollar amounts, KPIs).
- **Backlink everything.** Every person mentioned gets a link to their `people/` article. Every experiment gets a link to its `experiments/` article.

## What belongs here

- Decisions made (not just discussed)
- Experiment outcomes with numbers
- People: ownership areas, open items, working patterns
- Workstream status: current state, blockers, next step
- Metric definitions and benchmarks

## What does not belong here

- Raw meeting transcripts
- Day-by-day operational logs (those stay in Slack)
- Live metrics that change daily
- Credentials or secrets

## Data sources

This template is source-agnostic. The bootstrap prompt uses Slack via MCP, but you can adapt it for any source:

| Source | How to connect |
|---|---|
| Slack | MCP Slack tool (used in bootstrap prompt) |
| Meeting notes | Granola, Otter, Fireflies — paste transcripts or connect via MCP |
| Apple Notes | MCP Apple Notes tool |
| Google Docs | MCP Google Drive tool |
| Email | MCP Gmail tool |
| Notion | MCP Notion tool |
| Linear / Asana | MCP project management tools |
| Manual | Paste raw text into the bootstrap prompt |

The key is that you have a chronological record of what happened. The format doesn't matter — the bootstrap prompt will extract the structure.

## FAQ

**How is this different from a regular wiki?**
Regular wikis are written for humans and go stale. This wiki is written for agents — the format is optimized for machine reading, and the staleness rule forces updates. Humans can read it too, but it's not the primary audience.

**Do I need Slack?**
No. Slack is just the most common source. Any chronological record of decisions works — meeting notes, email threads, daily standups, even a running Google Doc.

**How many articles should I start with?**
Start with 5-10 workstreams, your direct reports as people articles, and any active experiments. You can always add more. The bootstrap prompt will suggest articles based on what it finds in your source.

**Can multiple people maintain the wiki?**
Yes. It's a git repo. Multiple people can update articles and the merge process handles conflicts. The `log.md` provides an audit trail.

**How do I handle sensitive information?**
Keep the repo private. Don't include credentials, salary information, or anything you wouldn't put in a shared Google Doc. The wiki is for operational knowledge, not secrets.

## Credits

Created by [Baris Kocdur](https://github.com/bkocdur). Built with Claude Code.
