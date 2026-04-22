# Worked Example — Property Management, Lease Abstraction

Draft. A filled-out candidate thesis brief showing what
`hvl-studio:generate-thesis` produces from a single-paragraph starting
input.

## Starting Input

> "Mid-market property managers (operating 500–5,000 units) still
> abstract leases by hand. Every renewal cycle means someone with a
> PDF and a spreadsheet pulling out rent escalators, option windows,
> co-tenancy clauses, and use restrictions. The same clauses show up
> over and over. Feels like a workflow waiting to be automated."

Source: voice-note transcript, 2026-04-10.

## Generated Candidate

File: `thesis-backlog/2026-04-21-property-management-lease-abstraction.md`

```markdown
---
title: "Property Management — Lease Abstraction"
date: 2026-04-21
status: candidate
template_complete: false
agent_validated: false
leadership_approved: false
approved_by: []
---

# Property Management — Lease Abstraction

## Domain
- **Industry**: Commercial and multifamily property management
- **Persona**: Mid-market operator, 500–5,000 units under management
- **Workflow band**: Lease abstraction and renewal cycle data extraction

## Disruption Thesis (Why Now)
Lease abstraction in mid-market property management is a manual,
high-repetition workflow where the same clauses — rent escalators,
option windows, co-tenancy provisions, use restrictions — recur
across hundreds of leases per portfolio. Today, this is done by
associates or outsourced teams with a PDF and a spreadsheet. Large
operators have abstraction teams or contracts with specialist
providers; mid-market operators do not, and the work piles up around
renewal cycles.

Generative AI for document extraction has crossed the accuracy
threshold where a vertical AI product could plausibly do the first
pass well enough that the associate only reviews and corrects. This
is a narrow, high-volume, recurring workflow with clear buyer pain at
renewal time — the kind of shape HVL's mini-cycle model is built for.

## HVL Fit Criteria
- [ ] **Vertical AI wedge** — [leadership to fill]
- [ ] **Viable buyer** — [leadership to fill]
- [ ] **Path to $1K MRR in 12 weeks** — [leadership to fill]

## Key Questions to Answer
1. **Workflow**: What is the current workflow — who does it, how often,
   with what tools?
2. **Motivation**: Is the driver perceived *pain* (costly, frustrating,
   error-prone) or an *automation opportunity* (routine job nobody has
   thought to automate)? What's the evidence?
3. **Buyer**: Who pays, how much, and why would they pay for HVL's
   shape of product?
4. **Competitive gap**: Who else is trying to solve or automate this,
   and why haven't they won?
5. **Disproof**: What evidence would kill this thesis?

## Known Contacts
| Name | Role / Company | Relationship | Intro Path |
|------|----------------|--------------|------------|
|      |                |              |            |

## Raw Inputs
- Voice-note transcript, 2026-04-10 — `[pointer to transcript]`
```

## What to notice

- Industry, persona, workflow band — all three filled, all specific
  (not "real estate" / "managers" / "lease work")
- Disruption Thesis grounds both the *what* (manual, recurring,
  vertical) and the *why now* (AI extraction accuracy crossed the
  usefulness line)
- HVL Fit Criteria unchecked, explainers blank — leadership job
- Key Questions left as the five template defaults — no per-brief edits
- Known Contacts empty table — leadership fills before sprint-ready
- Raw Inputs links back to the source material

## If a different angle is wanted

Same starting input, different cuts — each would be a separate run of
the skill with a different field pinned:

- Same persona, different workflow band: "Property Management —
  Tenant Screening and Onboarding"
- Adjacent industry: "Commercial Real Estate Brokerage — Lease
  Abstraction for Negotiation Support"

The skill produces one candidate per run on purpose. Re-running keeps
each candidate sharply scoped.
