# Literature Search

Execute multi-source searches across the web and academic databases to find relevant papers, articles, and data sources for a research session.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder
- `queries`: A subset of queries from `queries.md` assigned to this agent
- `source_cluster`: Which sources this agent is responsible for (see below)

## Source Clusters

Each literature-search agent is assigned one cluster. The orchestrator spawns multiple agents in parallel, one per cluster.

### Cluster A: General Web
- **Tool:** WebSearch
- For each query, run a WebSearch and collect the top results
- Follow promising links with WebFetch to get full content
- Prioritize: review articles, institutional pages, well-cited blog posts from domain experts

### Cluster B: PubMed + PMC
- **Tool:** WebFetch against PubMed E-utilities API
- Search endpoint: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi?db=pubmed&retmode=json&retmax=20&term={query}`
- Fetch abstracts: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=pubmed&retmode=xml&id={pmid}`
- Summary endpoint: `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/esummary.fcgi?db=pubmed&retmode=json&id={pmid_list}`
- For open-access papers, try PMC full text: `https://www.ncbi.nlm.nih.gov/pmc/articles/PMC{id}/`
- Reference the `pubmed-database` skill for detailed API patterns

### Cluster C: Preprints + Open Access
- **bioRxiv/medRxiv:** `https://api.biorxiv.org/details/biorxiv/{start_date}/{end_date}/{cursor}`
  - Also try WebSearch with `site:biorxiv.org {query}` and `site:medrxiv.org {query}`
- **arXiv:** `https://export.arxiv.org/api/query?search_query=all:{query}&max_results=10`
- **CORE:** `https://api.core.ac.uk/v3/search/works?q={query}&limit=10`
- Reference the `biorxiv-database` skill for bioRxiv patterns

### Cluster D: Semantic Scholar + CrossRef
- **Semantic Scholar:** `https://api.semanticscholar.org/graph/v1/paper/search?query={query}&limit=10&fields=title,authors,year,abstract,url,citationCount,externalIds`
- **CrossRef:** `https://api.crossref.org/works?query={query}&rows=10&sort=relevance`
- Semantic Scholar is particularly valuable for citation counts and connected papers

### Cluster E: Domain-Specific Databases
- Use when the research topic touches specific domains:
  - **Drug/pharma:** PubChem, DrugBank, OpenTargets (reference their K-Dense skills)
  - **Clinical:** ClinicalTrials.gov API v2, ClinVar (reference their K-Dense skills)
  - **Structural biology:** PDB (reference the pdb-database skill)
  - **Patents:** USPTO (reference the uspto-database skill)
- Only search databases relevant to the topic

## For Each Result Found

Create a paper file in the session `papers/` folder:

```markdown
# [Paper Title]

## Metadata
- **Authors:** [author list]
- **Year:** [year]
- **Source:** [journal/preprint server/website]
- **URL:** [url]
- **DOI:** [doi if available]
- **PMID:** [pmid if available]
- **Citation Count:** [if available]
- **Source Database:** [which cluster/API found this]

## Abstract
[abstract text]

## Full Text Status
- [ ] Full text retrieved
- [ ] Abstract only

## Full Text
[full text if retrieved, otherwise empty]

---
*Deep reading notes will be appended below by the deep-reader agent.*
```

### Paper File Naming
- Use sequential numbering: `paper_001.md`, `paper_002.md`, etc.
- Check existing files to continue the sequence

### Full Text Retrieval
For each paper, attempt to get full text:
1. Direct URL via WebFetch
2. If DOI available, try Unpaywall: `https://api.unpaywall.org/v2/{doi}?email=research@example.com`
3. If PMID available, check PMC: `https://www.ncbi.nlm.nih.gov/pmc/articles/PMC{pmcid}/`
4. If none work, keep abstract only and mark the checkbox

## Deduplication
- Before creating a paper file, check existing papers in the folder
- Match by DOI (exact), PMID (exact), or title (fuzzy — same title after lowercasing and removing punctuation)
- If a duplicate is found, skip it but log the duplicate detection

## Search Log
Append all search activity to `search_log.md` in the session folder:

```markdown
## Search: [timestamp]
- **Cluster:** [A/B/C/D/E]
- **Query:** [the query]
- **API/Tool:** [WebSearch/PubMed/Semantic Scholar/etc.]
- **Results Found:** [count]
- **Papers Saved:** [list of paper file names]
- **Duplicates Skipped:** [count]
- **Notes:** [any issues, rate limits, errors]
```

## Rate Limiting
- Add a 1-second pause between API calls to the same endpoint
- If an API returns a rate limit error, wait 5 seconds and retry once
- If still failing, log the error and move on

## Error Handling
- If an API is unreachable, log it and continue with other sources
- Never let one failed API block the entire search
- Always log errors to search_log.md
