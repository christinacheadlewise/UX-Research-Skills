---
name: ces-guide
description: "CES Rolling Research topline discussion guide. Fixed intro/conclusion, editable middle section that refreshes monthly based on squad input. Use when the user says 'ces guide', 'update ces guide', 'tweak the ces questions', or 'ces middle questions'."
---

# CES Guide: Topline Discussion Guide

A living discussion guide for CES Rolling Research. The intro and conclusion stay the same every month; the middle section rotates based on what the squad wants to explore.

## Flow

### Step 1: Check for Existing Guide

> "Updating the CES guide for this month? Let me check what's there."

Look for `CES/[Month Year]/ces-discussion-guide.md`.

- If it exists: read it, show the current middle section, ask what to change
- If it doesn't exist: create from the template below

### Step 2: Get This Month's Focus

> "What's the focus this month? I can pull from the Slack thread if you've already posted the question, or you can tell me directly."

If pulling from Slack (typically posted 4 days before sessions):
- Read recent messages in #onboarding-squad-public for the CES thread
- Extract suggested topics/questions
- Present: "Here's what the squad asked about: [list]. Want to use all of these or pick?"

If direct input: take whatever Christina gives.

### Step 3: Write/Update Middle Section

Generate 3-5 main questions with probes for the monthly focus area. Present for review:

> "Here's the updated middle section — check the questions and probes:"

Iterate until approved.

### Step 4: Save & Publish

Once Christina approves:

1. Save to `CES/[Month Year]/ces-discussion-guide.md` (overwrite the middle section, keep intro/conclusion intact)
2. Publish to Confluence as a child page under the **monthly CES page** (e.g., "CES Rolling Research — May 2026"):
   - Title: `Discussion Guide: CES Rolling Research — [Month Year]`
   - The monthly page is created by `ces-setup` — titled `[Mon] '[YY] - CES Rolling Research` (e.g., "May '26 - CES Rolling Research")
   - If a guide page already exists for this month, update it (follow wipe guard rules)
   - If not, create a new child page
3. Confirm: "Guide updated for [month] — saved locally and published to Confluence: [link]"

## Confluence Details

- Cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Space ID: `1097630102`
- CES parent page: `4125091326`
- Monthly pages are children of the CES parent page, titled `CES Rolling Research — [Month Year]`

---

## Template

```markdown
# CES Rolling Research — Discussion Guide
**Session length:** 30 minutes
**Updated:** [Month Year]
**This month's focus:** [Topic]

---

## Intro (5 min)

**[Moderator: Start recording, confirm consent]**

Thanks so much for taking the time to chat with me today. My name's Christina, I'm a researcher at Wise.

A few things before we start:
- This'll take about 30 minutes
- There are no right or wrong answers — I'm interested in your honest experience
- I'll be recording this for my notes, but it won't be shared outside the research team
- You can stop at any time or skip any question you're not comfortable with

To warm up:
1. Tell me a bit about yourself — what do you use Wise for?
   - How long have you been using it?
   - What made you sign up?

---

## Core Questions: [Monthly Topic] (20 min)

*Objective: [One sentence describing what we're trying to learn this month]*

1. [Main question]
   - [Probe]
   - [Probe]

2. [Main question]
   - [Probe]
   - [Probe]

3. [Main question]
   - [Probe]
   - [Probe]

**[Moderator: If time, ask:]**
4. [Bonus question]

---

## Conclusion (5 min)

1. Looking back at your experience getting started with Wise, what's one thing you'd change about the process?

2. Is there anything we didn't cover that you think is important for us to hear?

3. Any questions for me?

**[Moderator: Thank them, confirm incentive will be sent within 5 working days, stop recording]**
```

---

## Output Standards (Extreme Clarity)

1. **Brevity.** Questions must be short and open-ended. Cut preamble.
2. **No unexpanded acronyms.** Spell out on first use, even in moderator notes.
3. **Numbered lists** for questions within each section (enables "skip to Q3" references).
4. **Explicit units.** Every section has a time allocation in minutes. Total must equal 30 minutes.
5. **Proof-read.** Before presenting, check that no question could be misread by a moderator unfamiliar with the study.

## Rules

- Intro and Conclusion sections are FIXED. Never modify them unless Christina explicitly asks.
- Only the Core Questions section changes monthly.
- Keep core questions to 3-5 max (it's a 30-min session, 20 min for the middle)
- Always include at least one probe per main question
- Add moderator notes for timing or conditional questions
