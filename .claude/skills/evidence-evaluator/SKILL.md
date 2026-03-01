# Evidence Evaluator

Read all papers in a research session, extract and consolidate claims, assign evidence tiers, and detect contradictions across the entire evidence base.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder

## Process

### Step 1: Read All Paper Files

Read every paper file in `{session_path}/papers/`. Each will have deep reading notes with extracted claims appended by the deep-reader agent.

Also read `brief.md` to understand what research questions we're trying to answer.

### Step 2: Build the Claims Database

For every claim found across all papers, create a consolidated entry:

```markdown
### Claim [N]: "[claim text]"

- **Theme:** [which research question/theme this relates to]
- **Evidence Tier:** [Gold/Silver/Bronze/Noise]
- **Confidence:** [High/Medium/Low]
- **Supporting Sources:**
  - paper_XXX: [brief description of how it supports this claim]
  - paper_YYY: [brief description]
- **Contradicting Sources:**
  - paper_ZZZ: [brief description of contradiction]
- **Nuances:** [important caveats, conditions, or qualifications]
```

### Evidence Tier Definitions

**Gold — Highest confidence**
- Systematic reviews and meta-analyses of high-quality studies
- Large, well-designed randomized controlled trials (RCTs)
- Findings replicated across multiple independent studies
- Established scientific consensus with strong mechanistic understanding

**Silver — Moderate confidence**
- Single well-designed RCTs or large observational studies
- Expert consensus statements from recognized bodies
- Well-conducted systematic reviews with some limitations
- Findings from 2-3 independent studies, not yet extensively replicated

**Bronze — Lower confidence**
- Small studies (N < 50), pilot studies
- Single observational or case-control studies
- Expert opinion pieces, editorials
- Preprints not yet peer-reviewed
- Animal or in vitro studies (when claims are about human outcomes)
- Studies with notable methodological limitations

**Noise — Unreliable**
- Blog posts, social media, press releases without primary sources
- Studies with clear conflicts of interest and no independent replication
- Anecdotal evidence, single case reports used to make general claims
- Claims that misrepresent or overinterpret cited data
- Retracted or seriously questioned papers

### Step 3: Merge Duplicate Claims

Multiple papers may state the same claim in different words. Merge these:
- Group claims that say essentially the same thing
- Pick the most precise formulation as the canonical version
- List all supporting papers
- The merged claim's tier = the highest tier among its sources

### Step 4: Detect Contradictions

Systematically look for:

1. **Direct contradictions:** Paper A says "X increases Y", Paper B says "X decreases Y"
2. **Magnitude disagreements:** Paper A says "X has a large effect", Paper B says "X has a negligible effect"
3. **Scope contradictions:** Paper A says "X is true in general", Paper B says "X is only true under condition Z"
4. **Methodological contradictions:** Different methods yield different conclusions

For each contradiction:

```markdown
### Contradiction [N]: [brief description]

- **Claim A:** "[claim]" (paper_XXX, Tier: [tier])
- **Claim B:** "[claim]" (paper_YYY, Tier: [tier])
- **Nature:** [Direct/Magnitude/Scope/Methodological]
- **Stronger Evidence:** [which side has stronger evidence, and why]
- **Possible Explanation:** [why these might disagree — different populations, methods, time periods, etc.]
- **Resolution Status:** [Resolved/Unresolved/Partially Resolved]
```

### Step 5: Organize by Theme

Group all claims under thematic headings that map to the research questions in `brief.md`. Within each theme, order claims by evidence tier (Gold first, then Silver, then Bronze).

### Step 6: Compute Summary Statistics

At the top of claims.md, include:

```markdown
## Evidence Summary
- **Total Claims Extracted:** [N]
- **Gold Tier:** [N] ([%])
- **Silver Tier:** [N] ([%])
- **Bronze Tier:** [N] ([%])
- **Noise:** [N] ([%])
- **Contradictions Detected:** [N]
- **Resolved Contradictions:** [N]
- **Unresolved Contradictions:** [N]
```

## Output Files

### `claims.md`
Write the full claims database organized by theme, with the summary statistics at the top.

### `contradictions.md`
Write all detected contradictions with full analysis.

Format:
```markdown
# Contradictions Analysis

## Summary
- Total contradictions: [N]
- Resolved: [N]
- Unresolved: [N]
- Highest-impact unresolved: [brief description]

## Contradictions

### 1. [Brief description]
[full contradiction entry as formatted above]

### 2. [Brief description]
[...]
```

## Quality Standards

- Be conservative with Gold tier — most claims will be Silver or Bronze
- Don't manufacture contradictions where none exist — genuine disagreement only
- When evidence is ambiguous, say so rather than forcing a tier assignment
- Consider the full context: a claim supported by one Gold source and contradicted by three Bronze sources is still likely Gold-tier
- Note when claims are based on abstract-only analysis (reduced confidence)
