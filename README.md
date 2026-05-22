# UX Research Skills

A collection of AI-powered research agents built with [Claude Code](https://claude.ai/code). These automate the repetitive parts of qualitative UX research — from transcript processing to Confluence publishing to task management.

**[View the site](https://christinacheadlewise.github.io/UX-Research-Skills/)**

## Agents

### UXR Hub — Confluence Page Manager

Manages User Research Confluence pages: weekly updates, session syncing, study artifacts, and the monthly Customer Effort Score (CES) pipeline.

| Skill | What it does |
|-------|-------------|
| `uxr plan` | Writes a research plan and publishes to Confluence |
| `uxr grid` | Creates a recruitment and screening grid |
| `uxr notes` | Builds a session notes and observation template |
| `uxr guide` | Writes a discussion guide |
| `uxr analysis` | Codes data, surfaces themes, challenges assumptions |
| `uxr slack` | Generates an executive summary for Slack and Confluence |
| `uxr update` | Monday refresh — syncs In Progress, Recently Completed, repository |
| `uxr sessions` | Pushes live session info from Slack into Confluence |

**CES sub-skills (monthly rolling research):**

| Skill | What it does |
|-------|-------------|
| `ces setup` | Scaffolds the month's CES round |
| `ces guide` | Updates the discussion guide's middle questions |
| `ces notes` | Sets up the session notes document |
| `ces summary` | Writes up findings from transcripts |

### To-Do Agent

Personal task tracker with natural language input. Parses priority and due dates from conversational commands, auto-syncs to a Confluence page, and sends a formatted Slack DM every Monday morning.

## Safeguards

These apply globally across all agents:

1. **Wipe Guard** — Any Confluence update that would reduce page content by more than 50% is automatically aborted. No exceptions without explicit override.
2. **Draft Before Post** — Direct messages are sent immediately. Channel posts or messages to others always require review first.
3. **Extreme Clarity** — All outputs follow 8 rules: brevity, no acronyms, numbered lists, absolute and relative metrics, deep links, explicit units, state changes, proof-read.

## Trained Personality

Claude is configured as a research assistant with specific interaction rules:

- Speaks in a southern American dialect — warm and direct
- No sycophancy — never fawns or says "great question"
- Challenges assumptions — pushes back, asks "why", questions undercooked ideas
- Never halluccinates — says "I don't know" rather than inventing facts
- One question at a time — no dumping multiple questions in a single response

## Structure

```
skills/           UXR Hub skills (plan, grid, notes, guide, analysis, slack, update, sessions)
CES/              CES monthly pipeline skills (setup, guide, notes, summary)
todo-agent/       To-do list agent (items.json, config, CLAUDE.md)
docs/             GitHub Pages site
interaction-style.md   Personality and communication rules
CLAUDE.md         Root agent router
```

## How it works

1. Type a natural language trigger in Claude Code (e.g. "uxr plan", "ces setup", "todo add")
2. The router reads intent and loads the correct agent and skill instructions
3. Claude follows the skill's SKILL.md exactly, using MCP tools for Confluence, Slack, and Jira
4. Safeguards (wipe guard, draft review, clarity rules) apply before any external action

## Built with

- [Claude Code](https://claude.ai/code) (CLI agent)
- Anthropic Claude (Opus 4.7)
- MCP servers: Atlassian (Confluence, Jira), Slack
- GitHub Pages for hosting

---

Built by Christina Cheadle, Staff UX Researcher at Wise.
