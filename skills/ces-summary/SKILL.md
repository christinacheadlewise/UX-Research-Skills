---
name: ces-summary
description: "Process CES interview transcripts into a brief monthly summary for Confluence and Slack. Use when the user says 'ces summary', 'summarise ces', 'ces write-up', 'ces transcripts', or 'write up ces'."
---

# CES Summary: Monthly Transcript → Summary Pipeline

Takes CES interview transcripts, generates a brief monthly summary, and publishes to Confluence + Slack.

## Flow

### Step 1: Get Transcripts

> "Drop me the CES transcripts — file paths, pasted text, or a directory."

Read each transcript. Expect up to 4 (one per session).

### Step 2: Process

For each transcript:
1. Code key moments against this month's core questions
2. Pull standout quotes (verbatim, with pseudonym)
3. Note anything unexpected or off-topic but interesting

After processing all transcripts, generate a cross-session summary.

### Step 3: Generate Summary

Format:

```markdown
## CES Rolling Research — [Month Year]

**Topic this month:** [Monthly focus area]
**Participants:** [n] customers who recently completed onboarding
**Method:** 30-min semi-structured interviews

### Key Findings

**1. [Finding title]**
[2-3 sentences. How many participants expressed this.]
> "[Quote]" — P[X]

**2. [Finding title]**
[2-3 sentences.]
> "[Quote]" — P[X]

**3. [Finding title]**
[2-3 sentences.]
> "[Quote]" — P[X]

### Patterns & Connections
- [Connection to previous CES rounds or broader research if relevant]
- [Anything that reinforces or contradicts known findings]

### Recommendations
- **[Action label]** — [One sentence]
- **[Action label]** — [One sentence]

### Next Month
[Suggested topic for next round, based on loose threads from this month]
```

Present for review:

> "Here's the CES summary for [month]. Check it over — anything to change before I publish?"

### Step 4: Publish to Confluence

Once approved, create a child page under the CES research page (or Active Studies if no CES parent exists):

- Title: `CES Rolling Research — [Month Year]`
- Content: the summary in HTML format

Also update the Research Repository table if this is a new entry.

Follow wipe guard rules for any page updates.

### Step 5: Post to Slack

Post a condensed version to #onboarding-squad-public:

```
🔬 **CES Rolling Research — [Month] Summary**

Spoke to [n] customers this month about **[topic]**.

**Key takeaways:**
• [Finding 1 — one line]
• [Finding 2 — one line]
• [Finding 3 — one line]

💬 Best quote:
> "[Quote]" — P[X]

Full write-up: [Confluence link]

Questions? Thread below 👇
```

Confirm: "Published to Confluence and posted to Slack."

---

## Rules

- Keep summaries brief — this is rolling research, not a deep-dive. 1 page max.
- 3-4 findings is the sweet spot. Don't force more.
- Always include participant quotes.
- Connect to past CES rounds if patterns are emerging across months.
- Don't hallucinate findings. If only 1 of 4 people said something, say "one participant" not "participants."
- If a transcript is poor quality or the session was cut short, note it rather than over-interpreting thin data.
