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

#### Step 3: Create Recruitment Grid

Generate a CSV: `ces-[month]-[year]-recruit.csv`

```csv
Slot,Time,User ID,Email,Pseudonym,Score,Drop-Off Point,Comments,Country,Consent Form,Status
1,14:00,,,,,,,,,Upcoming
2,14:30,,,,,,,,,Upcoming
3,15:00,,,,,,,,,Upcoming
4,15:30,,,,,,,,,Upcoming
```

**Consent Form values (dropdown):** Not Sent / Sent / Signed
**Status values (dropdown):** Upcoming / Paid / Cancelled / No Show

Save to `CES/[Month Year]/` directory (create if it doesn't exist). Confirm: "Grid saved to `CES/[Month Year]/[filename]`."

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

Post to #onboarding-squad-public:

```
📅 **CES Interviews — Tomorrow ([date])**

Come observe! Here are the session links:

• 2:00pm — [link]
• 2:30pm — [link]
• 3:00pm — [link]
• 3:30pm — [link]

📝 Want to take notes? Notes doc is here: [Google Sheets link]

Feel free to ping me on Slack during the interviews if you want me to ask something!

💡 **What is this?** Every month I run 4 short interviews with customers who recently completed our Customer Effort Score (CES) survey. It's a chance to hear directly about their onboarding experience. More info: [CES Rolling Research Confluence link]
```

Post to **#current-account-onboarding** (search for channel ID via `slack_search_channels` on first use).

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
