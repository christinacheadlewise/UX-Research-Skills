---
name: uxr-guide
description: Generate a discussion guide for a qualitative research study. Use when the user says "uxr guide", "write a discussion guide", "new discussion guide", "create a guide", or "build a moderator guide". Conversational — pulls from research plan if available, asks questions to fill gaps.
---

# UXR Guide: Discussion Guide Generator

This skill generates a timed, structured discussion guide and publishes it to Confluence as a child page under the relevant research plan.

## Flow

### Step 1: Identify the Study

> "Which study is this guide for? Is there a research plan already on Confluence I should pull from, or are we starting fresh?"

If a plan exists:
- Read the research plan page to extract: research goal, research questions, methodology, participant profile, session length
- Confirm: "I've pulled your RQs and goals from the plan. Anything to add or change for this guide?"

If no plan exists, ask:
1. What's the study about?
2. What are the research questions?
3. Who are the participants?
4. How long are sessions? (default: 60 min)

### Step 2: Guide Structure

Ask ONE at a time:

5. "Any specific topics or sections you already know you want? Or should I propose a structure based on the RQs?"
6. "Any exercises or activities? (card sort, prototype walkthrough, diary debrief, stimulus reaction, etc.)"
7. "Any stimulus materials to reference? (prototypes, screenshots, concepts)"

### Step 3: Generate the Guide

Build the guide using the structure below. Present a markdown preview of the full guide for review.

> "Here's your guide — check the flow, timing, and probes. Tell me what to change."

Iterate until Christina approves.

### Step 4: Publish

Once approved:
1. Create as a child page under the research plan (if one exists) or under Active Studies (4125182953)
2. Title format: `Discussion Guide: [Study Name]`
3. Confirm with link

## Guide Structure

### Header Block
```html
<div data-type="panel-info">
<p><strong>Study:</strong> [Study name]</p>
<p><strong>Goal:</strong> [One-sentence research goal]</p>
<p><strong>Key Questions:</strong></p>
<ol><li><p>[RQ1]</p></li><li><p>[RQ2]</p></li><li><p>[RQ3]</p></li></ol>
<p><strong>Session Length:</strong> [X] minutes</p>
<p><strong>Participants:</strong> [Brief description]</p>
</div>
```

### Section Format
Each section follows this pattern:

```html
<h3>[Section Name] ([X] min)</h3>
<p><em>Objective: [What this section aims to learn]</em></p>
<ol>
<li><p>[Main question]</p>
<ul>
<li><p>[Probe]</p></li>
<li><p>[Probe]</p></li>
</ul>
</li>
<li><p>[Main question]</p>
<ul>
<li><p>[Probe]</p></li>
</ul>
</li>
</ol>
<p><strong>[Moderator note: instruction in brackets]</strong></p>
```

### Standard Sections (adapt per study)

1. **Intro & Logistics (5 min)** — consent, recording, ground rules, icebreaker
2. **Warm-Up / Context Setting (5-10 min)** — broad opening questions about their world
3. **Core Sections (bulk of time)** — 2-4 sections, each with:
   - An objective tied to a research question
   - 3-5 main questions with nested probes
   - Moderator notes for transitions, timing, or stimulus introduction
4. **Activities / Exercises (if any)** — timed, with clear instructions
5. **Wrap-Up (5 min)** — anything else, biggest takeaway, thank and close

### Timing Rules

- Total section times MUST add up to the session length
- Leave 5 min buffer (bake into the longest section)
- If session is 30 min: 2 min intro, 5 min warm-up, 18 min core, 5 min wrap
- If session is 60 min: 5 min intro, 10 min warm-up, 40 min core, 5 min wrap
- If session is 90 min: 5 min intro, 10 min warm-up, 65 min core (split into 3-4 sections), 5 min wrap, 5 min buffer

### Moderator Notes

Use bold bracketed text for instructions to the moderator:

- **[Share screen / show prototype]**
- **[If participant hasn't mentioned X, probe here]**
- **[Transition: "Now I'd like to shift to..."]**
- **[Time check — if over 30 min, skip to Section 4]**
- **[Hand participant the card sort / open activity]**

### Probe Types

Use a mix:
- Clarification: "Can you tell me more about that?"
- Example: "Can you give me a specific example?"
- Contrast: "How does that compare to [X]?"
- Emotion: "How did that make you feel?"
- Hypothetical: "What would you expect to happen if...?"
- Process: "Walk me through what you did step by step."

## Confluence Details

- Cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Space ID: `1097630102`
- Christina's Account ID: `712020:fd1bc9ec-14f4-4a60-8912-f251a32e1b6f`

## Questioning Style

- One question at a time
- If the RQs are vague, push: "What would a good answer to that question actually look like? What decision does it feed?"
- Suggest probes Christina might not have thought of
- Don't pad — if a 30-min session only needs 4 questions, don't invent filler
