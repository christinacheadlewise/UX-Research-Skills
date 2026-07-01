---
name: start-my-day
description: Morning ritual — synthesises Confluence, Slack, Memory and to-do list into a dated daily note. Run every morning to start the day informed.
---

# /start-my-day

Produces a single dated daily note in `~/Notes/3_Resources/Daily Notes/YYYY-MM-DD.md`.

## Trigger phrases
"start my day", "morning briefing", "start-my-day", "/start-my-day"

## Step-by-step

### 1. Read context sources (do all in parallel)

- Read `~/Notes/AI/Memory.md` — current projects, stakeholders, priorities
- Read yesterday's daily note from `~/Notes/3_Resources/Daily Notes/` if it exists
- Read `~/Notes/00_Inbox/` — list any files sitting there waiting to be triaged
- Fetch live Confluence: User Research hub (page 4125630194) — current In Progress and This Week
- Fetch live Confluence: Christina's to-do list (page 4127656302) — active items
- Search Slack for DMs and @mentions to christina.cheadle@wise.com since yesterday — surface anything that needs a response or contains a task

### 2. Check for meeting notes

- Check `~/Notes/Meet Recordings/` for any new files dropped since yesterday
- If files exist, note them — they'll be processed in end-my-day

### 3. Build the daily note

Create `~/Notes/3_Resources/Daily Notes/YYYY-MM-DD.md` with this structure:

```markdown
# YYYY-MM-DD

## Top Priorities
<!-- Max 3. Work I will actively produce output for today — not meetings, not admin. -->
1.
2.
3.

## Today's Focus
<!-- 2-3 sentences on the thread connecting today's priorities -->

## Active Projects
<!-- One line per active project, current status -->
- **Cuenta Corriente Spain Launch** — [status]
- [other projects]

## To-Do (from Confluence)
<!-- Pull active items from to-do Confluence page, soonest due first -->
| Priority | Task | Due |
|---|---|---|

## Slack — needs response
<!-- Any DMs or mentions that need a reply -->
- 

## Meetings today
<!-- From calendar — fill in manually if no Google MCP -->
- 

## Inbox
<!-- Files sitting in 00_Inbox/ waiting to be triaged -->
- 

## Notes
<!-- Free space -->
```

### 4. Confirm

Tell Christina: "Daily note created for [date]. [N] to-do items active, [N] Slack messages need a response. Top priority today: [P1]."

## Rules
- Top Priorities must be things she will produce output on today — not passive tasks
- Pull to-do items live from Confluence, not from items.json
- If yesterday's note had unfinished priorities, surface them
- Never invent Slack messages — only report what was actually found
- Date verification: run `date "+%Y-%m-%d"` to get today's date before creating the file
