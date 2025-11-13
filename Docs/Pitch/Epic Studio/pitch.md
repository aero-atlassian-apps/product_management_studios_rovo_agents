# Epic Studio — Pitch Deck v3 (Narrative Flow)

Act I: Our Reality (The Status Quo)

## Slide 1 — Title
Title: Epic Studio
Subtitle: Amplify product judgment. Turn vision into delivery.

## Slide 2 — Jira Is Our Backbone
Message: Jira drives delivery; Epics connect strategy to execution.
Key points:
- Epics are the strategic bridge from "why" to "what".
- When Epics are clear, teams move faster with confidence.

## Slide 3 — The Fragile Bridge
Message: Ambiguity slows teams and increases rework.
Impacts:
- Delays in sprint starts; blocked developers.
- Heavy rework; duplication and overlap.
- Misalignment between vision and delivery.

## Slide 4 — The Cost (C‑Level Pain)
Message: Poor Epic quality quietly taxes the organization.
Signals:
- Low ready rate, unclear goals, inconsistent outcomes.
- Governance friction and late escalations.

Act II: The Revelation (The Opportunity)

## Slide 5 — Amplify, Don’t Replace
Message: AI that augments product judgment, not human ownership.
Principles:
- Consent-first. Transparent. Epic-focused.
- Copy-ready outputs; technical formats on request.

## Slide 6 — Epic Studio Is Here
Message: A disciplined, end-to-end Epic lifecycle agent.
Core promise:
- From creation to evaluation, scoring, recommendations, improvement,
  progress analysis, and portfolio analysis.
- Automation-ready: integrates with Jira Automation for scheduled and event-based runs.

Act III: How It Works (The Proof)

## Slide 7 — Lifecycle Overview (End-to-End)
Message: One coherent flow for Epic lifecycle.
Sequence:
- Create → Evaluate → Automatic Scoring & Recommendations → Improve Existing →
  Analyze Epic Progress → Analyze Epic Portfolio.

## Slide 7b — Active Scenarios (Labels)
- Default (par défaut, redirection explicite)
- Créer une Epic de qualité
- Évaluer la qualité d’une Epic
- Améliorer une Epic existante
- Analyser avancement Epic (manuel)
- [AUTO] Analyser avancement Epic (automation‑only)
- [AUTO] Scoring & évaluation d’une Epic (automation‑only)
- Analyser portefeuille Epics

## Slide 8 — Create with Discipline
Message: Guide a raw idea into a complete, clear Epic.
What it does:
- Enforces essential dimensions (context, goals, personas, outcomes).
- Checks clarity; detects potential duplication/overlap.

## Slide 9 — Evaluate with Objectivity
Message: Shared language via a 0–100 quality score.
What it does:
- Scores against clear criteria; explains gaps.
- Produces actionable recommendations, not generic advice.

## Slide 10 — Automatic Scoring & Recommendations
Message: Fast, consistent, consent-first scoring for any Epic.
What it does:
- Generates score and targeted recommendations automatically.
 - Ready-to-copy summary; explicit handling on connector limits (no action; copy-ready block).
- Triggers: on schedule (e.g., nightly), on Epic updates, on status transitions, on labels.

## Slide 10b — Automation-First Integration (Jira Automation)
Message: Flexible, auditable automation built into the lifecycle.
What it enables:
- Schedule-based runs (cron): evaluate, score, recommend, progress analysis.
- Event-based runs: issue created/updated, field change, status transition.
- Scoped rules: per project, per label, per component; dry-run mode for audit.
- Outputs are copy-ready and logged; consent-first actions when required.

## Slide Notes — Automation Examples (Jira Automation)
Example 1 — Nightly Scoring & Recommendations (Scheduled)
- Trigger: schedule (cron `0 2 * * *`)
- Scope (JQL): `issuetype = Epic AND project IN (ABC, DEF) AND statusCategory != Done`
- Actions (non-destructive):
- Evaluate + score + targeted recommendations via agent
- Add comment with score summary and next actions
- Optional: update custom field `Epic Quality Score`

Pseudo-config:
```
trigger:
  type: schedule
  cron: "0 2 * * *"
  jql: "issuetype = Epic AND project IN (ABC, DEF) AND statusCategory != Done"
actions:
  - agent.evaluateScoreRecommend(issueKey)
  - addComment(issueKey, summary)
  - setField(issueKey, "Epic Quality Score", score)
guardrails:
  scope: projects_whitelist
  mode: dry_run_enabled
  unavailability_handling: copy_ready_outputs
```

Example 2 — Progress Analysis on Status Transition
- Trigger: issue transitioned to `Ready for Review`
- Scope: `issuetype = Epic`
- Actions (non-destructive):
- Run progress completeness analysis via agent
- Add comment with completeness breakdown and blockers/next steps
- Optional: set field `Progress Completeness` and label `needs-changes` if below threshold

Pseudo-config:
```
trigger:
  type: status_transition
  to_status: "Ready for Review"
  issuetype: Epic
conditions:
  - project IN (ABC, DEF)
actions:
  - agent.progressAnalysis(issueKey)
  - addComment(issueKey, analysis.summary)
  - setField(issueKey, "Progress Completeness", analysis.completeness)
  - setLabel(issueKey, analysis.threshold_ok ? "review-ok" : "needs-changes")
guardrails:
  scope: projects_whitelist
  mode: non_destructive_defaults
  audit: logs_enabled
```

## Slide 11 — Improve Existing Epics
Message: Precision enhancements with “before / after”.
What it does:
- Identifies weak sections; proposes concrete rewrites.
- Keeps PO in control; no silent changes.

## Slide 12 — Analyze Epic Progress
Message: See advancement clearly, remove friction early.
What it does:
- Manual and automatic progress analysis for an Epic.
- Surfaces blockers/risks; highlights next actions.
- Completeness model:
- Coverage of essential dimensions (context, measurable goals, personas, outcomes).
- Readiness checklist fields, acceptance criteria presence and clarity.
- Links to initiatives/OKRs if available; dependency and risk flags.
- Status history and activity signals (comments, updates) to gauge momentum.

## Slide 13 — Analyze Epic Portfolio
Message: Portfolio visibility for leaders and teams.
What it does:
- Quality distribution and ready rate across Epics.
- Detects duplicates/overlaps; spot portfolio hotspots.

## Slide 14 — Governance & Trust
Message: Reliability built into every step.
Guardrails:
- Pre‑flight checks before proposing actions.
- Explicit consent; transparent handoffs.
 - Explicit handling on unavailability: copy‑ready outputs if actions cannot run.
- Scope limited to Epics; redirects story breakdown to Product Backlog Studio.
- Automation guardrails: whitelisted projects, scoped triggers, non-destructive defaults, logs and auditability.

Act IV: Why It Matters (The Value)

## Slide 15 — Value by Role
Product:
- Faster decisions, reusable templates, clear outcomes.
Delivery:
- Fewer blockages, “Ready” Epics, smoother sprint starts.
Leadership:
- Visibility on quality and alignment; predictable delivery.

## Slide 16 — Simple KPIs
Message: Measure what matters.
Examples:
- Epic quality score (average, distribution).
- Ready rate (% passing pre‑validation).
- Lead time (idea → Ready).
- Duplication/overlap avoided.

Act V: The Future (The Vision)

## Slide 17 — Built‑In Quality Culture
Message: Quality is integrated, not policed.
Outcomes:
- POs focus on strategy, not admin.
- Teams understand the "why"; delivery is more predictable.

Act VI: Call to Action (The Decision)

## Slide 18 — Pilot Plan (6–8 Weeks)
Message: Start small, measure, decide.
Plan:
- Weeks 1–2: Select 3 domains; set 5 KPIs.
- Weeks 3–5: Use (create, evaluate, improve, pre‑validate); optional automation pilot.
- Automation pilot: nightly scoring & recommendations; on "Ready for Review" status change run progress analysis.
- Weeks 6–8: Impact summary; scale decision.

## Slide 19 — Success Thresholds
Message: Define success before scaling.
Examples:
- +15 points ready rate; −20% lead time; −30% rework.

## Slide 20 — Questions & Discussion
Message: Ready to make Epics clear, aligned, and faster?

## Appendix — Active Scenarios (labels)
- Default (par défaut, redirection explicite)
- Créer une Epic de qualité
- Évaluer la qualité d’une Epic
- Améliorer une Epic existante
- Analyser avancement Epic (manuel)
- [AUTO] Analyser avancement Epic (automation‑only)
- [AUTO] Scoring & évaluation d’une Epic (automation‑only)
- Analyser portefeuille Epics