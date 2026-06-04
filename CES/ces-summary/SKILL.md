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

Once approved:

1. Update the **monthly CES page** (e.g., "CES Rolling Research — May 2026") with the summary content:
   - The monthly page is created by `ces-setup` — titled `[Mon] '[YY] - CES Rolling Research` (e.g., "May '26 - CES Rolling Research")
   - Replace the placeholder text with the full summary in HTML format
   - Follow wipe guard rules (read page first, compare lengths)

2. Update the **Past Summaries table** on the CES Rolling Research parent page (4125091326):
   - Read the page first (wipe guard)
   - Add a new row to the table: Month | Topic | Link to child page (smart link)

3. Optionally update the Research Repository table (4125116067) if Christina wants it listed there too.

Follow wipe guard rules for all page updates.

## Confluence Details

- Cloud ID: `6c85b940-0f26-4355-9ba6-61ca2d0ce603`
- Space ID: `1097630102`
- CES parent page: `4125091326`
- Research Repository: `4125116067`
- Hub page: `4125630194`

### Step 5: Post to Slack

Post a condensed version to #onboarding-squad-public:

```
🔬 **CES Rolling Research — [Month] Summary**

Spoke to [n] customers this month about **[topic]**.

**Key takeaways:**
[emoji] [Finding 1 — one line]
[emoji] [Finding 2 — one line]
[emoji] [Finding 3 — one line]

💬 Best quote:
> "[Quote]" — P[X]

**Recommendations:**
[emoji] [Recommendation 1 — one line]
[emoji] [Recommendation 2 — one line]
[emoji] [Recommendation 3 — one line]

Full write-up: [embedded Confluence link]
Watch the recordings: [embedded recordings link]

Questions? Thread below 👇
```

Each takeaway AND each recommendation gets its own emoji prefix (choose one that fits — e.g. 💸 funding, ❓ confusion, 🚫 dead-end; ✅ shipped/validated, 🔧 fix, 🆔 identity). Always include the recordings folder link alongside the write-up link. Include a short recommendations list (one line each) — if a recommendation is already validated/shipped by an experiment, note that rather than presenting it as a new ask.

Confirm: "Published to Confluence and posted to Slack."

---

## Output Standards (Extreme Clarity)

1. **Prioritise brevity.** Findings are 2-3 sentences max. Slack version is one line per finding.
2. **No unexpanded acronyms.** First use: "Customer Effort Score (CES)". Then "CES" is fine.
3. **Absolute counts only — NEVER a percentage for participant findings.** Write "3 of 4 participants" — never "75%" or "3 of 4 (75%)". With a sample this small, a percentage reads like a statistic and is misleading; it implies a precision and projectability the data does not have. The ONLY percentages allowed in a CES summary are figures quoted directly from an external, properly-powered source (e.g. an A/B experiment readout), and they must be attributed to that source. This rule has NO exceptions for CES-derived numbers.
4. **Numbered lists** for findings and recommendations.
5. **Deep link, always embedded.** Always include the Confluence page link AND the session recordings folder link in Slack posts. Link to related prior CES summaries when referencing patterns. ALL links must be embedded behind descriptive text (e.g. "Watch the recordings") — never paste a raw, visible URL.
9. **Emoji before each Slack takeaway.** Every key-takeaway bullet in the Slack post starts with an emoji that fits the finding. Not in the Confluence write-up — Slack only.
6. **Explicit units.** Always state sample size ("n = 4"), session length ("30-minute sessions"), and timeframe ("May 2026").
7. **State changes.** If a finding reinforces or contradicts prior months, say what was known before and what's new.
8. **Proof-read.** Before presenting, re-read every finding. If it could be interpreted two ways, rewrite it.

## Rules

- Keep summaries brief — this is rolling research, not a deep-dive. 1 page max.
- 3-4 findings is the sweet spot. Don't force more.
- Always include participant quotes.
- Connect to past CES rounds if patterns are emerging across months.
- Don't hallucinate findings. If only 1 of 4 people said something, say "one participant" not "participants."
- If a transcript is poor quality or the session was cut short, note it rather than over-interpreting thin data.
