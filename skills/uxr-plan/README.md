# UXR Plan

Generates a structured research plan through conversation, then publishes to Confluence under Active Studies.

## How it works
1. Detects mode: generative/exploratory (full plan) or evaluative (stripped-down)
2. Gathers context one question at a time: title, background, goals, research questions
3. Collects methodology, participant profile, recruit source, timeline, risks, stakeholders
4. Generates the plan using HTML templates and presents for review
5. Publishes to Confluence as a child of Active Studies
6. Optionally updates the In Progress table on the hub page

## Trigger phrases
`uxr plan`, `new research plan`, `write a research plan`, `plan a study`, `start a new study`

## Outputs
- Confluence page: "Research Plan: [Title], [Quarter] [Year]"
- Optional: In Progress table update on hub + Active Studies pages
