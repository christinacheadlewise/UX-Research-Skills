# UXR Notes

Generates a session notes spreadsheet where rows are participants and columns mirror the discussion guide sections.

## How it works
1. Reads the discussion guide to extract section names and objectives
2. Proposes column structure: fixed columns (Participant #, Pseudonym, Session Date) + one column per guide section + trailing columns (Other, Key Quotes, Observer Notes)
3. Asks about any extra columns
4. Generates CSV, pre-fills participant info from recruit grid if available

## Trigger phrases
`uxr notes`, `notes grid`, `analysis grid`, `session notes template`, `make a notes doc`, `observation grid`

## Outputs
- `[study-name]-notes-grid.csv`
