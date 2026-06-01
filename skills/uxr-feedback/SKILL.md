---
name: uxr-feedback
description: "Log feedback Christina receives from others. Stores to a private Confluence page. Triggers on 'feedback from', 'log feedback', 'got feedback', or when Christina clearly describes feedback she received from someone."
---

# UXR Feedback: Private Feedback Log

Logs feedback Christina receives from colleagues, managers, or stakeholders to a private Confluence page in her personal space.

## Trigger Phrases

- "feedback from [person]: [what they said]"
- "log feedback"
- "got feedback from [person]"
- "[person] said [feedback]"
- Any clear statement about feedback received from a named person

## Flow

### Step 1: Parse the Feedback

Extract from what Christina tells you:
- **From:** Who gave the feedback (name, role if mentioned)
- **Feedback:** What they said (capture their words, not a summary)
- **Context:** What it was about (e.g., "after the show and tell", "in 1:1", "about the CES presentation")

If any of these are unclear, ask ONE clarifying question. Don't ask for all three — infer what you can.

### Step 2: Confirm Before Logging

Show Christina what you're about to log:

> "Got it — logging this:
>
> **From:** [person]
> **Feedback:** [what they said]
> **Context:** [situation]
>
> That right?"

If she says yes (or something affirmative), proceed. If she corrects, update and confirm again.

### Step 3: Add to Confluence

1. Read the current Feedback Log page (wipe guard — check content length)
2. Add a new row to the table with: Date, From, Feedback, Context
3. Update the page
4. Confirm: "Logged."

### Step 4: Optional — Sentiment Tag

If the feedback is clearly positive or constructive/critical, you can note it. But don't ask — just infer from the content. Don't categorise ambiguous feedback.

## Configuration

- Confluence cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Personal space ID: `4056794091`
- Feedback Log page ID: `4141581118`
- Page is **private** — only Christina can see it

## Rules

1. Never share, reference, or post feedback content anywhere other than this private page
2. Capture feedback in the person's own words where possible — don't sanitise or rephrase
3. Always apply Wipe Guard before updating Confluence
4. Date format: use absolute dates (e.g., "1 June 2026")
5. If Christina gives multiple pieces of feedback at once, log each as a separate row
6. This is Christina's private record — tone should be neutral and factual, not evaluative
