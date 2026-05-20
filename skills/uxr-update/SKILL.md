---
name: uxr-update
description: Weekly Monday update for User Research Confluence pages. Walks Christina through what's changed, updates In Progress / Recently Completed / Active Studies tables, and syncs the Research Repository. Triggers on "uxr update", "weekly update", "monday update", or the Monday morning cron.
---

# UXR Update: Weekly Confluence Refresh

This skill runs every Monday morning (via cron) or on-demand. It walks Christina through updating her User Research hub pages so they stay fresh.

## Wipe Guard

Before ANY page update, follow the wipe protection rules in CLAUDE.md. No exceptions.

## Flow

### Step 1: Greet and Gather

Start with a brief check-in:

> "Mornin' — time for the weekly research page refresh. Let me pull up what's currently on the pages and we'll walk through what needs updating."

Then read the current state of:
- User Research hub (4125630194) — get "In Progress" and "Recently Completed" tables
- Active Studies (4125182953) — get the current table

Present a summary:

> "Here's what's live right now:
>
> **In Progress:**
> - [list current items]
>
> **Recently Completed:**
> - [list current items]
>
> Anything to move, add, or remove?"

### Step 2: Collect Updates

Ask Christina ONE question at a time:

1. "Any studies to move from In Progress → Recently Completed?"
2. "Anything new to add to In Progress?"
3. "Any changes to the 'This Week' panel? (Live sessions, out of office, etc.)"
4. "Anything else to update?"

If she says "no" to all, skip to Step 4.

### Step 3: Apply Updates

For each change Christina confirms:
1. Read the current page content (wipe guard)
2. Modify only the relevant section
3. Update the page
4. Confirm: "Done — [description of change]."

Keep the tables in sync:
- If something moves to Recently Completed on the hub, also update the Research Repository table if it's a completed study
- If something moves to In Progress on the hub, also update Active Studies

### Step 4: Schedule Next Week's Slack Reminder

Determine the next update day:
1. Start with next Monday at 10:00am local
2. Check if that Monday is a UK bank holiday. UK bank holidays to check:
   - New Year's Day (1 Jan, or next Mon if weekend)
   - Good Friday / Easter Monday (variable)
   - Early May bank holiday (first Mon in May)
   - Spring bank holiday (last Mon in May)
   - Summer bank holiday (last Mon in Aug)
   - Christmas Day / Boxing Day (25-26 Dec, or substitute Mon/Tue if weekend)
3. If it IS a bank holiday, shift to Tuesday at 10:00am instead

Schedule a Slack DM to Christina (channel: `U0AK82NPKJA`) with:

> "👋 Monday research page refresh! Open Claude Code and say `uxr update` to walk through your weekly Confluence updates (In Progress, Recently Completed, This Week). If the cron fired already, ignore this."

Use `slack_schedule_message` with `post_at` set to the chosen day at 10:00am as a Unix timestamp. Confirm which day was scheduled: "Next reminder set for [Monday/Tuesday] [date]."

### Step 5: Wrap Up

> "All set for the week. Pages are fresh. Next Monday's Slack reminder is scheduled. Holler 'uxr sessions' if you need to push live session links later."

## Table Formats

### In Progress table (hub page + Active Studies page)
```html
<table data-width="760">
<thead><tr><th><p>Study</p></th><th><p>Status</p></th><th><p>Details</p></th></tr></thead>
<tbody><tr>
<td><p>[Study name]</p></td>
<td><p><span data-type="status" data-color="[blue|yellow|green]">[Status text]</span></p></td>
<td><p>[One-line description]</p></td>
</tr></tbody>
</table>
```

### Recently Completed table (hub page + Research Repository page)
```html
<table data-width="760">
<thead><tr><th><p>Study</p></th><th><p>Date</p></th><th><p>Resources</p></th></tr></thead>
<tbody><tr>
<td><p><strong>[Title]</strong></p><p>[2-3 sentence summary]</p></td>
<td><p>[Month Year]</p></td>
<td><p>[Links to Confluence page, slide deck, etc.]</p></td>
</tr></tbody>
</table>
```

## Status Lozenge Colors

- Blue = Not started / scheduled (e.g., "Starting w/c 26 May")
- Yellow = In progress
- Green = Complete / wrapping up
- Red = Blocked
- Purple = On hold
