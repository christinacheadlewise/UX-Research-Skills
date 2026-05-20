# CES Notes

Generates a 4-row notes grid for CES sessions. Columns are derived from the discussion guide sections so notes map directly to the conversation structure.

## How it works
1. Reads the current month's discussion guide
2. Creates columns from guide sections
3. Pre-fills pseudonyms and times from the recruit grid if available

## Trigger phrases
`ces notes`, `ces notes doc`, `set up ces notes`

## Outputs
- `CES/[Month Year]/ces-[month]-[year]-notes.csv`
