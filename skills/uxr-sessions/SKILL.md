---
name: uxr-sessions
description: Push live research session info from Slack into the "This Week" section on the User Research Confluence page. Triggers on "uxr sessions", "push sessions", "update this week", "sync sessions from slack", "add live sessions", or "post session links".
---

# UXR Sessions: Slack → Confluence Session Sync

This skill pulls live session information from Slack and pushes it into the "This Week" panel on the User Research hub page.

## Wipe Guard

Before ANY page update, follow the wipe protection rules in CLAUDE.md. No exceptions.

## Flow

### Step 1: Ask What to Post

> "What's happening this week? I can either:
>
> 1. Pull session info from a Slack message (give me the channel and I'll look)
> 2. You tell me directly — study name, dates/times, and any join links
>
> Which works?"

### Step 2a: From Slack

If Christina points to a Slack channel or message:
1. Use `slack_read_channel` or `slack_read_thread` to find the session info
2. Parse out: study name, dates, times, join links (Zoom/Teams/calendar)
3. Present what you found for confirmation

### Step 2b: From Direct Input

If Christina types it directly, acknowledge and confirm:

> "Got it — [study name] on [dates/times]. Any join links or observer instructions to include?"

### Step 3: Format and Update

Format the "This Week" panel content. Use a note panel:

```html
<div data-type="panel-note"><p>[Content]</p></div>
```

Examples of good content:
- "CES Interviews — Tue-Thu this week. Observer slots available. Join link: [url]"
- "No live sessions this week — analysis sprint."
- "Financial Ecosystems follow-ups — Wed 2pm & Fri 10am. DM Christina to observe."

### Step 4: Apply

1. Read the full User Research hub page (4125630194)
2. Replace ONLY the content between `<h2>This Week</h2>` and the next `<h2>` tag
3. Run wipe guard (compare old vs new full body length)
4. Update the page
5. Confirm: "Done — 'This Week' updated on the User Research page."

### Step 5: Optional Slack Post

> "Want me to also post this in a Slack channel? (e.g., #consumer-onboarding-public)"

If yes, format a brief Slack message:
```
📋 Live research this week:
[Study name] — [dates/times]
Observer link: [url]
DM @Christina Cheadle to join
```

Use `slack_send_message` to post.
