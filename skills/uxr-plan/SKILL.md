---
name: uxr-plan
description: Generate a research plan and publish it to Confluence (C20 space). Use when the user says "uxr plan", "new research plan", "write a research plan", "plan a study", or "start a new study". Conversational — asks questions to gather inputs rather than expecting a pasted brief.
---

# UXR Plan: Research Plan Generator

This skill generates a structured research plan through conversation, then publishes it to Confluence as a child page under Active Studies (4125182953).

## Wipe Guard

Before ANY page update, follow the wipe protection rules in the root CLAUDE.md. No exceptions.

## Mode Detection

Ask early: "Is this generative/exploratory or evaluative?" This determines which template to use.

- **Generative/Exploratory** — full plan (diary studies, interviews, longitudinal, discovery)
- **Evaluative** — stripped-down plan (usability tests, concept tests, design testing)

## Flow

### Step 1: Gather Context

Start with:

> "Alright, new research plan. First — what's the study about? Just gimme the elevator pitch."

Then ask ONE question at a time to collect:

1. **Study title** — what should the page be called?
2. **Type** — generative/exploratory or evaluative?
3. **Background** — what's the business context? Why now?
4. **Research goals** — what are you trying to learn?
5. **Research questions** — what specific questions need answering?

Pause after collecting these. Present back a summary for confirmation before continuing.

### Step 2: Methodology & Recruit

Ask ONE at a time:

6. **Methodology** — what method(s)? (interviews, diary study, usability test, survey, card sort, etc.)
7. **Participants** — who are you recruiting? How many? Any screening criteria?
8. **Recruit source** — how will you find them? (panel, in-app, intercept, internal, etc.)

### Step 3: Logistics (Full Plan Only)

For generative/exploratory, also ask:

9. **Stages** — is this multi-stage? If so, what are the stages and KPIs for each?
10. **Timeline** — what weeks does this run? Any hard deadlines?
11. **Materials** — what needs to be created? (discussion guide, screener, diary tasks, stimuli)
12. **Risks** — anything that could go sideways? (recruitment quality, bias, timing)
13. **Stakeholders** — who's R, A, C, I? (Responsible, Accountable, Consulted, Informed)

### Step 3b: Logistics (Evaluative Only)

For evaluative, ask only:

9. **Timeline** — rough dates (1-2 weeks typical)
10. **Materials** — prototype links, discussion guide
11. **Stakeholders** — who needs to know?

### Step 4: Generate the Plan

Once all inputs are collected, generate the Confluence page content using the appropriate template (see references/templates.md).

Present a preview:

> "Here's your plan — take a look and tell me if anything needs changing before I publish."

Show a markdown summary of the key sections (don't dump raw HTML).

### Step 5: Publish to Confluence

Once Christina approves:

1. Create the page as a child of Active Studies (4125182953) in space C20
2. Title format: `Research Plan: [Title], [Quarter] [Year]`
3. Confirm: "Published — [link to page]"
4. Ask: "Want me to update the In Progress table on the hub page too?"

If yes, add the study to the In Progress table on both the hub (4125630194) and Active Studies (4125182953) pages with a blue "Planning" status lozenge.

## Output Standards (Extreme Clarity)

All generated research plans must follow these rules:

1. **Brevity.** Every sentence must earn its place. Cut filler.
2. **No unexpanded acronyms.** First use: "Customer Effort Score (CES)". Then "CES".
3. **Numbered lists** for research questions, risks, and any sequenced items.
4. **Absolute + relative metrics.** "n = 10 (5 from branch, 5 from in-app survey)" not just "10 participants".
5. **Deep link.** Link to referenced pages, docs, or tools — don't describe what a reader could click.
6. **Explicit units.** Always state timeframes ("w/c 26 May"), durations ("60-min sessions"), and sample sizes ("n = 20").
7. **State changes.** If this research is a follow-up, say what was known before and what gap remains.
8. **Proof-read.** Before presenting the plan, re-read every sentence. If it could be interpreted two ways, rewrite it.

## Questioning Style

- One question at a time. Never dump a list.
- Push back if something seems undercooked: "What's the actual decision this'll inform?" or "Who's gonna act on this?"
- If she's vague on methodology, suggest options based on the research questions.
- Don't hallucinate details — if you need more info, ask.
