# Candidate Fields — `hvl-studio:generate-thesis` Output

Draft. For Trevor review before the skill ships.

A candidate thesis brief is a **partial** thesis brief. It fills the
fields that can be written from a desk-research pass alone. It leaves
every field that needs leadership judgement or market validation to
the curation agent.

## Reference: full thesis brief template

Source: `docs/brainstorms/2026-04-16-thesis-brief-template-brainstorm.md`

Full template fields:

**Frontmatter**
- `title` — one-line thesis name
- `date`
- `status` — `draft | validated | sprint-ready | retired`
- `template_complete: bool`
- `agent_validated: bool`
- `leadership_approved: bool`
- `approved_by: [names]`

**Body**
- **Domain** — Industry, Persona, Workflow band (three required fields)
- **Disruption Thesis (Why Now)** — 1–2 paragraph narrative
- **HVL Fit Criteria** — three checkboxes with per-item explainers
  (Vertical AI wedge, Viable buyer, Path to $1K MRR in 12 weeks)
- **Key Questions to Answer** — 5 defaults, editable per brief
- **Known Contacts** — table (name, role/company, warm/cold, intro path)
- **Raw Inputs** — links to source material

## What `generate-thesis` fills

| Field | Filled? | Note |
|---|---|---|
| `title` | ✅ | Derived from Industry + Workflow band (e.g., "Property Management — Lease Abstraction") |
| `date` | ✅ | Today's date |
| `status` | ✅ | Set to `candidate` (see open question below) |
| `template_complete` | ❌ | Left `false`; curation agent sets when structured |
| `agent_validated` | ❌ | Left `false` |
| `leadership_approved` | ❌ | Left `false` |
| `approved_by` | ❌ | Empty list |
| **Industry** | ✅ | Required |
| **Persona** | ✅ | Required |
| **Workflow band** | ✅ | Required |
| **Disruption Thesis (Why Now)** | ✅ | Draft narrative, 1–2 paragraphs; curation agent rewrites with leadership voice during structuring |
| **HVL Fit Criteria** | ❌ | All three checkboxes left unchecked; explainers left blank. Curation agent and leadership fill during validation. |
| **Key Questions to Answer** | ❌ | Left with the five template defaults, unedited |
| **Known Contacts** | ❌ | Empty table; leadership fills before brief goes sprint-ready |
| **Raw Inputs** | ✅ | Link back to the original input (paragraph, article URL, transcript reference) |

## Candidate example frontmatter

```yaml
---
title: "Property Management — Lease Abstraction"
date: 2026-04-21
status: candidate
template_complete: false
agent_validated: false
leadership_approved: false
approved_by: []
---
```

## New `candidate` status — approved

The April 16 brainstorm defined the status lifecycle as:

> `draft → validated → sprint-ready → retired`

The thesis brief lifecycle adds `candidate` as the state before `draft`:

> `candidate → draft → validated → sprint-ready → retired`

Reason: `draft` implies leadership has at least skimmed the brief. A
candidate is a machine-generated proposal that no human has reviewed
yet. Conflating them means the curation agent cannot tell which briefs
still need a structuring pass.

**Changes to flag downstream:**
- Unit 1 (thesis brief template) — lifecycle docs need updating
- Unit 2 (thesis backlog structure) — directory README updates
- Unit 8 (thesis curation agent) — the agent's first structuring action
  promotes `candidate → draft`

Approved by Trevor 2026-04-21 ("Worth testing at least").

## Worked example

See `worked-example-property-management.md` for a filled-out candidate.
