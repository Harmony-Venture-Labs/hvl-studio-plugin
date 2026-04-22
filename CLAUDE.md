# HVL Studio Plugin — Operator Context

Context for Claude instances operating inside this plugin.

## What this plugin is for

The HVL mini-cycle engine runs two sprints before a product ships:

1. **Problem Identification Sprint** (pre-Phase 1, 3–4 days) — the
   team picks the problem the next mini-cycle will solve. Output: a
   Problem Case.
2. **Idea Generation Sprint** (Phase 1, ~11 days) — the team picks
   the AI wedge to build for that problem. Output: a wedge plus a
   Phase 2 Build plan.

Upstream of both sits a **thesis backlog** of 4–8 sprint-ready
briefs, continuously curated by leadership. The `generate-thesis`
skill and the `thesis-curation` agent feed and maintain it.

Downstream of both sits **Phase 2 Build** (4 weeks) and **Phase 2
Growth** (8 weeks), then the revenue-gated Phases 3–5.

## Key constraints

- **Problem-level vs. solution-level matters.** Problem Identification
  Sprint is problem-level only — no solutions. Idea Generation Sprint
  moves to solution-level. Skills and prompts are scoped to one or the
  other; mixing them contaminates output.
- **Collaborative artifacts stay in Drive.** Dashboards, runbooks, and
  interview scripts are Google Drive assets the team edits together.
  Plugin skills reference them by URL; they're not embedded.
- **Skills are copied per project, not shared.** HVL Studio owns its
  own copies of CI Toolkit skills, customized for mini-cycle context.
- **One active mini-cycle at a time.** The plugin does not need to
  handle concurrent sprints.

## Namespaces and conventions

- All skills invoke as `/hvl-studio:<skill-name>`
- Skill names are verb-first (e.g., `generate-thesis`, not
  `thesis-generate`) — humans think in verbs
- Each skill is a directory under `skills/` with `SKILL.md` inside;
  heavy content goes in `references/`, `templates/`, `scripts/`,
  `assets/` subdirs (Compound Engineering plugin pattern)
- Each agent is a single `.md` file under `agents/` with YAML
  frontmatter

## When a skill or agent is added

1. Follow the Compound Engineering plugin pattern exactly — copy the
   shape of an existing skill (`skills/generate-thesis/SKILL.md`) or
   agent when adding a new one.
2. Name verb-first.
3. For Phase 1-only prompts and skills, include a note at the top of
   the file restricting use to Phase 1 context.
4. Bump the version in `.claude-plugin/plugin.json` and add a line to
   `CHANGELOG.md`.

## Related projects

- **Workspace repo:** `~/Projects/hvl-studio/` — docs, plans,
  meetings, tooling audit. The plugin is a distinct repo.
- **CI Toolkit:** `~/Projects/ci-toolkit/` — canonical source for the
  5 discovery/research skills and 4 prototyping skills. HVL Studio
  copies these and customizes for mini-cycle context.
- **Venture Performance Dashboard:** separate project — consumes the
  venture data contract emitted by this plugin's `gate-detector`
  agent.
- **Marketing Brain:** `~/Projects/hvl-marketing-brain/` — sibling
  plugin in the `hvl-tools` marketplace; serves Phase 2 Growth, not
  idea identification.
