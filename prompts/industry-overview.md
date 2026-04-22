# Industry Overview

A research prompt that returns a structured snapshot of an
industry: market size, company count, size distribution, growth
rate, and geography.

**Used automatically by:** `generate-thesis` during its
desk-research step. Claude reads this file, runs the research, and
returns the data to the calling skill. Nothing for the user to do.

**For standalone use:** copy the prompt below, paste it into
ChatGPT or Claude.ai, and replace `[INDUSTRY]` with the industry
name.

---

I'm researching [INDUSTRY] for vertical SaaS opportunities. Please provide:
1. Total US market size in revenue
2. Number of companies
3. Typical company size distribution
4. Industry growth rate
5. Geographic distribution

Format as structured data with sources.
