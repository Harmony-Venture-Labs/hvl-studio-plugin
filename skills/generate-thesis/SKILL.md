---
name: generate-thesis
description: Turn a starting input — a paragraph, article link, voice-note transcript, or market observation — into a candidate thesis brief in the HVL Studio thesis backlog. Use when surfacing a new idea for the backlog, processing a note from Shegun or Trevor, or working through an article or market signal. Triggers on "generate thesis", "add to backlog", "turn this into a thesis", or when leadership shares raw ideation input.
argument-hint: "[paragraph, article URL, transcript path, or market observation]"
---

# Generate a Thesis Candidate

Take a starting input and write one candidate thesis brief into the
HVL Studio thesis backlog. A candidate is a partial thesis brief —
enough for the curation agent to validate and leadership to review.

This skill creates candidates. The thesis curation agent validates
them, surfaces new ones proactively, and keeps them current — those
responsibilities belong to the agent, not this skill.

This skill operates at the **problem level only**. It never proposes
solutions, features, or product shapes. Solution-level work belongs to
the Phase 1 Idea Generation Sprint, not the backlog.

One input → one candidate. If leadership wants a different angle on
the same input (different persona, different workflow band, adjacent
industry), re-run the skill and pin the field you want to change.

## Input

<raw_input> $ARGUMENTS </raw_input>

**If the input above is empty**, ask: "What's the starting input? Paste
a paragraph, a link, a transcript path, or a market observation. You
can also pin any of industry, persona, or workflow band up front."

Do not proceed until input is provided.

## Step 1: Read the Input

Extract what's available. Do not ask for anything you can infer.

Extract if present:
- Industry hint (e.g., "property management", "financial services")
- Persona hint (e.g., "mid-market operator", "compliance officer")
- Workflow hint (e.g., "lease abstraction", "vendor onboarding")
- Why-now signal (regulatory change, technology inflection, funding
  activity, observed pain)
- Link or pointer to the original input

If the user pinned industry / persona / workflow band up front, carry
those through — do not second-guess them.

## Step 2: Desk Research

**Required before writing the candidate — invoke all three helper
prompts, in order:**

1. `hvl-studio/prompts/industry-overview.md` — populates market
   size, company count, size distribution, growth rate, and
   geography for the candidate's Domain section.
2. `hvl-studio/prompts/operations-mapping.md` — sketches the
   end-to-end workflow chain that grounds the disruption thesis.
3. `hvl-studio/prompts/competitive-analysis.md` — surfaces
   incumbent software, common complaints, and market gaps for the
   Why Now section.

**Use web search when executing each prompt — do not answer from
training knowledge alone.** The purpose of these calls is a sourced
"as-of" check that leadership can trust when reviewing the
candidate. If a prompt returns thin or low-confidence results, note
the gap in Open Questions rather than papering over it with
assumptions.

`hvl-studio:research-area` remains available but is **optional** at
this stage — invoke it only if the three prompts together leave
critical gaps that a full Thesis Brief would close. Full Thesis
Briefs are the job of Problem Identification Sprint Day 1 and Idea
Generation Sprint Week 1, not candidate capture.

Goal: understand the industry well enough to write the three domain
fields (industry, persona, workflow band) and a draft disruption
thesis, with every claim traceable to a source or flagged as an
open question.

**Do not use** (Phase 1 / Idea Generation Sprint only):
- Wedge Product Generator
- AI Opportunity Identifier
- Wedge Entry Analysis
- Competitive Intelligence
- Buying Process

If research pulls toward a solution shape, stop. Bring it back to the
problem.

## Step 3: Write the Candidate

Write a markdown file to the thesis backlog directory (placeholder
path: `thesis-backlog/` — canonical path comes from Unit 2 of the
pre-cycle plan).

File name: `YYYY-MM-DD-<industry-slug>-<workflow-slug>.md`

Fill these fields only (per `references/candidate-fields.md`):
- Frontmatter: `title`, `date`, `status: candidate`, all gate flags
  `false`, `approved_by: []`
- Domain: Industry, Persona, Workflow band (required, all three)
- Disruption Thesis (Why Now): 1–2 paragraph narrative draft, grounded
  in the desk research
- Raw Inputs: link back to the original input (URL, transcript path,
  "voice note on YYYY-MM-DD" — whatever fits)

Leave these empty (curation agent and leadership fill later):
- HVL Fit Criteria — all three boxes unchecked, explainers blank
- Key Questions to Answer — leave the five template defaults
- Known Contacts — empty table

## Step 4: Report

Print a short summary:

> Generated candidate: [Industry — Workflow]
> Saved to: `thesis-backlog/YYYY-MM-DD-<slug>.md`
>
> Next step: curation agent promotes `candidate → draft` during
> validation.

## Constraints

**MUST:**
- Fill all three domain fields (industry, persona, workflow band)
- Write a draft disruption thesis grounded in desk research
- Include the Raw Inputs pointer back to the original material
- Save one file per run into the backlog directory
- Set `status: candidate` on the file

**MUST NOT:**
- Produce any solution-level output (product ideas, feature lists,
  technical approach, pricing)
- Run any Phase 1 / Idea Generation Sprint prompt (Wedge Product
  Generator, AI Opportunity Identifier, Wedge Entry Analysis,
  Competitive Intelligence, Buying Process)
- Fill HVL Fit Criteria, Key Questions, or Known Contacts — those
  belong to the curation agent and leadership
- Set `template_complete`, `agent_validated`, or `leadership_approved`
  to `true`
- Invent contacts or cite sources not in the desk research
- Propose more than one candidate per run (re-run the skill with a
  pinned field if a different angle is wanted)

## Worked example

See `references/worked-example-property-management.md` for a complete
candidate. See `references/candidate-fields.md` for the full field
spec matched against the Unit 1 thesis brief template.
