---
name: ces-notes
description: "Generate a notes doc for this month's CES sessions. 4 participant rows, columns from the discussion guide. Use when the user says 'ces notes', 'ces notes doc', or 'set up ces notes'."
---

# CES Notes: Monthly Session Notes Grid

Generates a notes grid for the 4 CES sessions. Pulls columns from the current CES discussion guide.

## Flow

### Step 1: Read the Guide

Check for `CES/[Month Year]/ces-discussion-guide.md`.

- If found: extract section names (Intro, Core Questions topic, Conclusion)
- If not found: ask Christina what the sections are

### Step 2: Generate the Grid (Google Sheet)

Create a Google Sheet via Credal (`create_a_spreadsheet`) titled: `CES [Month] [Year] — Session Notes`

Sheet structure (1 sheet called "Notes", frozen header row):

| Slot | Time | Pseudonym | Warm-Up (Use Case + History) | [Core Topic]: Q1 | [Core Topic]: Q2 | [Core Topic]: Q3 | One Thing to Change | Other | Key Quotes |
|------|------|-----------|------------------------------|-------------------|-------------------|-------------------|---------------------|-------|------------|
| 1 | 14:00 | | | | | | | | |
| 2 | 14:30 | | | | | | | | |
| 3 | 15:00 | | | | | | | | |
| 4 | 15:30 | | | | | | | | |

**Fixed columns:**
- Slot (1-4)
- Time
- Pseudonym

**From guide:**
- Warm-Up (always: use case + history)
- One column per core question (named after the question topic, shortened)
- "One Thing to Change" (from conclusion Q1)

**Trailing:**
- Other
- Key Quotes

After creating the sheet, use `update_a_spreadsheet` to write the header row and 4 data rows.

### Step 3: Output

Confirm: "Notes grid created: [Google Sheet link]. Four rows, ready to fill during sessions."

---

## Output Standards (Extreme Clarity)

1. **Column headers must be unambiguous.** "[Topic]: Q1 (brief label)" not just "Q1".
2. **Explicit units.** Times include format ("14:00"). Dates use full format ("27 May 2026") in filenames and confirmations.
3. **No acronyms in column headers** unless universally known within the team.
4. **Proof-read.** Before saving, check that no column name could be misread by an observer unfamiliar with the study.

## Rules

- Always 4 rows (4 sessions)
- Column names from the guide, shortened to under 30 characters
- If the recruitment Google Sheet exists for this month, offer to pre-fill pseudonyms and times from it
