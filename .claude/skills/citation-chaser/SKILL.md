# Citation Chaser

Follow citation chains from key papers to discover important sources that weren't found by direct search. Uses forward (who cites this?) and backward (what does this cite?) traversal.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder
- `max_hops`: Maximum citation chain depth (default: 2)

## Process

### Step 1: Identify Seed Papers

Read all paper files in `{session_path}/papers/`. Select seed papers for citation chasing based on:

1. **Highest citation count** — heavily cited papers are likely foundational
2. **Most relevant to the brief** — papers that directly address core research questions
3. **Papers with "Key References to Chase"** — the deep-reader flagged these
4. **Review papers** — their reference lists are curated overviews of a field

Select the top 5-10 seed papers (fewer for fast profile, more for deep/legendary).

### Step 2: Backward Citation Chasing (References)

For each seed paper, get what it cites:

**Using Semantic Scholar API:**
```
GET https://api.semanticscholar.org/graph/v1/paper/{paper_id}/references?fields=title,authors,year,abstract,url,citationCount,externalIds&limit=100
```

Where `{paper_id}` can be:
- DOI: `DOI:{doi}`
- PMID: `PMID:{pmid}`
- Semantic Scholar ID (if available)
- arXiv ID: `ARXIV:{arxiv_id}`

**Also check:** The "Key References to Chase" section in each seed paper's deep reading notes — the deep-reader already identified which references look most promising.

### Step 3: Forward Citation Chasing (Who Cites This?)

For each seed paper, get what cites it:

**Using Semantic Scholar API:**
```
GET https://api.semanticscholar.org/graph/v1/paper/{paper_id}/citations?fields=title,authors,year,abstract,url,citationCount,externalIds&limit=100
```

This finds more recent papers that build on the seed paper's work. Prioritize:
- Highly cited citing papers
- Recent papers (last 2-3 years)
- Papers whose titles suggest they address our research questions

### Step 4: Filter for Relevance

For each discovered paper (from both forward and backward chasing):

1. **Read the title and abstract**
2. **Score relevance** to the research brief (0-10):
   - 8-10: Directly addresses a core research question → definitely add
   - 5-7: Partially relevant, provides useful context → add if under source limit
   - 0-4: Tangentially related or off-topic → skip
3. **Check for duplicates** against existing papers in the session folder (match by DOI, PMID, or title)
4. **Skip** papers already in the session

### Step 5: Create Paper Files

For each relevant new paper, create a paper file in `{session_path}/papers/` with the same format as literature-search:

```markdown
# [Paper Title]

## Metadata
- **Authors:** [author list]
- **Year:** [year]
- **Source:** [journal/preprint]
- **URL:** [url]
- **DOI:** [doi]
- **PMID:** [pmid if available]
- **Citation Count:** [count]
- **Source Database:** Citation chase from paper_XXX ([forward/backward])
- **Relevance Score:** [0-10]

## Abstract
[abstract]

## Full Text Status
- [ ] Full text retrieved
- [ ] Abstract only

## Full Text
[attempt retrieval same as literature-search]

---
*Deep reading notes will be appended below by the deep-reader agent.*
```

### Step 6: Second Hop (if max_hops >= 2)

From the most promising newly discovered papers (top 3-5 by relevance score), repeat steps 2-5 for one more hop. Be more selective on the second hop — only add papers with relevance score >= 8.

Do NOT go beyond 2 hops. The risk of scope explosion outweighs the diminishing returns.

### Step 7: Log Activity

Append to `search_log.md`:

```markdown
## Citation Chase: [timestamp]
- **Seed Papers:** [list of seed paper file names]
- **Backward References Checked:** [count]
- **Forward Citations Checked:** [count]
- **New Papers Added:** [count]
- **Duplicates Skipped:** [count]
- **Irrelevant Skipped:** [count]
- **Hops Completed:** [1 or 2]
- **New Paper Files:** [list]
```

## Rate Limiting

- Semantic Scholar API: max 100 requests per 5 minutes without API key
- Add a 1-second pause between API calls
- If rate limited, wait 10 seconds and retry once
- If still failing, log and move on

## Key Principle

Citation chasing finds the papers that search engines miss — foundational older works, niche studies, and recent follow-ups that haven't been indexed well yet. Focus on quality over quantity: a few highly relevant discovered papers are worth more than dozens of tangential ones.
