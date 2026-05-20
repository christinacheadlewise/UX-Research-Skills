# UXR Grid

Generates a recruitment/participant tracking grid as a CSV file for any research study.

## How it works
1. Identifies the study and pulls screening criteria from the research plan if available
2. Asks about specific screening dimensions and tracking needs
3. Builds a CSV with fixed columns (Participant #, Name, Email, Pseudonym, Status, Session Date/Time, Notes) plus variable columns from screening criteria
4. Presents a preview for approval, then saves

## Trigger phrases
`uxr grid`, `recruitment grid`, `make a recruit grid`, `participant tracker`, `screening grid`

## Outputs
- `[study-name]-recruit-grid.csv`
