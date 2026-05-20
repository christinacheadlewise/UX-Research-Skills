---
name: ces-setup
description: "Monthly CES Rolling Research kickoff. Two passes: (1) Monday before sessions — create recruit grid, post Slack question to squad; (2) Day before sessions — collect Google Calendar links, post to Slack + Confluence. Use when the user says 'ces setup', 'set up ces', 'ces this month', 'ces kickoff', or 'monthly ces'."
---

# CES Setup: Monthly Rolling Research Kickoff

CES Rolling Research runs monthly. Default schedule: last Friday of the month, 4 sessions at 2:00 / 2:30 / 3:00 / 3:30 (30 min each). Recruitment comes from in-app CES survey respondents.

## Two Passes

This skill runs twice per month:

### Pass 1: 4 Days Before Sessions (Kickoff)

Triggers when Christina says "ces setup" 4 days before sessions (e.g., Monday if sessions are Friday, Friday if sessions shift to Tuesday).

#### Step 1: Confirm Schedule

> "CES this month — last Friday default is [date]. Four slots: 2:00, 2:30, 3:00, 3:30. That still right, or different this time?"

If different, collect the actual date and times.

#### Step 2: Create Recruitment Grid

Generate a CSV: `ces-[month]-[year]-recruit.csv`

```csv
Slot,Time,Name,Email,Consent Sent,Consent Signed,Status,Paid,Notes
1,14:00,,,No,No,Awaiting Response,No,
2,14:30,,,No,No,Awaiting Response,No,
3,15:00,,,No,No,Awaiting Response,No,
4,15:30,,,No,No,Awaiting Response,No,
```

**Status values:** Awaiting Response / Confirmed / Cancelled / No Show / Completed

Save to working directory. Confirm: "Grid saved to `[filename]`."

#### Step 3: Post Slack Question

Post to #onboarding-squad-public:

```
🔬 **CES Interviews — [Month]**

Rolling research sessions are this [day], [date]. I've got 4 slots with customers who recently went through onboarding.

Standard intro + wrap stays the same. What do you want me to dig into this month? Drop your questions/topics in the thread 👇

(Last month we explored: [topic from previous month if known])
```

Use `slack_send_message` to post. Confirm with link.

#### Step 4: Wrap

> "Kickoff done. Grid's ready, Slack question's posted. Come back day-before to push session links, or say 'ces setup' again when you've got them."

---

## Timing

- **Kickoff (Pass 1):** 4 days before sessions. If sessions are Friday → kickoff Monday. If sessions shift to Tuesday → kickoff Friday.
- **Links (Pass 2):** Day before sessions.

---

### Pass 2: Day Before Sessions (Links)

Triggers when Christina says "ces setup" again (or "push ces links", "ces links") closer to the session date.

#### Step 1: Collect Links

> "Session links time. Give me the Google Calendar links for each slot (or one link if it's a single event with all four)."

Collect the join/calendar links from Christina.

#### Step 2: Post to Slack

Post to #onboarding-squad-public:

```
📅 **CES Interviews — Tomorrow ([date])**

Come observe! Here are the session links:

• 2:00pm — [link]
• 2:30pm — [link]
• 3:00pm — [link]
• 3:30pm — [link]

DM me if you want context on what we're exploring this month. No prep needed to observe.
```

#### Step 3: Push to Confluence "This Week"

Update the "This Week" panel on the User Research hub page (4125630194):

```html
<div data-type="panel-note"><p><strong>CES Interviews — [Day] [Date]</strong></p><p>2:00 / 2:30 / 3:00 / 3:30 — <a href="[link]">Join to observe</a></p><p>Topic this month: [topic from Slack thread]</p></div>
```

Follow wipe guard rules (read page first, check content length before updating).

Confirm: "Slack posted, Confluence updated."

---

## Confluence Details

- Cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Hub page: `4125630194`
- Space ID: `1097630102`

## Slack Channel

- #onboarding-squad-public (search for channel ID via `slack_search_channels` on first use, then remember it)
