# Product Management Studios — Rovo AI Agents

Purpose
- This repository hosts a set of Atlassian Rovo AI agents designed for Product Management workflows.
- Current studios: Epic Studio (implemented) and Product Backlog Studio (present and evolving). More studios will be added over time.

Repository Layout
- Each Studio folder (e.g., `Epic Studio`, `Product Backlog Studio`) represents an agent.
- Within a Studio, content is organized by scenarios. Each scenario has its own folder named after the scenario.
- Studio‑level behavior and guardrails are defined in `behaviour.md` inside the Studio folder.

Scenario Folder Structure
- `trigger.md`: The scenario prompt and trigger format (intent, required inputs, examples).
- `instructions.md`: The scenario’s objective, evaluation/processing logic, output format, and guardrails.
- `skills.md`: The actions/capabilities the agent can perform across the Atlassian ecosystem (e.g., create, edit, comment). `NO_SKILLS` indicates the scenario has no external action capability.

Notes
- Documentation in `Docs/` provides blueprint and agent guidance and may reference scenarios and flows across studios.
- As new studios and scenarios are introduced, they will follow the same folder and file conventions for consistency.