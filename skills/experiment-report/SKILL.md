---
name: experiment-report
description: Generate the Consumer Onboarding + Account Team weekly experiment summary report. Pulls from Slack, Confluence (C20 + HOLD spaces), Mixpanel, Lightdash, and all local notes. Covers launched/running/results experiments, regional tests, account team tests, adoption metrics, and open requests.
---

Generate the Consumer Onboarding & Account Team Experiment Summary Report. Pull from all available sources — Slack, Confluence, Mixpanel, Lightdash, and local notes.

**Sources to search:**

- **Slack:** search #current-account-onboarding, #consumer-onboarding, #onboarding-private, #account-squad-day-chatter, #dynamic-recommendations, #account-experience-dev, and any relevant regional channels (e.g. #proj-tap-to-verify-japan, #singapore-growth) for experiment updates, launches, and results in the past month
- **Confluence:** 
  - C20 space (Consumer Onboarding) — pages updated in the past month, Q3/26 Pager, experiment results pages
  - HOLD space (Account/Hold Team) — Q3 Account First Experience pager and related pages
  - COG space — Onboarding & Scalable Growth pages
  - Search broadly: "experiment results" "A/B test" "launched" "shipped" across all relevant spaces
- **Mixpanel:** project 2224100 (Wise Merged) — query for adoption metrics, funnel CVR, and experiment-related events where possible
- **Lightdash:** query for any available onboarding or account adoption dashboards
- **Local notes:** read ALL files in /Users/christina.cheadle/Notes/ — including:
  - All 1:1 notes: /Users/christina.cheadle/Notes/2_Areas/z-121s/
  - Latest daily note: /Users/christina.cheadle/Notes/3_Resources/Daily Notes/ (most recent file)
  - AI memory: /Users/christina.cheadle/Notes/AI/Memory.md
  - Session log: /Users/christina.cheadle/Notes/AI/Session Log.md

**Report sections:**

1. **Recently Launched Experiments** — name, team (onboarding/account/regional), market, hypothesis/purpose, status, early metrics

2. **Running Experiments** — name, team, market, hypothesis, latest metrics with stat sig status, adoption metrics, proven? (✅ / ❌ / ⏳), key trade-offs or tensions

3. **Results Published** (past month) — name, hypothesis, what happened, learnings, proven? (✅ / ❌), decision/next steps

4. **Upcoming Launches** — name, team, market, ETA, what it's testing

5. **Regional Onboarding Tests** — Japan, US/NorthAm, APAC, LatAm, Canada, Spain, MEA, Australia, Singapore, or other markets

6. **Account Team Experiments & Upcoming Work** — tests from the Hold/Account Experience team that touch post-onboarding flows: Launchpad, NBA, account structure, Joint Accounts, FAB, Everyday Account rollout. Include active debates (e.g. NBA vs Send friction, Total Balance removal). Source: HOLD space + #account-squad-day-chatter + #dynamic-recommendations

7. **Key Adoption Metrics** — registration → adopted CVR, F30D revenue per user, contact rate, funnel step drops. Pull from Mixpanel or Confluence pager, whichever is fresher.

8. **Open Stakeholder Requests** — any outstanding analysis or action asks from 1:1 notes or daily notes (Pete, Divya, Jess, Ash, Ian, or others). Not just Pete — check all 1:1 notes.

Format with clear headers, tables where helpful, Confluence links where available, and flag any stat sig status explicitly (✅ stat sig / ⏳ directional / ❌ not sig).
