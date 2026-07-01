---
name: end-my-day
description: Evening ritual — triages inbox, processes meeting notes, updates memory, syncs to-do list to Confluence, and pushes a Slack DM summary. Run at end of working day.
---

# /end-my-day

Keeps the vault clean, current, and ready for tomorrow.

## Trigger phrases
"end my day", "wrap up", "end-my-day", "/end-my-day"

## Step-by-step

### 1. Process Meet Recordings

- Check `~/Notes/Meet Recordings/` for any new files
- For each file:
  - Identify who the meeting was with from the filename or content
  - Check if that person has a folder under `~/Notes/2_Areas/z-121s/`
  - If yes: append key points and action items to their existing note
  - If no: create a new note `~/Notes/2_Areas/z-121s/[Name].md` with date, attendees, key points, and action items
  - Move the source file to `~/Notes/4_Archives/`
- Show Christina what was processed and confirm before moving anything

### 2. Triage 00_Inbox/

- List all files in `~/Notes/00_Inbox/`
- For each file, suggest the correct PARA destination:
  - Active project work → `1_Projects/[project]/`
  - Ongoing responsibility → `2_Areas/`
  - Reference material → `3_Resources/`
  - Done / old → `4_Archives/`
- Show the proposed moves and ask for confirmation before executing
- If a file looks like a Confluence clip, note it — offer to fetch the live page content via MCP and replace the snapshot

### 3. Update today's daily note

- Read today's note from `~/Notes/3_Resources/Daily Notes/YYYY-MM-DD.md`
- Add a `## Done today` section at the bottom with a brief summary of what was completed
- Mark any to-do items completed

### 4. Sync to-do list to Confluence

- Read active to-do items from `~/Notes/` context + today's note
- If any items were completed or added today, update the Confluence to-do page (4127656302)
- Apply wipe guard before any Confluence update — read existing page first, abort if new body < 50% of existing

### 5. Update Memory and Session Log

- **Session Log** (`~/Notes/AI/Session Log.md`) — append a new dated entry:
  - Key decisions made today
  - Outputs produced
  - Context that future-Christina should know
- **Memory** (`~/Notes/AI/Memory.md`) — update the snapshot:
  - Refresh current focus and active projects based on today's work
  - Update any stakeholder changes
  - Keep it concise — this is a snapshot, not a diary

### 6. Push Slack DM summary

- Draft a brief end-of-day summary to send to Christina via Slack DM:
  ```
  📋 End of day — [date]
  
  ✅ Done: [key outputs]
  🔄 In progress: [what's carrying over]
  📌 Tomorrow: [top priority]
  ```
- Show the draft and confirm before sending — DMs to Christina never need extra approval, but show it first so she can edit

### 7. Archive old daily notes

- List daily notes in `~/Notes/3_Resources/Daily Notes/` older than 7 days
- Propose moving them to `~/Notes/4_Archives/Daily Notes/`
- Confirm before moving

### 8. Wrap up

Tell Christina: "All done. Memory updated, [N] inbox items triaged, [N] meeting notes processed. First thing tomorrow: [top priority from Memory]."

## Rules

- Never move or delete files without showing the proposed action and getting confirmation
- Never update Confluence without applying wipe guard
- Never send Slack messages without showing the draft first
- Date verification: run `date "+%Y-%m-%d"` before creating or naming any files
- If Meet Recordings/ is empty, skip step 1 silently
- If 00_Inbox/ is empty, skip step 2 and note it
