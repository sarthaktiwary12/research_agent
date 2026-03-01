# Deep Reader

Perform deep comprehension of a paper or source, extracting structured insights and preparing it for evidence evaluation.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder
- `paper_file`: Path to the specific paper file in `papers/` to read
- `brief_path`: Path to `brief.md` for context on what the research is about

## Process

### Step 1: Read the Paper File

Read the paper file from the session folder. It will already contain metadata and either an abstract or full text, placed there by the literature-search agent.

### Step 2: Attempt Full Text Retrieval (if needed)

If the paper only has an abstract (the "Full text retrieved" checkbox is unchecked):

1. Try the direct URL with WebFetch
2. If a DOI is available, try Unpaywall: `https://api.unpaywall.org/v2/{doi}?email=research@example.com`
   - Parse the response for `best_oa_location.url_for_pdf` or `best_oa_location.url_for_landing_page`
   - Fetch that URL with WebFetch
3. If a PMID is available, check if it has a PMC version:
   - `https://www.ncbi.nlm.nih.gov/pmc/articles/PMC{pmcid}/`
   - `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/elink.fcgi?dbfrom=pubmed&db=pmc&id={pmid}&retmode=json`
4. If full text is retrieved, update the paper file with the full text and check the box

### Step 3: Deep Comprehension

Read the brief to understand the research context. Then analyze the paper thoroughly.

### Step 4: Append Structured Notes

Append the following sections to the paper file (after the `---` separator):

```markdown
## Deep Reading Notes

### Key Findings
- [Bullet each major finding, stated as a clear factual claim]
- [Be specific — include numbers, effect sizes, p-values where available]
- [Distinguish between what the authors claim vs. what the data shows]

### Methodology
- **Study Type:** [RCT, cohort, case-control, review, meta-analysis, in vitro, in silico, etc.]
- **Sample Size:** [N=X, or "N/A" for reviews]
- **Population/Model:** [who/what was studied]
- **Key Methods:** [techniques, assays, statistical approaches]
- **Statistical Methods:** [tests used, significance thresholds]
- **Duration:** [study duration if applicable]

### Evidence Strength Assessment
- **Tier:** [Gold/Silver/Bronze/Noise]
- **Reasoning:** [Why this tier? Consider: study design, sample size, replication, bias risk, conflicts of interest]
- **Risk of Bias:** [Low/Medium/High — with specific concerns]

### Specific Claims
[Number each claim for easy reference]

1. **Claim:** "[exact claim, quoted if possible]"
   - **Evidence:** [what data supports this]
   - **Confidence:** [high/medium/low]
   - **Section/Page:** [where in the paper]

2. **Claim:** "[next claim]"
   - **Evidence:** [...]
   - **Confidence:** [...]
   - **Section/Page:** [...]

[Continue for all significant claims]

### Limitations
- **Stated by authors:** [what the authors acknowledge]
- **Additional concerns:** [limitations you identify that authors don't mention]

### Relevance to Research Brief
- **Directly addresses:** [which research questions from the brief]
- **Partially addresses:** [which questions it touches on]
- **Novel contribution:** [what this adds that other papers in the session don't]

### Key References to Chase
[List 3-5 references cited in this paper that look important for our research question]
- [Author(s) (Year). "Title." — Why: [reason this looks important]]
- [...]

### Connections to Other Session Papers
[After reading, note any connections to other papers already in the session]
- Agrees with paper_XXX on: [topic]
- Contradicts paper_XXX on: [topic]
- Extends paper_XXX by: [how]
```

## Quality Standards

- **Accuracy:** Never misrepresent what a paper says. When uncertain, say "the paper appears to suggest" rather than stating definitively.
- **Completeness:** Extract ALL significant claims, not just the abstract's highlights. Methods sections and supplementary data often contain crucial details.
- **Context:** Always read claims in context of the methodology. A claim from an N=10 pilot study is different from an N=10,000 RCT.
- **Quotes:** Use direct quotes for critical claims, with section/page references.
- **Honesty:** If you can only access the abstract, clearly note that all notes are "based on abstract only" and adjust confidence accordingly.

## Abstract-Only Papers

If only the abstract is available after all retrieval attempts:
- Prefix the Deep Reading Notes section with: `> **Note: Analysis based on abstract only. Evidence confidence is reduced.**`
- Still extract what you can, but:
  - Set all claim confidence to no higher than "medium"
  - Note methodology as "Not fully assessable from abstract"
  - Mark evidence tier one level lower than it would otherwise be (e.g., Gold → Silver)
