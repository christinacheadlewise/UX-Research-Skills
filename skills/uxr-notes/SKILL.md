---
name: uxr-notes
description: Generate a notes/analysis spreadsheet for a research study. Rows are participants, columns mirror discussion guide sections. Use when the user says "uxr notes", "notes grid", "analysis grid", "session notes template", "make a notes doc", or "observation grid".
---

# UXR Notes: Session Notes Grid Generator

This skill generates a structured notes spreadsheet where rows = participants and columns = discussion guide sections. Output is a CSV that can be opened in Google Sheets.

## Flow

### Step 1: Identify the Source

> "Which study is this for? Is there a discussion guide I should pull sections from?"

If a discussion guide exists on Confluence:
- Read the guide page to extract section names and their objectives
- Confirm: "I've pulled these sections from the guide: [list]. Using these as columns — sound right?"

If no guide exists, ask:
1. What's the study?
2. What are the main sections/topics of each session? (list them)
3. How many participants?

### Step 2: Confirm Structure

Present the proposed columns:

> "Here's the grid layout:
>
> | Participant | Pseudonym | [Section 1] | [Section 2] | ... | Other | Key Quotes | Observer Notes |
>
> [N] participants as rows. Look good, or want to add/remove columns?"

Ask:
4. "Any extra columns beyond the guide sections? (e.g., 'Overall Impression', 'Usability Issues', 'Emotional Reactions')"

### Step 3: Generate the Grid

Build a CSV with:

**Fixed columns (always present):**
- Participant # (P1, P2, etc.)
- Pseudonym
- Session Date

**Variable columns (from discussion guide sections):**
- One column per guide section, named after the section
- Each cell is for notes captured during that section of the interview

**Trailing columns (always present):**
- Other (catch-all for anything that doesn't fit a section)
- Key Quotes (verbatim quotes worth pulling)
- Observer Notes (if observers are present)

### Step 4: Output

Once approved:
1. Write the CSV to the current working directory: `[study-name]-notes-grid.csv`
2. Pre-fill Participant # column (P1 through Pn)
3. If pseudonyms are known from the recruitment grid, pre-fill those too
4. Leave all note cells empty
5. Confirm: "Grid saved to `[filename]`. Open it in Sheets — one row per session, fill as you go."

## Grid Format

```csv
Participant,Pseudonym,Session Date,[Section 1: Name],[Section 2: Name],...,Other,Key Quotes,Observer Notes
P1,,,,,,,,
P2,,,,,,,,
P3,,,,,,,,
```

## Column Naming

- Use the section name from the guide, shortened if needed
- Keep under 30 characters per column header
- Examples: "Warm-Up: Financial Life", "Mental Models", "Prototype Reaction", "Diary Debrief"

## Linking to Recruitment Grid

If a recruitment grid already exists for this study (check working directory for `*-recruit-grid.csv`):
- Offer to pull participant numbers and pseudonyms from it
- "I found your recruit grid — want me to pre-fill the participant list from there?"

## Output Standards (Extreme Clarity)

1. **Column headers must be unambiguous.** "Warm-Up: Financial Life" not "Warm-Up". "Prototype Reaction (Task 2)" not "Prototype".
2. **Numbered lists** for any sequenced items in instructions or confirmations.
3. **Explicit units.** Session dates use full format ("27 May 2026"). Times include timezone if relevant.
4. **No acronyms in column headers** unless universally known within the team.
5. **Proof-read.** Before presenting, check that no column name could be misread by an observer unfamiliar with the study.

## Questioning Style

- One question at a time
- If sections are unclear, ask: "What's the main thing you're listening for in that section? That'll help me name the column."
- Suggest an "Other" column is always useful — things come up
