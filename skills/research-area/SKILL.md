---
name: research-area
description: Research a thesis area from the HVL Studio backlog and produce a Thesis Brief grounded in market data, investment activity, comparable companies, and technical feasibility. Use at Day 1 of a Problem Identification Sprint to understand the space, during early Week 1 of an Idea Generation Sprint for desk research before interviews, or when the generate-thesis skill calls this skill for industry grounding. Internal-only — no client-facing polish.
argument-hint: "[Thesis Title, or path to a thesis brief file]"
---

# Research a Thesis Area

Research a thesis area from the HVL Studio backlog and produce a
Thesis Brief. This skill gathers market data, investment activity,
comparable companies, and inflection points, then fills the Thesis
Brief template.

The brief is internal — no client-facing polish required. Target
one page; extend a section only when the research turned up more
detail than fits and dropping that detail would cost a reader
something they need to judge the thesis.

## Input

<raw_input> $ARGUMENTS </raw_input>

**If the input above is empty**, run Step 1 below to gather context.

## Step 1: Basic Information

Ask:

**"What's the Thesis Title? (A short name for the thesis —
industry plus angle, for example 'Property Management — AI Lease
Abstraction'.) What's the one-line disruption thesis? If a thesis
brief already exists, paste the path instead."**

Capture:
- Thesis Title
- Disruption thesis (one line)
- Industry
- Candidate persona (if known)
- Candidate workflow band (if known)

## Step 2: Workflow Information

Ask:

**"What workflow might we be improving or automating? Walk me
through the key steps, who performs it today, and roughly how long
it takes. If you're not sure, say so — I'll research typical
workflows for this industry."**

Capture whatever the user provides. If they say they're unsure,
acknowledge and move on — workflow research is part of the Research
Phase. Do not treat this as "TBD"; it is a standard branch of the
process.

## Step 3: Known Players

Ask:

**"Are there any companies already on your radar — competitors,
adjacent players, or startups in this space?"**

## Step 4: Output Location

**Default: save as a Google Doc in the HVL "Thesis Briefs" folder
on Drive.** The folder is shared across the leadership team so
everyone can see briefs as they land.

Folder ID (as of 2026-04-22): `12WS8E0z9MV887dg87cy8HCEoAXSD26_p`.
Folder URL: https://drive.google.com/drive/folders/12WS8E0z9MV887dg87cy8HCEoAXSD26_p

**Note:** This folder ID is temporary — the team is deciding on a
longer-term storage structure. Keep using this folder until the
decision lands.

### If the skill was called by `generate-thesis`

Honor whatever output location `generate-thesis` passed in. Do not
re-ask the user.

### Standalone use — Drive path (default)

1. Ask the user: **"Save to the shared Drive folder (default) or a
   local file?"** If the user says Drive or gives no answer, use
   Drive.
2. Create a Google Doc via
   `mcp__claude_ai_Google_Drive__create_file`:
   - `mimeType: "text/plain"` (the Drive MCP auto-converts plain
     text content to a Google Doc; Markdown formatting comes
     through)
   - `title: "<YYYY-MM-DD> — <Thesis Title> — Thesis Brief"`
   - `parentId: "12WS8E0z9MV887dg87cy8HCEoAXSD26_p"`
   - `content`: the filled template, base64-encoded
3. After the Doc is created, return its `viewUrl` to the user.

### Drive failure fallback

If the Drive call fails for any reason (authentication, network,
folder not accessible, MCP not connected):

1. Save the brief locally. Default path:
   `~/Desktop/<thesis-title-slug>-thesis-brief.md`. Ask the user to
   confirm the path before writing.
2. Tell the user:
   **"Drive save failed — brief saved locally at <path>. Please
   let Trevor know so he can investigate."**

### Explicit local request

If the user asks for a local save:

1. Suggest `~/Desktop/<thesis-title-slug>-thesis-brief.md` as a
   default path.
2. Write Markdown to the confirmed path.

---

## Research Phase

After collecting context, conduct research using web search.

### Workflow Research (if not provided by user)

If the user didn't provide workflow details, research typical
workflows for this problem or industry:

1. Identify 3–5 key workflows that would be automated or improved
2. Document typical steps for each workflow
3. Research who performs these workflows today (roles, titles)
4. Estimate time spent based on industry sources
5. **Estimate cost for each workflow** — research hourly rates for
   the roles involved, calculate annual cost per workflow (hourly
   rate × time), and sum to a per-customer total
6. Mark these as "research-derived" in the output
7. Add "Validate workflow assumptions with the team" to Open
   Questions

### Market Analysis

Research and document:

1. **Industry market size (US)** — total addressable market with
   source
2. **Target segment size** — the specific demographic or use case
   being addressed (for example "households with $30–100M in
   assets" or "mid-market manufacturers with 100–500 employees")
3. **Growth rate** — CAGR with source, and whether the market is
   growing, stable, or shrinking

Note: per-workflow cost estimates live in Workflow Analysis. Market
Analysis uses the per-customer total from that section to calculate
total addressable labor cost.

### Investment Landscape

- Recent funding activity (companies, rounds, amounts, investors)
- Mergers and acquisitions in the space
- What investor thesis does this funding suggest?

For each funding round, verify and record:
- Exact amount (not rounded)
- Exact date (month and year)
- Round type (Seed, Series A/B/C, or extension)
- Lead investors vs. participants
- Cross-reference at least two sources when possible

### Comparable Companies

Research 4–6 companies working on this problem or adjacent
problems. For each, find:
- What they do (one-sentence description)
- Total funding raised
- Target customer segment
- Key differentiator — how they position against alternatives

### Inflections

State changes that make this opportunity possible now (the
"why now?"). Technology breakthroughs, regulatory changes, platform
shifts. These are discontinuities, not gradual changes.

### Trends

Linear forces that accelerate adoption or growth (the tailwind).
Market dynamics, demographic shifts, behavioral changes. These
unfold over time and are more predictable than inflections.

### Technical Feasibility

Assess whether this is technically feasible with current AI and
automation capabilities, and what it would take to ship and adopt.

**Overall rating:**

- **High** — Core capabilities exist in production today (proven
  APIs, mature ML models, established integration patterns).
  Primary risk is integration and product execution, not technical
  invention.
- **Medium** — Key components exist but require significant
  customization, fine-tuning, or novel combination. Some technical
  uncertainty.
- **Low** — Requires capabilities that don't exist yet or are only
  in research stages. High technical risk.

Provide the rating with a brief explanation of what's proven vs.
uncertain.

**Then assess each of these dimensions:**

1. **Dependencies** — What external systems, APIs, data sources, or
   third-party services must be in place? Which are mature, which
   are not? What happens if a dependency breaks or changes terms?

2. **Implementation friction** — What's the realistic build effort
   from zero to a usable prototype? Where are the hardest
   engineering problems (data quality, model accuracy, latency,
   integration complexity)? What would a team need to prove out
   before committing?

3. **Security and compliance blockers** — What data sensitivity,
   regulatory, or audit requirements apply (HIPAA, SOC 2, GDPR,
   industry-specific rules)? Are there blockers that would prevent
   deployment in the target segment? Where do incumbents sit on
   compliance today?

4. **Change-management risk** — How hard is it for the target user
   to adopt this? What existing workflows or tools would be
   displaced? Who inside the buyer organization might resist, and
   why? Is there a version that ships alongside current tools vs.
   one that forces replacement?

Summarize each dimension in 2–4 sentences grounded in research,
not speculation. Flag anything that downgrades the overall rating.

---

## Research Guidelines

### Quality Standards

1. **Cite sources.** Every data point should have a source cited
   inline.

2. **Flag uncertainty.** Note when data is:
   - Estimated or projected (vs. reported actuals)
   - From a single source only
   - Older than 12 months
   - Unable to be independently verified — move unverifiable claims
     to Open Questions rather than stating as fact

3. **Be directional, not exhaustive.** This is a screening
   document. "Good enough to decide" is the bar.

4. **Prioritize recency.** Prefer data from the current and prior
   year. Note when using older data.

5. **Note gaps.** If you can't find data, say so explicitly and add
   to Open Questions.

6. **Be precise about metrics.** When citing figures, clarify
   exactly what's being measured:
   - Distinguish between similar metrics (for example "revenue" vs.
     "funding raised" vs. "valuation"; "market size" vs. "total
     addressable market" vs. "assets under management")
   - Specify the entity being measured (single company, industry
     segment, total market)
   - Include "as of" dates for company-specific metrics that change
     rapidly (customers, employees, assets under management)

7. **Match thresholds to sources.** Different sources use different
   definitions for wealth segments, company sizes, and so on:
   - Note the exact threshold each source uses (for example "$30M+
     net worth" vs. "$50M+ financial assets" vs. "$50M+ investable
     assets")
   - Do NOT apply one source's threshold to another source's
     figures
   - If combining data from multiple sources, explicitly note
     definitional differences
   - When in doubt, quote the source's exact language rather than
     paraphrasing

8. **Prefer primary sources.** When available, use:
   - Company press releases and investor announcements
   - Regulatory filings
   - Research firm reports
   - When using secondary sources (news articles, aggregators),
     verify key figures against primary sources when possible

9. **Verify research attributions.** When citing academic research
   or industry reports:
   - Confirm the institution or organization that published the
     research (for example "University of Chicago," not "Stanford")
   - Verify author names if mentioned
   - Check that the paper title and findings match the source
   - Link directly to the paper (arXiv, journal, or official report
     URL) when possible

### Research Depth

Search thoroughly, but report honestly. It is far better to document
fewer findings than to stretch or fabricate data.

- **Funding activity:** search for recent rounds (last 24 months)
  in both direct competitors and adjacent spaces. If the space is
  nascent and funding activity is limited, say so — that's a
  finding. **For each funding round, verify the amount and date
  against the company's own press release or blog post** — do not
  rely solely on news aggregators or databases, which often have
  errors. If you cannot find a primary source, note this
  uncertainty.
- **Comparable companies:** look for direct competitors, adjacent
  players, and companies solving similar problems in other
  industries. If few exist, note whether this signals white space
  or a warning sign.
- **Inflections and trends:** identify what's genuinely relevant.
  Two strong inflections are better than five weak ones.

When research yields limited results, document:
1. What you searched for
2. What you found (or didn't find)
3. What that absence might indicate

---

## Generate the Thesis Brief

After completing research, generate the Thesis Brief.

**Read `templates/thesis-brief.md`** (co-located in this skill).
Copy the structure and fill in each `{{placeholder}}` with your
research findings.

Target one page. If a section genuinely needs more room because the
research turned up more detail than fits, and cutting that detail
would drop something a reader needs to judge the thesis, extend
that section rather than truncate. Do not add sections the template
doesn't have. Do not pad sections just to fill space.

---

## Verification Pass

Before saving, review the brief for common errors:

1. **Funding data:** do all dates, amounts, and round types match
   your sources exactly? Check for rounding errors and date
   approximations.

2. **Metric consistency:** are you comparing like-for-like figures?
   Ensure you haven't conflated different types of metrics (for
   example market size vs. company revenue, total wealth vs.
   assets under management).

3. **Unverified claims:** are any statistics presented without a
   source? Either find a source or move the claim to Open
   Questions.

4. **Data freshness:** for company-specific metrics, have you noted
   the "as of" date? Fast-growing companies may have significantly
   different figures within months.

5. **Source quality:** are key claims supported by primary sources,
   or only secondary reporting?

6. **Per-workflow cost math:** does the cost breakdown in Workflow
   Analysis add up correctly? Are hourly rate assumptions
   documented? Does Market Analysis use the per-customer total from
   the workflow section?

7. **Workflow sourcing:** if workflows are research-derived (not
   from user), is this clearly noted? Is validation added to Open
   Questions?

---

## Save and Confirm

Save the Thesis Brief to the location chosen in Step 4.

After saving, tell the user:

---

## Thesis Brief Created

**Thesis Title:** [Name]
**Saved to:** `[Drive URL or file path]`

### Summary
- **Industry:** [Industry]
- **Market size (US):** [Top-line figure]
- **Target segment:** [Who specifically]
- **Total addressable labor cost:** [Calculated figure]
- **Growth:** [X% CAGR — growing / stable / shrinking]
- **Comparable companies:** [X] identified
- **Technical feasibility:** [High / Medium / Low]
- **Key inflection:** [Most significant one]

### Research Notes
- **Workflows:** [User-provided / Research-derived — note which]
- **Data gaps:** [Any significant gaps noted in Open Questions]

### Next Steps

1. If this skill was called by `generate-thesis`: the brief grounds
   the candidate thesis's domain fields and the why-now signal.
2. If called standalone during Problem Identification Sprint Day 1:
   the brief seeds the sprint pair's problem-hunting.
3. If called during Idea Generation Sprint Week 1: the brief sets
   the context for subsequent customer interviews.

---
