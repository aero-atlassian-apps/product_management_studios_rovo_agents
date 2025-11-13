# "Epic Studio" Cheat Sheet — Production Prompt (PDF, Hand‑Drawn Style)

This prompt is designed for Google Note LM (or similar design tools) to generate a one‑page PDF cheat sheet in a hand‑drawn/written visual sketching style. It reflects the current Epic Studio agent capabilities end‑to‑end and uses the brand colors and watermark.

## Output Requirements
- Format: PDF, single page (A4 portrait). Safe margins: 12–16 mm.
- Background: snow white (#FFFAFA or pure white).
- Colors: primary text/accent `#EA5B39`, secondary accent `#F7B02F`, default text black `#000000`.
- Style: hand‑drawn sketch; uneven line strokes; doodle icons; handwritten fonts.
- Watermark: use `Brand/epic_studio_logo_icon_256x240.svg` centered at 10–12% opacity behind content.
- Typography: headings in a handwritten font (e.g., “Patrick Hand”, “Architects Daughter”, “Marker Felt”); body in a clean sans (e.g., Inter) or a legible handwritten style; keep lines short.

## Visual Composition (Hand‑Drawn Layout)
- Title banner at top with hand‑drawn underline.
- Five sketched panels arranged in a loose grid:
  1) What is the agent
  2) Capabilities (end‑to‑end)
  3) Active scenarios (French labels)
  4) How to use — manual
  5) How to use — automation
- Hand‑drawn arrows connecting panels to show lifecycle flow.
- Doodle icons: pencil (create), meter (score), wrench (improve), clock (schedule), portfolio tiles (portfolio).
- Accents: use `#EA5B39` for headings/underlines/arrows; use `#F7B02F` for callouts/tags; default black for text.

## Content (Authoritative, Current)

### Title
- Epic Studio — Rovo Agent Cheat Sheet
- Subline: End‑to‑end Epic lifecycle: Create → Evaluate → Auto Score & Recommend → Improve → Analyze Progress → Analyze Portfolio

### Panel 1 — What Is the Agent
- A disciplined, Epic‑only orchestration agent for Jira.
- Augments product judgment; ownership stays human.
- Consent‑first; pre‑flight checks; copy‑ready outputs.

### Panel 2 — Capabilities (End‑to‑End)
- Create with discipline: guide raw idea to a clear, complete Epic.
- Evaluate with objectivity: quality score 0–100 + targeted recommendations.
- Automatic scoring & recommendations: consistent, fast, consent‑first.
- Improve existing Epics: precision rewrites with before/after.
- Analyze Epic progress: manual and automatic completeness & momentum.
- Analyze Epic portfolio: quality distribution, ready rate, duplicates/overlaps.

### Panel 3 — Active Scenarios (Aligned with “Epic Studio/”)
- Default (fallback)
- Créer une Epic de qualité
- Évaluer la qualité d’une Epic
- Améliorer une Epic existante
- Analyser avancement Epic (manuel)
- [AUTO] Analyser avancement Epic (automation‑only)
- [AUTO] Scoring & évaluation d’une Epic (automation‑only)
- Analyser portefeuille Epics

### Panel 4 — How to Use (Manual)
- Create: “Create a high‑quality Epic from this idea…” → outputs Markdown ready to copy.
- Evaluate: “Evaluate Epic `EPIC-123` and give a 0–100 score + recommendations.”
- Improve: “Propose concise rewrites for weak sections in `EPIC-123` (before/after).”
- Progress: “Analyze progress for `EPIC-123` and propose 3 next actions.”
- Portfolio: “Review these 10 Epics; summarize quality and prioritize improvements.”

### Panel 5 — How to Use (Automation, Jira Automation)
- Nightly scoring & recommendations (scheduled):
  - Trigger: cron `0 2 * * *`
  - Scope (JQL): `issuetype = Epic AND project IN (ABC, DEF) AND statusCategory != Done`
  - Actions (non‑destructive): evaluate → score → recommend → add comment → optional set field `Epic Quality Score`
- Progress analysis on transition (event‑based):
  - Trigger: status → “Ready for Review” (issuetype: Epic)
  - Actions: run completeness analysis → add comment → optional set field `Progress Completeness` → label `needs-changes` if below threshold

### Guardrails & Trust (Sketch Tag)
- Pre‑flight first; explicit consent for actions.
- Safe fallback: copy‑ready outputs; never promise async.
- Epic‑only scope; redirect story breakdown to Product Backlog Studio.
- Automation guardrails: whitelisted projects, scoped triggers, non‑destructive defaults, audit logs.

### Data Signals (Used in Progress Analysis)
- Dates: created/resolution/start/due; age & cycle time.
- Status/time in status; To Do / In Progress / Done.
- Children: total/done/in progress; completion %, reopens, churn.
- Links: blocked by / blocks / relates; flagged.
- Changelog: last transition/activity; transitions last 14 days; scope change.
- Summary: On Track / At Risk / Late + confidence.

### Quick Examples (One‑liners)
- Manual: “Evaluate `EPIC-123` (normal detail) → score + 3 recos.”
- Manual: “Improve `EPIC-123` → rewrite objectives to be measurable.”
- Automation: `intent=rovo:automation:epic_score_v1 key=EPIC-123`
- Automation: `intent=rovo:automation:epic_progress_v1 url=https://jira/.../browse/EPIC-123`

### KPI Callouts (Small Tags)
- Epic quality score (avg, distribution)
- Ready rate (% passing pre‑validation)
- Lead time (idea → Ready)
- Duplication/overlap avoided

## Hand‑Drawn Styling Directions
- Use imperfect strokes for boxes/lines/arrows; rounded corners; light shadows.
- Headings in `#EA5B39` with a brush underline; callouts/tags in `#F7B02F`.
- Icons are minimal: pencil, gauge, wrench, clock, tiles; outline only.
- Watermark placement: center page; scale ~60–70% width; opacity 10–12%; behind all content.
- Keep text blocks ≤ 6 lines per panel; line length ≤ 11–14 words.

## Production Instructions (Tool)
- Import watermark from `Brand/epic_studio_logo_icon_256x240.svg`.
- Compose panels with generous spacing; avoid edge crowding.
- Export PDF (A4 portrait, 300 DPI, embedded fonts).
- Verify color values exactly: `#EA5B39`, `#F7B02F`, `#000000` on snow white.

## Optional Footer (Small)
- “Epic Studio — Pilot: 3 domains, 5 KPIs, 6–8 weeks. Consent‑first, copy‑ready.”

---

## One‑Shot Command‑Style Prompt (for Generators)

“Create a one‑page A4 portrait PDF cheat sheet titled ‘Epic Studio — Rovo Agent Cheat Sheet’ in a hand‑drawn/written visual sketch style on a snow white background. Use `#EA5B39` for headings/underlines/arrows, `#F7B02F` for callouts/tags, black for body text. Place `Brand/epic_studio_logo_icon_256x240.svg` centered as a watermark at 10–12% opacity behind content.

Panels and bullets:
1) What is the agent: Epic‑only orchestration; consent‑first; pre‑flight; copy‑ready outputs.
2) Capabilities end‑to‑end: Create; Evaluate (0–100 + recos); Automatic scoring & recommendations; Improve existing (before/after); Analyze Epic progress (manual+automatic completeness); Analyze Epic portfolio (quality distribution, ready rate, duplicates/overlaps).
3) Active scenarios (French labels): Default; Créer une Epic de qualité; Évaluer la qualité d’une Epic; Améliorer une Epic existante; Analyser avancement Epic (manuel); [AUTO] Analyser avancement Epic; [AUTO] Scoring & évaluation d’une Epic; Analyser portefeuille Epics.
4) How to use (manual): short commands for create, evaluate, improve, progress, portfolio.
5) How to use (automation, Jira Automation): nightly scoring (cron `0 2 * * *`, JQL scope); progress analysis on transition to ‘Ready for Review’; actions are non‑destructive.

Add a guardrails tag (pre‑flight, consent, fallback, scope, audit). Add a data signals tag (dates, status/time, children %, links, changelog, summary). Include KPI callouts (quality score, ready rate, lead time, duplication avoided). Use doodle icons (pencil, meter, wrench, clock, tiles). Export as PDF with exact colors and embedded fonts.”