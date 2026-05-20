---
name: uxr-slack
description: Generate a summary Slack post from a research slide deck (PDF or Google Slides link). Use when the user says "uxr slack", "write a slack summary", "slack post", "share this research", "write up for slack", or "summarise this deck for slack".
---

# UXR Slack: Research Summary Post Generator

This skill takes a research slide deck and generates a formatted Slack post summarising the findings. Can post directly to a channel or output as text for Christina to paste.

## Flow

### Step 1: Get the Deck

> "What's the deck? Drop me a PDF, a file path, or a Google Slides link."

Read the deck content:
- If PDF: use the Read tool to read the file
- If file path to .md or .txt: read directly
- If Google Slides link: ask Christina to export as PDF or paste key slides

Extract: background, methodology, key findings/insights, recommendations, participant quotes.

### Step 2: Confirm Details

> "Got it. Quick questions before I write this up:"

Ask ONE at a time:
1. "Which channel should this go in?" (e.g., #consumer-onboarding-public, #consumer-research)
2. "Is this part of a series, or standalone?" (if series, ask what's coming next for teaser)
3. "Any specific insight you want to lead with?"

### Step 3: Generate the Post

Write the Slack post following this format:

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

Present the draft:

> "Here's the Slack post — check tone and content. Anything to change?"

### Step 4: Iterate

If Christina has edits, apply them and show the updated version. Keep iterating until she approves.

### Step 5: Post or Output

Once approved, ask:

> "Ready to post? I can send it to [channel name] now, or just hand you the text to paste yourself."

If posting directly:
- Use `slack_send_message` to the confirmed channel
- Confirm: "Posted to #[channel]."

If text output:
- Display the final formatted text for copy-paste

## Formatting Rules

- **Emojis for insights:** Use varied, relevant emojis (🧠 🔍 💡 🎯 🚨 📊 🗣️ 🏦 💳 🔑 ⚡ 🧩). Don't repeat the same one.
- **Header emoji:** Pick one that reflects the study theme (🏦 for banking, 🧭 for navigation, 🎨 for design, etc.)
- **Quotes:** Always include at least one participant quote per insight. Use pseudonyms (P1, P2) not real names.
- **TL;DR bullets:** Short, punchy, opinionated. These are findings, not descriptions of what you did.
- **Recommendations:** Actionable. Start with a bold label that a PM could put on a ticket.
- **Length:** Aim for readable in 2 minutes. 3-5 insights max. If there are more, pick the most impactful.

## Tone

- Confident but not academic
- Direct, not hedging ("We found..." not "It appeared that perhaps...")
- Accessible to non-researchers (no jargon, explain methods briefly)
- The TL;DR should make someone care enough to read the rest

## Questioning Style

- If the deck is ambiguous on a finding, ask: "What's the actual implication here? What should the team do differently?"
- If quotes are weak or absent, ask: "Got any standout quotes from sessions? Even paraphrased is fine."
- If there are too many findings, ask: "If you could only tell them three things, what would they be?"
