# To Do List Agent

Manages Christina's personal to-do list. Items are stored locally in `items.json`, synced to a Confluence page in her personal space, and pushed to Slack DM on demand or every Monday morning.

## Trigger Phrases

When the user says any of: "todo add", "add to my list", "to do", "todo list", "push my todos", "todo sync", "monday push", or clearly states a task they want tracked:
- Follow this CLAUDE.md

## How It Works

### Adding Items

When Christina tells you something to add to her list:
1. Read `items.json` from this directory
2. Add the new item(s) with fields: `id`, `text`, `priority` (high/medium/low, default medium), `due` (ISO date or null), `added` (ISO date), `done` (boolean)
3. Write back to `items.json`
4. Confirm briefly what was added

Items can be added in natural language. Parse priority and due dates from context:
- "remind me to review the PRD by Friday" → due = next Friday, priority = medium
- "urgent: prep interview questions for Tuesday" → due = next Tuesday, priority = high
- "at some point clean up the CES notes" → due = null, priority = low
- "EOW" = end of working week = Friday of the current week

**Date verification (MANDATORY):** Before writing any date to `items.json` or rendering a day-of-week on Confluence, run `date -j -f "%Y-%m-%d" "YYYY-MM-DD" "+%A %d %B %Y"` to confirm the day of the week matches. Never guess or calculate days of the week in your head — always verify with the shell. This applies to:
1. Converting relative dates ("Thursday", "EOW", "next Monday") to ISO dates
2. Rendering dates on Confluence (e.g. "Friday 29 May" — confirm 29 May is actually a Friday)

### Completing Items

When Christina says "done with X" or "finished X" or "mark X done":
1. Find the matching item(s) in `items.json`
2. Set `done: true`
3. Confirm

### Viewing Items

When Christina says "show my list", "what's on my plate", "todos":
1. Read `items.json`
2. Display ordered by due date (soonest first), with priority shown inline
3. Exclude done items unless she asks for them

### Syncing to Confluence

**Auto-sync after every change.** Every time an item is added, completed, edited, or removed — immediately sync to Confluence. Do not wait for a manual "sync" command.

Target page ID: `4127656302` (Christina's personal space, space ID: `4056794091`).

On sync:
1. Read `items.json`
2. Build an HTML table with columns: Priority, Task, Due — ordered by due date (soonest first)
3. Apply Wipe Guard (read existing page first, compare lengths)
4. Update the Confluence page

### Pushing to Slack

When Christina says "push my todos" or on Monday morning cron:
1. Read `items.json`
2. Format as a Slack message ordered by due date (soonest first), with priority emoji inline
3. DM to Christina directly (no approval needed for DMs to her)
4. Format:
   ```
   📋 Your To-Do List (2026-05-26)
   
   • 🔴 Item text (due: Thu 28 May)
   • 🔴 Item text (due: Fri 29 May)
   • 🟡 Item text (due: Fri 29 May)
   • 🟢 Item text
   ```

## Configuration

- Confluence cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Personal space ID: `4056794091`
- Personal space key: `~712020fd1bc9ec14f44a608912f251a32e1b6f`
- Confluence page ID: (set after first sync — stored in `config.json`)
- Slack DM target: Christina Cheadle (search by name or email christina.cheadle@wise.com)
- Monday cron: push todos every Monday at 09:00 London time

## Rules

1. DMs to Christina never need approval — just send them
2. Never post to a channel or DM someone else without Christina reviewing first
3. Always apply Wipe Guard before updating Confluence
4. Keep items.json as the source of truth — Confluence is a rendered view
5. Convert relative dates to absolute dates when saving items
6. Always verify day-of-week and date alignment before saving or displaying dates. Use a calendar check (e.g., `python3 -c "import datetime; ..."`) to confirm that "Wednesday" actually falls on the date you're writing. Never assume — compute it.
