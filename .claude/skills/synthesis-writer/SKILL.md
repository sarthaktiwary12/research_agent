# Synthesis Writer

Produce the final comprehensive research report by synthesizing all evidence, claims, contradictions, and gaps from the entire research session.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder

## Process

### Step 1: Read the Entire Session

Read ALL files in the session folder:
- `brief.md` — research questions and context
- `claims.md` — all claims with evidence tiers
- `contradictions.md` — all contradictions
- `gaps.md` — remaining knowledge gaps
- `loop_log.md` — research process history
- `search_log.md` — what was searched
- All paper files in `papers/` — source details and deep reading notes

### Step 2: Plan the Report Structure

Based on the research questions and themes that emerged:
1. Identify 3-7 major thematic sections
2. Order them logically (general → specific, or chronological, or by importance)
3. Map claims to sections
4. Identify where contradictions and gaps fit in

### Step 3: Write the Report

Write `final_report.md` with the following structure:

```markdown
# [Research Question — as a clear title]

**Research Date:** [date]
**Profile:** [fast/balanced/deep/legendary]
**Sources Analyzed:** [N]
**Research Iterations:** [N loops]

---

## Executive Summary

[3-5 paragraphs summarizing the key findings. This should be readable as a standalone summary. Include:
- The main conclusions
- The strength of evidence behind them
- The most important caveats or uncertainties
- What is well-established vs. still debated]

---

## Key Findings

[A numbered list of the most important findings, each with its evidence tier noted. This is the "TL;DR" section.]

1. **[Finding]** (Evidence: Gold/Silver/Bronze)
2. **[Finding]** (Evidence: Gold/Silver/Bronze)
...

---

## Detailed Analysis

### [Theme 1: Descriptive Title]

[Write in flowing paragraphs, not bullet points. Integrate evidence from multiple sources. For each major claim, cite the source(s) using the format (Author, Year) or (paper_XXX). Include specific data points — numbers, percentages, effect sizes, p-values — when available.

Note the evidence tier for key claims: "This finding is supported by Gold-tier evidence from a meta-analysis of 15 RCTs (Author, Year)..." or "Limited Bronze-tier evidence suggests... (Author, Year)."]

### [Theme 2: Descriptive Title]

[Same approach. Cross-reference with Theme 1 where relevant.]

### [Theme 3]
...

[Continue for all major themes]

---

## Contradictions and Debates

[For each significant contradiction from contradictions.md, explain:
- What the disagreement is
- Who says what, and based on what evidence
- What might explain the disagreement
- Which side has stronger evidence (if determinable)
- What would be needed to resolve it]

---

## Evidence Quality Assessment

### Overall Evidence Landscape
[Summarize: how strong is the overall evidence base for answering the research questions?]

### Distribution
| Tier | Count | Percentage |
|------|-------|------------|
| Gold | [N] | [%] |
| Silver | [N] | [%] |
| Bronze | [N] | [%] |
| Noise | [N] | [%] |

### Strengths of the Evidence Base
[What aspects are well-supported?]

### Weaknesses of the Evidence Base
[Where is evidence thin or problematic?]

---

## Knowledge Gaps and Uncertainties

[From gaps.md, honestly present what remains unknown or uncertain. This section builds credibility by showing intellectual honesty.]

- **[Gap 1]:** [description and why it matters]
- **[Gap 2]:** [description and why it matters]
...

---

## Research Methodology

[Transparent documentation of how this research was conducted]

- **Databases Searched:** [list all APIs and sources used]
- **Total Queries Executed:** [N]
- **Papers/Sources Found:** [N]
- **Papers Deeply Analyzed:** [N]
- **Research Iterations:** [N loops]
- **Date of Research:** [date]
- **Completeness Score:** [X]% (from final gap analysis)
- **Limitations of This Review:** [what this research process might have missed]

---

## Recommendations

### For Practitioners / Decision-Makers
[What should someone DO based on these findings?]

### For Researchers
[What studies would be most valuable to conduct next?]

### For Further Reading
[3-5 particularly important papers that readers should start with]

---

## Sources

[Every source used, organized by evidence tier]

### Gold-Tier Sources
1. [Author(s) (Year). "Title." *Journal*, Volume(Issue), Pages. DOI/URL. — [1-line annotation of what this source contributes]]
...

### Silver-Tier Sources
...

### Bronze-Tier Sources
...

### Other Sources
...
```

## Writing Standards

### Style
- Write in clear, precise prose — paragraphs, not bullet points (except where lists are genuinely appropriate)
- Be accessible to an informed non-specialist but useful to an expert
- Use hedging language appropriately: "evidence suggests" vs "evidence demonstrates" vs "evidence conclusively shows" — match to the evidence tier
- Define technical terms on first use

### Citations
- Cite every factual claim with at least one source
- Use (Author, Year) format in text, with full details in the Sources section
- When a claim has multiple sources, cite the strongest one in text and note others
- When paraphrasing, make clear this is your synthesis, not a direct quote

### Intellectual Honesty
- Never state something more confidently than the evidence warrants
- Explicitly flag where you're extrapolating beyond the evidence
- Present both sides of genuine debates, not just the side with more papers
- Acknowledge limitations of this research process itself

### Length Guidelines
| Profile | Target Length |
|---------|-------------|
| fast | 2,000-5,000 words |
| balanced | 5,000-15,000 words |
| deep | 15,000-30,000 words |
| legendary | 30,000-50,000 words |

These are guidelines, not strict limits. Completeness and quality matter more than hitting a word count.

## Final Check

Before saving the report, verify:
- [ ] Every claim in the report has at least one citation
- [ ] Evidence tiers are noted for key claims
- [ ] Contradictions are presented fairly
- [ ] Gaps are honestly acknowledged
- [ ] The executive summary accurately reflects the report
- [ ] The sources section is complete
- [ ] The report directly addresses all questions from brief.md
