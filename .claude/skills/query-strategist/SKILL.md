# Query Strategist

Generate diverse, high-quality search queries for a research session, and evolve them across loop iterations to target knowledge gaps.

## Trigger

You are invoked by the deep-research orchestrator with:
- `session_path`: Path to the research session folder
- `mode`: Either `initial` (first pass) or `evolve` (subsequent loops)
- `profile`: The research profile (fast/balanced/deep/legendary)

## Initial Query Generation (mode = initial)

Read `brief.md` from the session folder. Generate queries using ALL of the following strategies:

### Query Strategies

1. **Definitional** — "What is [X]?", "Define [X]", "[X] definition"
2. **Mechanistic** — "How does [X] work?", "Mechanism of [X]", "[X] pathway"
3. **Comparative** — "[X] vs [Y]", "Difference between [X] and [Y]", "[X] compared to [Y]"
4. **Temporal** — "Recent advances in [X] 2024-2026", "[X] latest research", "History of [X]"
5. **Causal** — "What causes [X]?", "Effects of [X] on [Y]", "[X] outcomes"
6. **Quantitative** — "Meta-analysis of [X]", "[X] statistics", "[X] prevalence rates"
7. **Controversial** — "Criticisms of [X]", "Limitations of [X]", "[X] debate"
8. **Expert-seeking** — "Leading researchers in [X]", "[X] review paper", "Seminal papers on [X]"
9. **Cross-domain** — "[X] applications in [adjacent field]", "[X] AND [unexpected domain]"
10. **Negation** — "Why [X] fails", "[X] negative results", "Against [X]"
11. **Methodology** — "[X] study design", "How to measure [X]", "[X] methodology review"
12. **Applied** — "[X] clinical applications", "[X] real-world use", "[X] implementation"

### Query Count by Profile

| Profile | Min Queries | Max Queries |
|---------|-------------|-------------|
| fast | 10 | 20 |
| balanced | 30 | 50 |
| deep | 50 | 100 |
| legendary | 100 | 300 |

### Query Formatting

For each query, include:
- The query text
- The strategy tag (e.g., `[mechanistic]`, `[comparative]`)
- Target source hint: `[web]`, `[academic]`, `[patent]`, `[clinical]`, `[database]`

### Synonym and Terminology Expansion

For every key concept in the brief:
- List common synonyms, abbreviations, and alternative names
- Include MeSH terms where applicable (for biomedical topics)
- Include both technical and lay terminology
- Generate queries using each variant

## Evolved Query Generation (mode = evolve)

Read `gaps.md` from the session folder. For each identified gap:

1. Understand what information is missing
2. Generate 5-15 targeted queries specifically designed to fill that gap
3. Use more specific Boolean operators: `"exact phrase"`, `AND`, `OR`, `NOT`
4. Try different terminology than previous iterations (read `queries.md` to avoid repetition)
5. Include queries that approach the gap from a different angle or discipline
6. Add source-specific queries (e.g., PubMed MeSH queries, patent classification codes)

Tag evolved queries with `[evolved-loop-N]` where N is the loop iteration number.

## Output

Write all queries to `queries.md` in the session folder.

Format:
```markdown
# Search Queries

## Generation Info
- Profile: [profile]
- Mode: [initial/evolve]
- Loop iteration: [N]
- Total queries: [count]

## Queries

### Definitional
1. [web] "What is [X]?"
2. [academic] "Define [X] in the context of [Y]"
...

### Mechanistic
...

### Evolved (Loop N) — Targeting Gap: [gap description]
...
```

When in `evolve` mode, APPEND to the existing queries.md, do not overwrite previous queries.
