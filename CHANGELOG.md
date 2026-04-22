# Changelog

## 0.2.0 — 2026-04-22

- `research-area` skill added. Copies CI Toolkit
  `/research-opportunity` and customizes for mini-cycle context —
  internal audience, shorter output, no client-alignment framing.
  Produces a Thesis Brief via the co-located template.
- `skills/research-area/templates/thesis-brief.md` added. One-page
  template filled by the skill. Establishes the process/shape split
  pattern for subsequent template-producing skills.
- Three helper prompts added under `prompts/`: `industry-overview.md`,
  `operations-mapping.md`, `competitive-analysis.md`. Extracted from
  the Prompts Library Google Sheet per the 2026-04-21 tool
  consolidation decision log (rows 10, 11, 15). Used automatically by
  `generate-thesis` during its desk-research step; also usable
  standalone by humans.
- Default output location for Thesis Briefs set to the shared
  "Thesis Briefs" Drive folder (via Drive MCP), with local-file
  fallback if the Drive call fails. Folder ID is temporary pending a
  team decision on long-term storage structure.

## 0.1.0 — 2026-04-21

- Plugin skeleton created (manifest, directory layout, operator
  context docs)
- `generate-thesis` skill landed (moves a starting input — paragraph,
  link, transcript, market observation — into a candidate thesis brief
  in the backlog)
- Placeholder directories for `agents/`, `prompts/`, `templates/`

## Remaining for 0.3.0+

- Remaining discovery/research skills copied from CI Toolkit
  canonical: `research-market`, `analyze-interview`,
  `synthesize-interviews`, `social-scan`
- Prototyping skills copied from CI Toolkit: `synthesize-demo`,
  `changelog`, `prd-lite`, `tasks`
- Sprint orchestration skills: `thesis-add`, `thesis-refresh`,
  `sprint-kickoff`, `sprint-status`, `sprint-debrief`, `gate-check`,
  `problem-case-analyze`
- Thesis curation agent
- Gate detection agent + venture data contract
- Remaining Prompts Library helpers (wedge-generator,
  ai-opportunity-identifier, wedge-entry-analysis,
  competitive-intelligence, buying-process, strategy-narrative)
- Remaining Problem Identification Sprint templates:
  `problem-case`, `pitch-format`, `decision-rubric`
- Team decision on central storage for thesis briefs (currently
  hardcoded to a single Drive folder ID in `research-area`)
