# Deep Research — Master Orchestrator

You are the research engine. When activated, you run the entire multi-phase research pipeline by spawning specialized agents, coordinating their work through the session folder, and iterating until the research is thorough.

## Activation

This skill is activated when the user asks a research question. See `CLAUDE.md` for activation criteria.

## Phase 1: UNDERSTAND

Parse the user's prompt into a structured research brief.

1. Identify the core research question(s)
2. Determine the domain: science, medicine, technology, finance, law, policy, general
3. Determine the research profile from user's language (see CLAUDE.md for profile table). Default to `balanced`.
4. Identify key concepts, entities, and relationships to investigate
5. Expand the prompt into 3-7 specific, answerable sub-questions

Create the session folder and write `brief.md`:

```bash
# Create the session folder
mkdir -p research_sessions/YYYY-MM-DD_slug-of-prompt/papers
```

Write `brief.md`:
```markdown
# Research Brief

## Original Prompt
[exact user prompt]

## Domain
[identified domain]

## Profile
[fast/balanced/deep/legendary]

## Core Research Questions
1. [primary question]
2. [sub-question]
3. [sub-question]
...

## Key Concepts
- [concept 1]: [brief definition/context]
- [concept 2]: [brief definition/context]
...

## Scope Boundaries
- **In scope:** [what we will investigate]
- **Out of scope:** [what we won't cover, to avoid scope creep]
```

Initialize `loop_log.md`, `search_log.md`, and `queries.md` as empty files with headers.

## Phase 2: EXPAND — Query Generation

Spawn a **query-strategist** agent:

```
Agent prompt:
"You are a query strategist. Read the skill file at .claude/skills/query-strategist/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}
- mode: initial
- profile: {profile}

Read brief.md from the session folder and generate search queries. Write them to queries.md."
```

Wait for completion. Read `queries.md` to verify queries were generated.

## Phase 3: SEARCH — Multi-Source Parallel Search

Read the queries from `queries.md`. Divide them across source clusters and spawn **3-5 literature-search agents in parallel**:

```
Agent A (General Web):
"You are a literature search agent. Read the skill file at .claude/skills/literature-search/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}
- source_cluster: A (General Web — use WebSearch)
- queries: [list the web-targeted queries]

Search for sources and save paper files to the papers/ folder. Log activity to search_log.md."

Agent B (PubMed + PMC):
"...source_cluster: B (PubMed + PMC)
- queries: [list the academic-targeted queries]..."

Agent C (Preprints + Open Access):
"...source_cluster: C (Preprints — bioRxiv, arXiv, CORE)
- queries: [list the preprint-targeted queries]..."

Agent D (Semantic Scholar + CrossRef):
"...source_cluster: D (Semantic Scholar + CrossRef)
- queries: [list the academic-targeted queries]..."

Agent E (Domain-Specific — only if relevant):
"...source_cluster: E (Domain-specific databases)
- queries: [list the domain-specific queries]
- Relevant databases for this topic: [list which K-Dense database skills to reference]..."
```

**All agents run in parallel.** Wait for all to complete.

After search completes, check the papers/ folder to see what was found. If very few papers were found (< 5), consider running additional searches with modified queries before proceeding.

## Phase 4: READ — Deep Comprehension

List all paper files in `papers/`. Spawn **parallel deep-reader agents** — one per paper:

```
For each paper file, spawn:
"You are a deep reader agent. Read the skill file at .claude/skills/deep-reader/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}
- paper_file: {paper_file_path}
- brief_path: {session_path}/brief.md

Read the paper, attempt full text retrieval if needed, and append structured deep reading notes to the paper file."
```

**Parallelism limits by profile:**
| Profile | Max parallel readers |
|---------|---------------------|
| fast | 5 |
| balanced | 8 |
| deep | 10 |
| legendary | 10 |

If there are more papers than the limit, batch them. Wait for each batch to complete before starting the next.

## Phase 5: EVALUATE — Evidence Assessment

Spawn an **evidence-evaluator** agent:

```
"You are an evidence evaluator. Read the skill file at .claude/skills/evidence-evaluator/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}

Read all paper files in the papers/ folder. Extract claims, assign evidence tiers, detect contradictions. Write claims.md and contradictions.md."
```

Wait for completion.

## Phase 6: CHASE — Citation Chain Traversal

Spawn a **citation-chaser** agent:

```
"You are a citation chaser. Read the skill file at .claude/skills/citation-chaser/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}
- max_hops: {1 for fast/balanced, 2 for deep/legendary}

Identify seed papers, follow citation chains forward and backward, add newly discovered relevant papers to the papers/ folder."
```

Wait for completion.

If new papers were added, spawn additional **deep-reader agents** for them (same as Phase 4, but only for the new papers).

## Phase 7: CRITIQUE — Gap Analysis

Spawn a **research-critic** agent:

```
"You are a research critic. Read the skill file at .claude/skills/research-critic/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}
- loop_number: {current loop number, starting at 1}

Read the entire session folder and produce a gap analysis. Write gaps.md and append to loop_log.md."
```

Wait for completion. Read `gaps.md` to get the completeness score and recommendation.

## Phase 8: LOOP OR STOP

Read `gaps.md`. Check the recommendation:

**STOP if ANY of these are true:**
- The critic recommends STOP
- Completeness score >= 90%
- Current loop >= max loops for this profile
- Diminishing returns detected (improvement < 5% across 2 consecutive loops)

**Max loops by profile:**
| Profile | Max Loops |
|---------|-----------|
| fast | 1 |
| balanced | 3 |
| deep | 8 |
| legendary | 15 |

**If CONTINUING:**
1. Spawn a **query-strategist** agent in `evolve` mode:
   ```
   "...mode: evolve, session_path: {session_path}, profile: {profile}
   Read gaps.md and generate evolved queries targeting the identified gaps. Append to queries.md."
   ```
2. Wait for completion
3. Go back to **Phase 3** with the new queries only (don't re-search old queries)
4. Continue through Phases 4-7 again with any new papers

**If STOPPING:** Proceed to Phase 9.

## Phase 9: SYNTHESIZE — Final Report

Spawn a **synthesis-writer** agent:

```
"You are a synthesis writer. Read the skill file at .claude/skills/synthesis-writer/SKILL.md for your full instructions.

Your task:
- session_path: {session_path}

Read the entire session folder and write a comprehensive final report to final_report.md."
```

Wait for completion.

## Phase 10: DELIVER

After the report is written:

1. Read the executive summary from `final_report.md`
2. Present to the user:
   - The path to the full report
   - The executive summary
   - Key statistics: number of sources, loops completed, completeness score
   - Any major caveats or limitations
3. Ask if they want to explore any section deeper or have follow-up questions

## Error Recovery

- If an agent fails or times out, log the error to `loop_log.md` and continue with remaining agents
- If a critical agent fails (evidence-evaluator or synthesis-writer), retry once
- If a search cluster returns zero results, log it but don't block the pipeline
- If the session folder has < 3 papers after all search agents complete, notify the user that the topic may be too niche for automated search and offer to continue with what was found

## Agent Spawning Best Practices

When spawning agents with the Agent tool:
- **Always include the full session path** so the agent knows where to read/write
- **Always point to the skill file** so the agent knows its full instructions
- **For parallel agents**, spawn all of them in a single message with multiple Agent tool calls
- **Give each agent a descriptive name** in the description field (e.g., "Search PubMed for queries", "Deep read paper_003")
- **Use background agents** for long-running tasks when you have other work to do in parallel
- **Use subagent_type: "general-purpose"** for all research agents — they need access to WebSearch, WebFetch, Read, Write, and other tools

## Timing Expectations

| Profile | Estimated Duration |
|---------|-------------------|
| fast | 2-5 minutes |
| balanced | 5-15 minutes |
| deep | 15-45 minutes |
| legendary | 45-120 minutes |

These are rough estimates. Quality matters more than speed.
