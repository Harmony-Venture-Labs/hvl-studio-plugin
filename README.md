# HVL Studio

Claude Code plugin for running HVL's internal mini-cycle engine — the
process that takes a raw idea from leadership through a 3–4 day
Problem Identification Sprint, an 11-day Idea Generation Sprint, and
into a mini-cycle that ships a product.

This plugin holds the skills, agents, templates, and helper prompts
the team uses. Collaborative sprint artifacts (sheets, docs) stay in
Google Drive and are referenced by name, not embedded.

## Namespace

All commands invoke as `/hvl-studio:<name>`.

## Installation

Install via the `hvl-tools` marketplace:

```
/plugin marketplace add Harmony-Venture-Labs/hvl-tools
/plugin install hvl-studio@hvl-tools
```

## Status

**0.2.0 — in progress.** Skills so far: `generate-thesis` (populate
the thesis backlog from a raw input) and `research-area` (produce a
Thesis Brief grounded in market research). Helper prompts for
industry overview, operations mapping, and competitive analysis are
callable by skills and usable standalone.

Remaining skills land as CI Toolkit Part 2 ships (copies) and the
orchestration commands get built out. See `CHANGELOG.md` for the
version history and `CLAUDE.md` for operator context.

## Layout

- `skills/` — user-invokable skills (`/hvl-studio:<name>`)
- `agents/` — background / task agents invoked via `Task`
- `prompts/` — reusable helper prompts (Industry Overview, Operations
  Mapping, etc.)
- `templates/` — markdown templates (Thesis Brief, Problem Case, Pitch
  Format, Decision Rubric)

## Sources

- Project docs and plans: `~/Projects/hvl-studio/` (the workspace repo,
  separate from this plugin repo)
- Canonical skill source: CI Toolkit (`~/Projects/ci-toolkit/`) — HVL
  Studio copies and customizes per the duplicate-skills-per-project
  principle
