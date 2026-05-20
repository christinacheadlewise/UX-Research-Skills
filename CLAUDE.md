# UXR Hub — Confluence Page Manager

This agent manages Christina's User Research Confluence pages (space C20). It handles weekly updates, wipe protection, and Slack-to-Confluence session syncing.

## Available Skills

When the user says "uxr plan", "new research plan", "write a research plan", "plan a study", or "start a new study":
- Read and follow the instructions in `skills/uxr-plan/SKILL.md`
- Reference files are in `skills/uxr-plan/references/`

When the user says "uxr grid", "recruitment grid", "make a recruit grid", "participant tracker", or "screening grid":
- Read and follow the instructions in `skills/uxr-grid/SKILL.md`

When the user says "uxr notes", "notes grid", "analysis grid", "session notes template", "make a notes doc", or "observation grid":
- Read and follow the instructions in `skills/uxr-notes/SKILL.md`

When the user says "uxr guide", "write a discussion guide", "new discussion guide", "create a guide", or "build a moderator guide":
- Read and follow the instructions in `skills/uxr-guide/SKILL.md`
- Reference files are in `skills/uxr-guide/references/`

When the user says "uxr analysis", "analyse this", "code this", "run analysis", "what are the themes", "challenge me", "devil's advocate", or "push back on this":
- Read and follow the instructions in `skills/uxr-analysis/SKILL.md`

When the user says "ces setup", "set up ces", "ces this month", "ces kickoff", "monthly ces", "push ces links", or "ces links":
- Read and follow the instructions in `skills/ces-setup/SKILL.md`

When the user says "ces guide", "update ces guide", "tweak the ces questions", or "ces middle questions":
- Read and follow the instructions in `skills/ces-guide/SKILL.md`

When the user says "ces notes", "ces notes doc", or "set up ces notes":
- Read and follow the instructions in `skills/ces-notes/SKILL.md`

When the user says "ces summary", "summarise ces", "ces write-up", "ces transcripts", or "write up ces":
- Read and follow the instructions in `skills/ces-summary/SKILL.md`

When the user says "uxr slack", "write a slack summary", "slack post", "share this research", "write up for slack", or "summarise this deck for slack":
- Read and follow the instructions in `skills/uxr-slack/SKILL.md`

When the user says "uxr update", "weekly update", "update confluence", "monday update", or this fires from a Monday cron:
- Read and follow the instructions in `skills/uxr-update/SKILL.md`
- Reference files are in `skills/uxr-update/references/`

When the user says "uxr sessions", "push sessions", "update this week", "sync sessions from slack", or "add live sessions":
- Read and follow the instructions in `skills/uxr-sessions/SKILL.md`
- Reference files are in `skills/uxr-sessions/references/`

## Wipe Protection

**CRITICAL — applies to ALL Confluence updates made by this agent:**

Before ANY call to `updateConfluencePage`, the agent MUST:
1. Read the current page content first via `getConfluencePage`
2. Compare the length of the existing body to the new body
3. If the new body is less than 50% of the existing body length, ABORT and warn Christina: "Wipe guard triggered — the update would reduce page content by more than 50%. Showing diff for review."
4. Never pass empty or placeholder body content when using parentId to move pages
5. Never use updateConfluencePage with body="" or body="<p></p>" on a page that has existing content

This rule has NO exceptions. A previous incident wiped 6 pages by passing empty body content.

## Page Registry

These are the pages this agent manages:

| Page | ID | Purpose |
|------|-----|---------|
| User Research (hub) | 4125630194 | Main landing page — This Week, In Progress, Recently Completed |
| Active Studies | 4125182953 | Table of current studies with status |
| Research Repository | 4125116067 | Full archive table, grouped by theme |
| Financial Ecosystems | 4075623625 | Research plan (child: Final Reports) |

Cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
Space ID: `1097630102`
Christina's Account ID: `712020:fd1bc9ec-14f4-4a60-8912-f251a32e1b6f`

## Catch-All

If the user says something related to the UXR hub pages but it doesn't clearly map to a skill:

> "I can help with a few things:
>
> - **uxr plan** — Write a new research plan and publish it to Confluence
> - **uxr guide** — Write a discussion guide (pulls from your research plan if one exists)
> - **uxr update** — Monday refresh: review what's changed, update In Progress/Recently Completed, and sync the repository
> - **uxr sessions** — Push live session info from Slack into the 'This Week' section on Confluence
>
> Which one are you after?"
