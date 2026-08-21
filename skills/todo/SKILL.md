---
name: todo
description: Manage Christina's personal to-do list — add, complete, edit, view, and push to Slack. Use when she says "todo add", "add to my list", "to do", "todo list", "show my list", "what's on my plate", "push my todos", "mark X done", "finished X", or clearly states a task she wants tracked. Source of truth is this skill's local items.json — no Confluence.
---

# To-Do List Skill

Manages Christina's personal to-do list. **`items.json` in this skill folder is the single source of truth.** There is no Confluence sync — the old Confluence page has been retired. The list can be pushed to her Slack DM on demand ("push my todos"). There is no scheduled cron.

Data file: `skills/todo/items.json` (relative to the repo root, `~/dev/uxr-hub`).

## Item schema

Each item is an object with:
- `id` — short kebab-case slug
- `text` — the task, in natural language
- `priority` — `high` | `medium` | `low` (default `medium`)
- `due` — ISO date `YYYY-MM-DD`, or `null`
- `added` — ISO date the item was created
- `done` — boolean
- `completed` — ISO date (only present when `done: true`)

## Date verification (MANDATORY)

Before writing any date to `items.json` or rendering a day-of-week for display, run:

```
date -j -f "%Y-%m-%d" "YYYY-MM-DD" "+%A %d %B %Y"
```

to confirm the weekday matches. Never guess or compute weekdays in your head. This applies to:
1. Converting relative dates ("Thursday", "EOW", "next Monday") to ISO dates
2. Rendering a weekday label back to Christina (e.g. "Monday 24 August")

Relative-date shorthands: "EOW" = end of working week = Friday of the current week; "next Friday" = the Friday of next week.

## Operations

### Add
1. Read `items.json`.
2. Parse the task from natural language — infer `priority` and `due` from context (e.g. "urgent: prep for Tuesday" → high, next Tuesday; "at some point clean up notes" → low, null).
3. Verify any date with the shell command above.
4. Append the new item and write `items.json`.
5. Confirm briefly what was added.

### Complete
1. Read `items.json`.
2. Find the matching item(s), set `done: true` and `completed` to today's date.
3. Write `items.json`.
4. Confirm.

### Edit (e.g. change due date or priority)
1. Read `items.json`.
2. Verify any new date with the shell command.
3. Update the field(s) and write `items.json`.
4. Confirm.

### View
1. Read `items.json`.
2. Show active items (`done: false`) ordered by due date, soonest first, with priority inline. Flag overdue items against today's date.
3. Only show completed items if she asks for them.

### Push to Slack
When she says "push my todos" (on demand only — no scheduled cron):
1. Read `items.json`.
2. Format active items ordered by due date (soonest first), priority emoji inline (🔴 high / 🟡 medium / 🟢 low).
3. DM Christina directly (christina.cheadle@wise.com) — no approval needed for DMs to her.

Format:
```
📋 Your To-Do List (YYYY-MM-DD)

• 🔴 Item text (due: Mon 24 Aug)
• 🟡 Item text (due: Fri 28 Aug)
• 🟢 Item text
```

## Rules

1. `items.json` is the source of truth. There is no Confluence page — never write to Confluence for the to-do list.
2. DMs to Christina never need approval; never post to a channel or DM anyone else without her review.
3. Always verify day-of-week and date alignment before saving or displaying dates.
4. Convert relative dates to absolute ISO dates when saving.
