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

#### Step 2: Create Monthly Confluence Page

Create a child page under **CES Rolling Research** (4125091326):
- Title: `[Mon] '[YY] - CES Rolling Research` (e.g., "May '26 - CES Rolling Research")
- Content: placeholder for summary + sessions table + focus topic
- This page becomes the parent for the discussion guide and eventual summary

Store the new page ID — all other CES pages this month (discussion guide, summary) are children of this page.

#### Step 3: Create Recruitment Grid (Google Sheet)

Create a Google Sheet via Credal (`create_a_spreadsheet`) titled: `CES [Month] [Year] — Recruitment`

Sheet structure (1 sheet called "Recruitment", frozen header row, 11 columns):

| Slot | Time | User ID | Email | Pseudonym | Score | Drop-Off Point | Comments | Country | Consent Form | Status |
|------|------|---------|-------|-----------|-------|----------------|----------|---------|--------------|--------|
| 1 | 14:00 | | | | | | | | Not Sent | Upcoming |
| 2 | 14:30 | | | | | | | | Not Sent | Upcoming |
| 3 | 15:00 | | | | | | | | Not Sent | Upcoming |
| 4 | 15:30 | | | | | | | | Not Sent | Upcoming |

After creating the sheet, use `update_a_spreadsheet` to:
1. Write the header row and 4 data rows
2. Add data validation on **Consent Form** column (Not Sent / Sent / Signed)
3. Add data validation on **Status** column (Upcoming / Paid / Cancelled / No Show)

**Consent Form values:** Not Sent / Sent / Signed
**Status values:** Upcoming / Paid / Cancelled / No Show

Confirm: "Recruitment grid created: [Google Sheet link]"

#### Step 4: Draft Slack Question

Draft the message and send it to Christina as a DM (U0AK82NPKJA) for review BEFORE posting to any channel:

```
🔬 **CES Rolling Research Sessions — [Month]**

I've got 4 slots this [day], [date] with customers who recently went through onboarding.

• 2:00pm
• 2:30pm
• 3:00pm
• 3:30pm

I've added these to the Consumer Onboarding calendar. Viewing links will be generated the day before.

What do you want me to dig into this month? Drop your questions/topics in the thread 👇
```

> "Sent you a draft in Slack DMs — check it and tell me what to tweak or say 'push' to post."

**NEVER post to a channel without Christina's explicit approval.** Iterate on the draft until she says to push it.

When approved, ask which channel to post to (default: #onboarding-squad-public / C04KLT41GN5, but she may want #consumer-onboarding-private / G5EAY3A2K instead). Then post and confirm with link.

#### Step 5: Schedule Links Reminder

Schedule a Slack DM to Christina (U0AK82NPKJA) for the working day before sessions at 10:00 AM:
- If sessions are Friday → remind Thursday
- If sessions are Tuesday → remind Friday (skip bank holiday Monday)
- Message: "👋 Reminder: CES sessions are tomorrow. Time to push the calendar links — say `ces links` when you've got them and I'll post to #current-account-onboarding + update Confluence."

#### Step 6: Wrap

> "Kickoff done. Grid's ready, Slack question's posted. You'll get a reminder on [day] to send me the calendar links."

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

Post to #onboarding-squad-public (C04KLT41GN5):

```
📅 **CES Interviews — Tomorrow ([day] [date])**

Come observe! Here are the session links for this month's Customer Effort Score (CES) interviews:

• **[time]** — Rated [score]/7 | Drop-off: [step] | [flag] [country] — [Join to observe](link)
• **[time]** — Rated [score]/7 | Drop-off: [step] | [flag] [country] — [Join to observe](link)
• **[time]** — TBD — link TBD
...

_(Ratings are how each participant scored their onboarding experience on a 1–7 ease scale, where 1 = very difficult)_

All sessions are on the [Consumer Onboarding calendar](https://calendar.google.com/calendar/u/0?cid=dHJhbnNmZXJ3aXNlLmNvbV9ub2g1dTc2ajN1bzIzZGxrNWY4dnUwanNxa0Bncm91cC5jYWxlbmRhci5nb29nbGUuY29t). Check back here for updated links and additional participant details.

🧵 Use this thread to leave any comments or questions during the interviews — if there's something you'd like me to ask, drop it here and I'll work it in!

💡 **What is this?** Every month I run short interviews with customers who recently completed our CES survey about their onboarding experience. It's a chance to hear directly what went well and what didn't.
```

Follow up in thread: _I'll update this thread once remaining participants and links are confirmed._

Links come from UserTesting session URLs (Christina provides these). Include participant drop-off point and country (from Snowflake `INT_FEATURE_FEEDBACK` table) for each confirmed slot. Leave unconfirmed slots as "TBD — link TBD".

#### Step 3: Push to Confluence "This Week"

Update the "This Week" panel on the User Research hub page (4125630194):

```html
<div data-type="panel-note"><p><strong>CES Interviews — [Day] [Date]</strong></p><p>2:00 / 2:30 / 3:00 / 3:30 — <a href="[link]">Join to observe</a></p><p>Topic this month: [topic from Slack thread]</p></div>
```

Follow wipe guard rules (read page first, check content length before updating).

Confirm: "Slack posted, Confluence updated."

---

## Output Standards (Extreme Clarity)

1. **Explicit units.** Always state full dates ("Tuesday 26 May 2026"), times with format ("14:00"), and durations ("30-minute sessions").
2. **No unexpanded acronyms.** "Customer Effort Score (CES)" on first use in Slack posts. Then "CES" is fine.
3. **Deep link.** Calendar links and Confluence links must be clickable — never describe where to find them.
4. **Proof-read.** Before sending any Slack draft, re-read for ambiguity. If a sentence could be read two ways, rewrite it.

## Confluence Details

- Cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Hub page: `4125630194`
- Space ID: `1097630102`

## Slack Channel

- #onboarding-squad-public (search for channel ID via `slack_search_channels` on first use, then remember it)
