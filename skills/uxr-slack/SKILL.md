---
name: uxr-summarize
description: "Generate an executive summary from a research deck — posts to Slack and publishes to Confluence. Use when the user says 'uxr summarize', 'uxr summary', 'summarise this', 'write a summary', 'share this research', 'uxr slack', 'write a slack summary', 'slack post', or 'summarise this deck'."
---

# UXR Summarize: Research Executive Summary Generator

This skill takes a research slide deck and generates:
1. A formatted Slack post summarising the findings
2. An executive summary page on Confluence (as a child of the project's parent page)

## Flow

### Step 1: Get the Deck

> "What's the deck? Drop me a PDF, a file path, or a Google Slides link."

Read the deck content:
- If PDF: use the Read tool to read the file
- If file path to .md or .txt: read directly
- If Google Slides link: search Drive via Credal (`search_drive_by_keywords_and_get_file_content_or_summary`), or ask Christina to export as PDF
- If on Drive but unreadable: use the local text copy if available

Extract: background, methodology, key findings/insights, recommendations, participant quotes.

### Step 2: Confirm Details

> "Got it. Quick questions before I write this up:"

Ask ONE at a time:
1. "Which channel should the Slack post go in?" (e.g., #consumer-onboarding-public, #consumer-research)
2. "Where on Confluence should the executive summary live? Give me a parent page or I'll suggest one based on the project."
3. "Is this part of a series, or standalone?" (if series, ask what's coming next for teaser)
4. "Any specific insight you want to lead with?"

### Step 3: Generate the Executive Summary

Write both outputs at once. Present both for review before posting/publishing anything.

#### Confluence Executive Summary

Format:

```html
<h2>Research Context</h2>
<p>[Background — what prompted this research, why it matters, methodology, sample size]</p>

<h2>[Finding Area 1]</h2>
<p>[Key finding with supporting data]</p>
<ul><li>[Sub-point]</li><li>[Sub-point]</li></ul>

<h2>[Finding Area 2]</h2>
<p>[Key finding with supporting data]</p>
<ul><li>[Sub-point]</li><li>[Sub-point]</li></ul>

<h2>[Finding Area 3]</h2>
<p>[Key finding with supporting data]</p>
<ul><li>[Sub-point]</li><li>[Sub-point]</li></ul>

<h2>Strategic Recommendations</h2>
<ol><li><strong>[Label]</strong> — [Action]</li></ol>

<h2>Further Research</h2>
<ul><li>[What's next]</li></ul>
```

Rules for Confluence version:
- More detailed than the Slack post — include all major findings, not just top 3
- Include a table for frameworks/matrices where applicable
- Link to the full slide deck and any related pages
- Use warning/note panels for critical gaps or callouts
- Title format: `[Study Title] — Executive Summary`

#### Slack Post

Same format as below (see Slack Format section).

### Step 4: Present for Review

Show both outputs clearly separated:

> "Here's what I've got. Two things to check:"
>
> **1. Confluence executive summary** (will go as a child of [parent page name]):
> [Show the content]
>
> **2. Slack post** (will go to #[channel]):
> [Show the content]
>
> "Anything to change on either before I push?"

**NEVER publish to Confluence or post to Slack without Christina's explicit approval.** Both require a separate "yes" or "push" from her. Do not batch them — ask about each one individually:

> "Happy with the Confluence summary? Say 'push' and I'll publish it to [parent page]."

Then, separately:

> "Happy with the Slack post? Say 'push' and I'll send it to #[channel]."

### Step 5: Iterate

If Christina has edits, apply them and show the updated version. Keep iterating until she approves both.

### Step 6: Publish

Once Christina says to push:

1. **Confluence:** Create the page using `createConfluencePage` as a child of the confirmed parent page. Follow wipe guard rules if updating an existing page. Confirm with link.
2. **Slack:** Post using `slack_send_message` to the confirmed channel. Confirm with link.

If she only approves one, only publish that one.

> "Published to Confluence: [link]. Posted to #[channel]."

## Slack Format

```
[Emoji] **[Study Title]**

📎 [Link to deck]

**Background**
[2-3 sentences of context — what prompted this research and why it matters]

**Methodology**
• [Method] with [n] participants
• [Participant description]
• [Timeframe]

**TL;DR**
• [Punchy bullet 1 — the headline finding]
• [Punchy bullet 2]
• [Punchy bullet 3]
• [Optional bullet 4]

**Key Insights**

[Emoji] **[Insight Name]**
[One-sentence summary]
> "[Participant quote]" — P[X]

[Emoji] **[Insight Name]**
[One-sentence summary]
> "[Participant quote]" — P[X]

[Emoji] **[Insight Name]**
[One-sentence summary]
> "[Participant quote]" — P[X]

**Recommendations**
• **[Bold label]** — [One sentence on what to do]
• **[Bold label]** — [One sentence on what to do]
• **[Bold label]** — [One sentence on what to do]

[Optional teaser if series: "Next up: [what's coming]"]

💬 Questions? Thread below or DM me.
```

## Formatting Rules

- **Emojis for insights:** Use varied, relevant emojis. Don't repeat the same one.
- **Header emoji:** Pick one that reflects the study theme.
- **Quotes:** Always include at least one participant quote per insight. Use pseudonyms (P1, P2) not real names.
- **TL;DR bullets:** Short, punchy, opinionated. These are findings, not descriptions of what you did.
- **Recommendations:** Actionable. Start with a bold label that a PM could put on a ticket.
- **Length:** Aim for readable in 2 minutes. 3-5 insights max for Slack. Confluence can be more detailed.

## Output Standards (Extreme Clarity)

1. **Prioritise brevity.** TL;DR bullets should be punchy — one finding per line.
2. **No unexpanded acronyms.** First use: "Customer Effort Score (CES)". Then "CES" is fine.
3. **Absolute + relative metrics.** "7 of 10 participants (70%)" not just "most participants".
4. **Deep link.** Always link to the full deck/report — never describe where to find it.
5. **Explicit units.** Always state sample size, method, and timeframe in the methodology section.
6. **State changes.** If this builds on prior research, say what was known before and what's new.
7. **Proof-read.** Before presenting, re-read every bullet. If it could be interpreted two ways, rewrite it.

## Tone

- Confident but not academic
- Direct, not hedging ("We found..." not "It appeared that perhaps...")
- Accessible to non-researchers (no jargon, explain methods briefly)
- The TL;DR should make someone care enough to read the rest

## Questioning Style

- If the deck is ambiguous on a finding, ask: "What's the actual implication here? What should the team do differently?"
- If quotes are weak or absent, ask: "Got any standout quotes from sessions? Even paraphrased is fine."
- If there are too many findings, ask: "If you could only tell them three things, what would they be?"
