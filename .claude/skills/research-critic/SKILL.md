# Research Critic

Perform a comprehensive gap analysis of the current research session. Identify what's missing, what's weak, and what needs further investigation. This assessment drives whether the orchestrator loops for another iteration.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder
- `loop_number`: The current loop iteration (1 = after first pass)

## Process

### Step 1: Read the Entire Session

Read ALL of the following from the session folder:
- `brief.md` — the original research questions
- `queries.md` — all queries generated so far
- `search_log.md` — what was searched and found
- `claims.md` — all extracted claims with evidence tiers
- `contradictions.md` — detected contradictions
- All paper files in `papers/` (at minimum their metadata and key findings)
- `loop_log.md` — previous loop iterations (if any)
- Previous `gaps.md` (if exists from prior loops)

### Step 2: Assess Coverage Against Brief

For each research question in `brief.md`, evaluate:

```markdown
### Research Question: "[question text]"
- **Coverage:** [Fully Addressed / Partially Addressed / Minimally Addressed / Not Addressed]
- **Evidence Quality:** [Strong (mostly Gold/Silver) / Moderate (mixed) / Weak (mostly Bronze/Noise)]
- **Number of Sources:** [N]
- **Key Findings:** [1-2 sentence summary of what we know]
- **What's Missing:** [specific information gaps]
```

### Step 3: Identify Gap Categories

Analyze gaps across these dimensions:

**1. Unanswered Questions**
- Which parts of the original brief remain unaddressed?
- What follow-up questions have emerged from the research that aren't answered?

**2. Weak Evidence Areas**
- Where do we only have Bronze-tier or Noise-tier evidence?
- Where do we have only a single source for important claims?
- Where are we relying on abstracts because full text wasn't available?

**3. Unresolved Contradictions**
- Which contradictions in `contradictions.md` remain unresolved?
- Could additional evidence tip the balance?
- Are there undetected contradictions you notice now?

**4. Missing Perspectives**
- Are there important viewpoints not represented? (e.g., only positive studies, no negative results)
- Are certain geographies, populations, or subgroups underrepresented?
- Are dissenting expert opinions missing?

**5. Recency Gaps**
- Are key findings based on old studies (pre-2020) with no recent confirmation?
- Are there recent developments the search may have missed?
- Has the field moved since the most recent sources found?

**6. Methodological Concerns**
- Is there systematic bias in the evidence collected? (e.g., publication bias — mostly positive results)
- Are study designs adequate for the claims being made?
- Are there important methodological papers about how to study this topic that we haven't found?

**7. Source Diversity**
- Are most papers from a small number of research groups?
- Is there geographic or institutional concentration?
- Are there relevant databases we haven't searched?

### Step 4: Score Research Completeness

Assign an overall completeness score:

```markdown
## Completeness Score: [0-100]%

### Breakdown:
- Question coverage: [0-100]% — are all questions addressed?
- Evidence quality: [0-100]% — is the evidence strong enough?
- Source diversity: [0-100]% — enough independent sources?
- Contradiction resolution: [0-100]% — are conflicts explained?
- Recency: [0-100]% — is evidence up to date?
```

**Scoring guide:**
- 90-100%: Exhaustive coverage, strong evidence, minimal gaps → **STOP**
- 70-89%: Good coverage with some gaps → **loop if under max loops**
- 50-69%: Significant gaps remain → **definitely loop**
- Below 50%: Major gaps → **definitely loop, and reconsider search strategy**

### Step 5: Generate Recommendations

For each significant gap, recommend specific follow-up actions:

```markdown
### Gap: [description]
- **Priority:** [High/Medium/Low]
- **Recommended Queries:**
  - "[specific query 1]"
  - "[specific query 2]"
- **Recommended Sources:** [specific databases or search strategies to try]
- **Expected Impact:** [what finding this information would add to the report]
```

### Step 6: Compare to Previous Loops

If `loop_number > 1`, read previous `gaps.md` and assess:
- Which previous gaps have been filled?
- Which remain despite additional searching?
- Are we seeing diminishing returns? (few new papers, same gaps persisting)
- Should we stop even if below the completeness threshold?

Flag diminishing returns explicitly — if two consecutive loops fail to improve completeness by more than 5%, recommend stopping.

## Output

### `gaps.md`

```markdown
# Gap Analysis — Loop [N]

## Completeness Score: [X]%

## Recommendation: [CONTINUE / STOP]
[Brief justification]

## Coverage Assessment
[Step 2 output — coverage for each research question]

## Identified Gaps

### High Priority
[gaps that significantly impact the report if unfilled]

### Medium Priority
[gaps that would improve the report]

### Low Priority
[nice-to-have information]

## Recommended Follow-Up Queries
[from Step 5]

## Loop Progress
[from Step 6, if applicable]
- Loop 1 completeness: [X]%
- Loop 2 completeness: [X]%
- ...
- Improvement trend: [improving / plateauing / diminishing returns]
```

### `loop_log.md` (append)

```markdown
## Loop [N] — [timestamp]
- **Completeness Score:** [X]%
- **Recommendation:** [CONTINUE/STOP]
- **Papers in Session:** [total count]
- **Claims Extracted:** [total count]
- **Contradictions Detected:** [total count]
- **Gaps Remaining:** [High: N, Medium: N, Low: N]
- **Key Gaps:** [1-2 sentence summary of biggest gaps]
```
