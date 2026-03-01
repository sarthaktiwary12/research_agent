# Deep Research Agent — Build Plan

## Philosophy

**No code. Only skills and agents.**

When the user sends a research prompt, Claude Code itself does ALL the work by:
1. Reading skill files that tell it exactly how to research
2. Spawning parallel agents for concurrent work
3. Using its native tools (WebSearch, WebFetch, Read, Write, Bash) to gather and process information
4. Storing everything in a simple folder-per-prompt structure

There are no Python scripts, no servers, no databases. Claude Code IS the research engine.

---

## Project Structure

```
research_agent/
├── CLAUDE.md                              # Master instructions — Claude reads this first
│
├── .claude/
│   └── skills/
│       │
│       │ ── CUSTOM SKILLS (we build these) ──
│       │
│       ├── deep-research/
│       │   └── SKILL.md                   # Master orchestrator — the brain
│       │
│       ├── query-strategist/
│       │   └── SKILL.md                   # Query generation & adaptive evolution
│       │
│       ├── literature-search/
│       │   └── SKILL.md                   # Multi-source search across web + APIs
│       │
│       ├── deep-reader/
│       │   └── SKILL.md                   # Full-text comprehension & structured extraction
│       │
│       ├── evidence-evaluator/
│       │   └── SKILL.md                   # Claim extraction, evidence tiering, contradiction detection
│       │
│       ├── citation-chaser/
│       │   └── SKILL.md                   # Follow citation chains to find hidden gems
│       │
│       ├── research-critic/
│       │   └── SKILL.md                   # Gap analysis, uncertainty, what's missing
│       │
│       ├── synthesis-writer/
│       │   └── SKILL.md                   # Multi-perspective final report generation
│       │
│       │ ── K-DENSE SKILLS (install from repo) ──
│       │
│       ├── document-skills/               # PDF/DOCX/PPTX/XLSX processing
│       │   ├── pdf/SKILL.md
│       │   ├── docx/SKILL.md
│       │   ├── pptx/SKILL.md
│       │   └── xlsx/SKILL.md
│       ├── markdown-mermaid-writing/SKILL.md
│       ├── matplotlib/SKILL.md
│       ├── biopython/SKILL.md
│       ├── exploratory-data-analysis/SKILL.md
│       ├── statistical-analysis/SKILL.md
│       ├── literature-review/SKILL.md
│       ├── scientific-brainstorming/SKILL.md
│       ├── scientific-critical-thinking/SKILL.md
│       ├── pubmed-database/SKILL.md
│       ├── pubchem-database/SKILL.md
│       ├── opentargets-database/SKILL.md
│       ├── pdb-database/SKILL.md
│       ├── uspto-database/SKILL.md
│       ├── drugbank-database/SKILL.md
│       ├── clinicaltrials-database/SKILL.md
│       ├── clinvar-database/SKILL.md
│       └── biorxiv-database/SKILL.md
│
└── research_sessions/                     # One folder per research prompt
```

---

## Per-Prompt Folder Structure

When the user gives a research prompt, Claude creates:

```
research_sessions/
└── 2026-03-01_[slug-of-prompt]/
    ├── brief.md                 # The original prompt + expanded research questions
    ├── queries.md               # All search queries (initial + evolved)
    ├── search_log.md            # What was searched, where, what was found
    ├── papers/                  # Downloaded/saved papers and sources
    │   ├── paper_001.md         # Full text or detailed notes from each source
    │   ├── paper_002.md
    │   └── ...
    ├── claims.md                # Extracted claims with evidence tiers (gold/silver/bronze)
    ├── contradictions.md        # Detected contradictions between sources
    ├── gaps.md                  # Identified knowledge gaps after each loop
    ├── loop_log.md              # Progress log for each iteration of the research loop
    └── final_report.md          # The comprehensive synthesis
```

---

## CLAUDE.md — What It Says

The CLAUDE.md is the most important file. It tells Claude Code:

1. **When the user asks a research question** → activate the `deep-research` skill
2. **Always create a session folder** in `research_sessions/` before starting
3. **Deploy agents in parallel** whenever possible — don't do things sequentially that can be done concurrently
4. **Save everything to files** — every paper, every claim, every query goes into the session folder
5. **Loop until satisfied** — keep searching, reading, and evaluating until gaps are filled
6. **Use the installed skills** as reference knowledge when working with specific tools/databases
7. **Research profiles** — how deep to go based on what the user asks for

---

## The 8 Custom Skills — What Each One Does

### 1. `deep-research` (Master Orchestrator)

**Purpose:** The brain. When activated, it runs the entire research pipeline.

**What the SKILL.md tells Claude to do:**

```
PHASE 1: UNDERSTAND
- Parse the user's prompt into a structured research brief
- Identify the domain (science, finance, law, tech, general)
- Determine the research profile (fast/balanced/deep/legendary)
- Create the session folder

PHASE 2: EXPAND (spawn query-strategist agent)
- Generate 20-100 diverse search queries from the brief
- Cover: definitions, mechanisms, evidence, controversies, recent developments, key people

PHASE 3: SEARCH (spawn 3-5 parallel literature-search agents)
- Each agent searches a cluster of sources
- Agent A: WebSearch (Google, general web)
- Agent B: Academic (PubMed, bioRxiv, Semantic Scholar via WebFetch)
- Agent C: Domain-specific (patents, clinical trials, financial data, etc.)
- Agent D: Specialized databases (using installed K-Dense database skills)
- All agents save found papers/sources to the session papers/ folder

PHASE 4: READ (spawn parallel deep-reader agents)
- One agent per paper/source (up to 10 parallel)
- Each reads the full text and extracts structured notes
- Saves comprehension notes back to the papers/ folder

PHASE 5: EVALUATE (spawn evidence-evaluator agent)
- Read all paper notes from the folder
- Extract claims, assign evidence tiers
- Detect contradictions
- Save to claims.md and contradictions.md

PHASE 6: CHASE CITATIONS (spawn citation-chaser agent)
- From top-cited papers, follow references to find key sources
- Use Semantic Scholar API via WebFetch
- Save newly found papers to papers/ folder

PHASE 7: CRITIQUE (spawn research-critic agent)
- Read everything in the session folder
- Identify gaps, unanswered questions, weak evidence areas
- Save to gaps.md

PHASE 8: LOOP OR STOP
- If significant gaps remain AND loop count < max_loops:
  → Spawn query-strategist agent with gaps as input
  → Generate evolved queries targeting gaps
  → Go back to PHASE 3
- If gaps are minor OR max loops reached:
  → Proceed to synthesis

PHASE 9: SYNTHESIZE (spawn synthesis-writer agent)
- Read the entire session folder
- Write a comprehensive report with:
  - Executive summary
  - Detailed findings organized by theme
  - Evidence quality assessment
  - Contradictions and open questions
  - Recommendations for further research
  - Full source list with annotations
- Save to final_report.md
```

**Research Profiles (configured in the skill):**

| Profile | Queries | Max Papers | Loops | Use When |
|---------|---------|------------|-------|----------|
| fast | 10-20 | 10-20 | 1 | Quick overview, simple questions |
| balanced | 30-50 | 30-50 | 2-3 | Standard research questions |
| deep | 50-100 | 50-150 | 5-8 | Thorough investigation |
| legendary | 100-300 | 200-500 | 10-15 | Exhaustive, multi-hour deep dive |

---

### 2. `query-strategist`

**Purpose:** Generate and evolve search queries.

**What the SKILL.md tells Claude to do:**
- Given a research brief (or gaps from a previous loop), generate diverse queries
- Use multiple strategies:
  - **Definitional:** "What is X?"
  - **Mechanistic:** "How does X work?"
  - **Comparative:** "X vs Y"
  - **Temporal:** "Recent advances in X 2024-2026"
  - **Controversial:** "Criticisms of X", "Limitations of X"
  - **Expert-seeking:** "Leading researchers in X"
  - **Quantitative:** "Meta-analysis of X", "Statistics on X"
  - **Cross-domain:** "X applications in [adjacent field]"
- When evolving queries (loop iteration > 1):
  - Read gaps.md from the session folder
  - Generate queries that specifically target unfilled gaps
  - Add Boolean operators for precision
  - Try different terminology and synonyms
- Save all queries to queries.md with tags for which strategy generated them

---

### 3. `literature-search`

**Purpose:** Search for sources across the web and academic databases.

**What the SKILL.md tells Claude to do:**
- Accept a set of queries and a source cluster assignment
- For each query:
  - Use **WebSearch** for general web results
  - Use **WebFetch** to hit specific APIs:
    - Semantic Scholar API: `https://api.semanticscholar.org/graph/v1/paper/search?query=...`
    - PubMed E-utilities: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=pubmed&term=...`
    - bioRxiv API: `https://api.biorxiv.org/details/biorxiv/...`
    - CrossRef: `https://api.crossref.org/works?query=...`
    - arXiv: `https://export.arxiv.org/api/query?search_query=...`
    - CORE API: `https://api.core.ac.uk/v3/search/works?q=...`
  - For domain-specific searches, use the installed K-Dense database skills as reference
- For each result found:
  - Create a paper file in the session papers/ folder
  - Include: title, authors, year, abstract, URL, source database
  - If full text is accessible via URL, fetch it with WebFetch
- Log everything to search_log.md
- Deduplicate by title/DOI

---

### 4. `deep-reader`

**Purpose:** Deeply comprehend a paper/source and extract structured insights.

**What the SKILL.md tells Claude to do:**
- Read the paper file from the session papers/ folder
- If the paper only has an abstract, try to fetch full text via:
  - Direct URL with WebFetch
  - Unpaywall API: `https://api.unpaywall.org/v2/[DOI]?email=...`
  - PubMed Central: `https://www.ncbi.nlm.nih.gov/pmc/articles/PMC.../`
- Comprehend the full document and add structured notes to the paper file:
  - **Key findings** (bulleted)
  - **Methodology** (study type, sample size, statistical methods)
  - **Strength of evidence** (gold/silver/bronze with reasoning)
  - **Claims** (specific, quotable assertions with page/section references)
  - **Limitations** (stated by authors + your assessment)
  - **Connections** (how this relates to other papers in the session)
  - **Key references to chase** (papers cited here that look important)
- Update the paper file in-place with these notes appended

---

### 5. `evidence-evaluator`

**Purpose:** Extract and tier all claims across the research session.

**What the SKILL.md tells Claude to do:**
- Read ALL paper files in the session papers/ folder
- Extract every factual claim and categorize:

  **Evidence Tiers:**
  - **Gold:** Systematic reviews, meta-analyses, large RCTs, replicated findings
  - **Silver:** Single well-designed studies, expert consensus statements
  - **Bronze:** Case reports, observational studies, expert opinions, preprints
  - **Noise:** Blog posts, unreferenced claims, conflicts of interest noted

- For each claim, record:
  - The claim text
  - Evidence tier with justification
  - Supporting sources (which papers)
  - Contradicting sources (if any)
  - Confidence level (high/medium/low)

- Detect contradictions:
  - Find claims that directly oppose each other
  - Note which has stronger evidence
  - Flag for the research-critic to investigate

- Write claims.md with all claims organized by theme
- Write contradictions.md with all detected conflicts

---

### 6. `citation-chaser`

**Purpose:** Follow citation chains to discover important papers not found by search.

**What the SKILL.md tells Claude to do:**
- Read the paper files in the session, identify the most important/cited ones
- For each key paper, use Semantic Scholar API to get:
  - **References** (papers this one cites): `https://api.semanticscholar.org/graph/v1/paper/{id}/references`
  - **Citations** (papers that cite this one): `https://api.semanticscholar.org/graph/v1/paper/{id}/citations`
- Filter by relevance to the research brief
- For highly relevant cited/citing papers:
  - Check if already in the session (deduplicate)
  - If new, create a paper file in papers/ with available metadata
  - Flag for the deep-reader to process
- Do 1-2 hops (not more, to avoid scope explosion)
- Log all citation chasing activity to search_log.md

---

### 7. `research-critic`

**Purpose:** Find what's missing, what's weak, and what's wrong.

**What the SKILL.md tells Claude to do:**
- Read the ENTIRE session folder: brief, queries, all papers, claims, contradictions
- Produce a gap analysis:
  - **Unanswered questions:** What parts of the original brief remain unaddressed?
  - **Weak evidence areas:** Where do we only have bronze-tier evidence?
  - **Unresolved contradictions:** Where do sources disagree without resolution?
  - **Missing perspectives:** Are there viewpoints, disciplines, or geographies underrepresented?
  - **Recency gaps:** Are key findings from before 2020 with no recent updates?
  - **Methodological concerns:** Are there systematic biases in the evidence collected?
- Score overall research completeness (0-100%)
- Recommend specific follow-up queries to fill gaps
- Write gaps.md with structured gap analysis
- This file is the input for the next loop iteration (if the orchestrator decides to continue)

---

### 8. `synthesis-writer`

**Purpose:** Produce the final comprehensive research report.

**What the SKILL.md tells Claude to do:**
- Read the ENTIRE session folder
- Write final_report.md with this structure:

  ```
  # [Research Question]

  ## Executive Summary
  [3-5 paragraph overview of key findings]

  ## Key Findings
  [Organized by theme, each finding with evidence tier noted]

  ## Detailed Analysis
  [Deep dive into each major topic area]
  [Include specific data, statistics, quotes from sources]

  ## Evidence Quality Assessment
  [How strong is the overall evidence base?]
  [Distribution of gold/silver/bronze sources]

  ## Contradictions & Open Questions
  [Where experts disagree and why]
  [Questions that remain unanswered]

  ## Methodology
  [How this research was conducted]
  [Number of sources, databases searched, iterations performed]

  ## Recommendations
  [What to do with these findings]
  [Where further research is needed]

  ## Sources
  [Every source with: title, authors, year, URL, evidence tier]
  [Organized by relevance/importance]
  ```

- Use markdown-mermaid-writing skill for any diagrams
- Use matplotlib skill if data visualization would help
- Make the report readable by a non-expert but useful to an expert

---

## K-Dense Skills — Installation Plan

Clone the 20 skills from the K-Dense repo into `.claude/skills/`:

| Skill | Why We Need It |
|-------|---------------|
| document-skills (pdf/docx/pptx/xlsx) | Process downloaded documents |
| markdown-mermaid-writing | Diagrams in reports |
| matplotlib | Data visualizations |
| biopython | Bio sequence analysis when needed |
| exploratory-data-analysis | Analyze datasets found during research |
| statistical-analysis | Statistical reasoning about evidence |
| literature-review | Reference methodology for systematic reviews |
| scientific-brainstorming | Ideation when generating hypotheses |
| scientific-critical-thinking | Critical evaluation of claims |
| pubmed-database | PubMed API patterns |
| pubchem-database | PubChem API patterns |
| opentargets-database | Drug target data |
| pdb-database | Protein structures |
| uspto-database | Patent search |
| drugbank-database | Drug information |
| clinicaltrials-database | Clinical trial search |
| clinvar-database | Genetic variant data |
| biorxiv-database | Preprint search |

---

## Build Order

### Step 1: Scaffold
- Create all directories
- Write CLAUDE.md
- Install K-Dense skills (clone + copy)

### Step 2: Core Skills (build in this order)
1. `query-strategist/SKILL.md`
2. `literature-search/SKILL.md`
3. `deep-reader/SKILL.md`
4. `evidence-evaluator/SKILL.md`
5. `citation-chaser/SKILL.md`
6. `research-critic/SKILL.md`
7. `synthesis-writer/SKILL.md`

### Step 3: Master Orchestrator
8. `deep-research/SKILL.md` — references all the above skills

### Step 4: Test
- Give it a real research prompt
- Watch it work
- Iterate on the skills based on what works and what doesn't

---

## What Makes This 50x Better

| Dimension | ChatGPT/Perplexity Deep Research | This System |
|-----------|----------------------------------|-------------|
| Sources | 1 search engine | 10+ APIs + web search in parallel |
| Depth | Snippets and summaries | Full-text reading of every source |
| Iteration | Single pass | 1-15 adaptive loops |
| Citation graph | None | BFS 2 hops from key papers |
| Evidence quality | No assessment | Gold/silver/bronze tiering |
| Contradictions | Ignored | Explicitly detected and analyzed |
| Gap analysis | None | Systematic critique after each loop |
| Parallelism | Sequential | 5-10 agents running simultaneously |
| Runtime | 30 seconds | Minutes to hours (configurable) |
| Output | Short summary | 5,000-50,000 word annotated report |
| Storage | Gone after session | Permanent folder with all papers and notes |
| Transparency | Black box | Full search log, paper notes, claim extraction visible |
