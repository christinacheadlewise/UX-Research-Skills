---
name: uxr-grid
description: Generate a recruitment grid spreadsheet for a research study. Use when the user says "uxr grid", "recruitment grid", "make a recruit grid", "participant tracker", or "screening grid". Pulls screening criteria from the research plan if available.
---

# UXR Grid: Recruitment Grid Generator

This skill generates a structured recruitment/participant tracking grid. Output is a CSV file that can be opened in Google Sheets or Excel.

## Flow

### Step 1: Identify the Study

> "Which study is this grid for? Got a research plan I should pull screening criteria from?"

If a plan exists:
- Read the research plan page to extract: participant criteria, sample size, recruit source
- Confirm: "I've pulled these criteria from the plan: [list]. Anything to add or change?"

If no plan:
1. What's the study?
2. How many participants? (n = ?)
3. What are the screening criteria? (demographics, behaviours, product usage, etc.)

### Step 2: Define Variable Columns

Ask:

4. "Any specific screening dimensions you want as columns? (e.g., age range, device type, Wise usage, financial product mix)"
5. "Anything you want to track beyond the standard columns?"

### Step 3: Generate the Grid

Build a CSV with:

**Fixed columns (always present):**
- Participant # (P1, P2, etc.)
- Name
- Email
- Pseudonym
- Status (dropdown values: Signed Up / Confirmed / Paid / Cancelled / No Show)
- Session Date/Time
- Notes

**Variable columns (from screening criteria):**
- One column per screening dimension identified in Step 2

Present a preview as a markdown table:

> "Here's the grid structure — [N] columns. Look right?"

### Step 4: Output

Once approved:
1. Write the CSV to the current working directory: `[study-name]-recruit-grid.csv`
2. Pre-fill the Participant # column (P1 through Pn)
3. Leave all other cells empty (ready for filling)
4. Confirm: "Grid saved to `[filename]`. Open it in Sheets and you're good to go."

Optional: "Want me to also create a Google Sheet? (I'd need you to upload the CSV — I can't create Sheets directly)"

## Grid Format

```csv
Participant,Name,Email,Pseudonym,Status,Session Date/Time,[Variable1],[Variable2],...,Notes
P1,,,,,,,,
P2,,,,,,,,
P3,,,,,,,,
```

## Status Values

Standard status options (for reference when filling):
- **Signed Up** — expressed interest, not yet confirmed
- **Confirmed** — session booked
- **Paid** — incentive sent
- **Cancelled** — withdrew before session
- **No Show** — didn't attend

## Output Standards (Extreme Clarity)

1. **Column headers must be unambiguous.** "Age Range (years)" not "Age". "Device (primary)" not "Device".
2. **Status values are predefined.** List all valid options in the header row or a legend — no free text for status.
3. **Explicit units.** Time columns include timezone ("14:00 BST"). Date columns use full format ("27 May 2026").
4. **No acronyms in column headers** unless universally known within the team.

## Questioning Style

- One question at a time
- If criteria are vague, push: "What would disqualify someone? That tells me what columns you actually need."
- Suggest common screening dimensions based on methodology (e.g., for usability testing: device type, tech confidence; for diary studies: notification preferences, availability window)
