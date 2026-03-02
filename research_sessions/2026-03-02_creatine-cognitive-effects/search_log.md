# Search Log

## Search: 2026-03-02T00:01 — Query 1
- **Cluster:** A (General Web)
- **Query:** "creatine supplementation cognitive effects definition and overview"
- **API/Tool:** WebSearch
- **Results Found:** 10
- **Papers Saved:** paper_001.md (Xu et al. 2024 — Frontiers systematic review/meta-analysis), paper_002.md (Kreider & Stout 2021 — Nutrients review)
- **Duplicates Skipped:** 0
- **Notes:** Rich search summary returned. Multiple results from PMC/PubMed. WebFetch failed with HTTP 403 on all attempted URLs (Frontiers, PMC). Mayo Clinic result noted but not saved (general consumer page, not research source).

## Search: 2026-03-02T00:01 — Query 2
- **Cluster:** A (General Web)
- **Query:** "creatine compared to other nootropics for cognitive enhancement"
- **API/Tool:** WebSearch
- **Results Found:** 10
- **Papers Saved:** None new (Xu et al. 2024 already captured; nootropics blog sites not suitable as primary sources)
- **Duplicates Skipped:** 2 (Avgerinos et al. 2018 PMC6093191, Xu et al. 2024 PMC11275561)
- **Notes:** Several commercial nootropics sites appeared (jinfiniti.com, nootropicsexpert.com, becomelucid.com, nootropicsdepot.com). These provided useful context on creatine vs. other nootropics but are not primary research sources. ScienceDirect critical perspective article (S0022316625004687) identified and tracked for paper_004 area.

## Search: 2026-03-02T00:01 — Query 3
- **Cluster:** A (General Web)
- **Query:** "creatine cognition research latest findings 2024 2025 2026"
- **API/Tool:** WebSearch
- **Results Found:** 10
- **Papers Saved:** paper_004.md (EFSA 2024 health claim evaluation), paper_005.md (Gordji-Nejad et al. 2024 — single dose creatine/sleep deprivation), paper_006.md (Smith et al. 2025 — Alzheimer's pilot)
- **Duplicates Skipped:** 2 (Xu et al. 2024 appeared again; Avgerinos et al. 2018 appeared again)
- **Notes:** Identified Marshall et al. 2026 (Nutrition Reviews) on creatine and cognition in aging — not saved as a separate paper but noted. Also identified CONCRET-MENOPA 2025 RCT on menopausal women — noted but not saved due to 6-paper limit. EFSA evaluation is especially significant as a regulatory assessment.

## Search: 2026-03-02T00:01 — Query 4
- **Cluster:** A (General Web)
- **Query:** "limitations of creatine for cognitive enhancement criticisms negative findings"
- **API/Tool:** WebSearch
- **Results Found:** 10
- **Papers Saved:** paper_003.md (Forbes et al. 2024 — systematic review finding creatine fails to support theoretical basis)
- **Duplicates Skipped:** 4 (Xu et al. 2024, EFSA 2024, Avgerinos et al. 2018, Forsberg et al. 2023 already tracked)
- **Notes:** Identified Machado 2025 (SAGE) on BBB challenge — integrated key points into paper_006.md notes. Critical perspective from Journal of Nutrition (S0022316625004687) — key arguments noted. Forsberg et al. 2023 (largest RCT, BMC Medicine) identified: found essentially null results with Bayesian evidence for only a small effect; side effects 4.25x more frequent with creatine vs placebo. This study's findings are captured in paper context notes.

## Search: 2026-03-02T00:01 — Query 5
- **Cluster:** A (General Web)
- **Query:** "how does creatine supplementation increase brain creatine levels MRS spectroscopy"
- **API/Tool:** WebSearch
- **Results Found:** 10
- **Papers Saved:** None new (Smith et al. 2025 already captured; Kreider review already captured)
- **Duplicates Skipped:** 3 (Gordji-Nejad et al. 2024, KUMC press release for Smith et al. 2025, Kreider & Stout review)
- **Notes:** Key MRS findings integrated across papers: Dechent et al. 1999 (pioneering MRS study, 8.7% avg increase), Lyoo et al. 2003 (multinuclear MRS, 8-9% increase), dose-response data from Kondo et al. showing 4.6-9.1% increases at 2-10 g/day. GAA supplementation (16.2% brain creatine increase) noted as alternative approach. BBB permeability limited by SLC6A8 transporter operating near saturation.

## WebFetch Attempts
- **All WebFetch calls failed with HTTP 403 errors**
- Attempted URLs: Frontiers, PMC (x2), Nature Scientific Reports, EFSA Wiley, Springer, KUMC, Hapres, MDPI, JN Nutrition
- Fallback: Used comprehensive WebSearch summaries to populate paper files
- All papers marked as "Abstract only" in full text status

## Summary — Cluster A
- **Total unique papers saved:** 6 (paper_001 through paper_006)
- **Total duplicates detected and skipped:** ~11 across all queries
- **Full texts retrieved:** 0 (all WebFetch attempts returned 403)
- **Key gap:** Full text retrieval was not possible; all paper files rely on WebSearch summaries which were fortunately quite detailed

---

## Search: 2026-03-02T00:05 — Cluster B, Query 1
- **Cluster:** B (PubMed + PMC)
- **Query:** "meta-analysis creatine supplementation cognitive performance"
- **API/Tool:** WebSearch (PubMed E-utilities API returned 403 — eutils.ncbi.nlm.nih.gov not on proxy allow-list; curl also failed; fell back to WebSearch)
- **Results Found:** 10 results returned
- **Papers Saved:** paper_020.md (Xu et al. 2024 — Frontiers in Nutrition meta-analysis), paper_021.md (Prokopidis et al. 2023 — Nutrition Reviews meta-analysis), paper_022.md (Avgerinos et al. 2018 — Experimental Gerontology systematic review)
- **Duplicates Skipped:** 0 (first Cluster B query; cross-cluster duplicates with Cluster A noted — Xu 2024 appears in both clusters but saved with different paper numbers to preserve cluster separation)
- **Notes:** WebSearch provided detailed effect sizes (SMD, CI, I², p-values), sample sizes, and methodology details. All three meta-analyses/systematic reviews identified are the core evidence base for this research question.

## Search: 2026-03-02T00:05 — Cluster B, Query 2
- **Cluster:** B (PubMed + PMC)
- **Query:** "systematic review creatine cognition effect size healthy participants"
- **API/Tool:** WebSearch (fallback from PubMed E-utilities)
- **Results Found:** 10 results returned
- **Papers Saved:** None new (all top results were duplicates of Query 1 papers)
- **Duplicates Skipped:** 3 within cluster (Xu 2024, Prokopidis 2023, Avgerinos 2018 already captured)
- **Notes:** Surfaced EFSA Scientific Opinion (2024) — critical methodological review that identified double-counting issue in Xu et al. meta-analysis. Also identified Forbes et al. (2025) systematic review on older adults and a 2025 Frontiers corrigendum correcting Xu et al. processing speed results.

## Search: 2026-03-02T00:05 — Cluster B, Query 3
- **Cluster:** B (PubMed + PMC)
- **Query:** "effects of creatine supplementation on memory executive function processing speed healthy adults"
- **API/Tool:** WebSearch (fallback from PubMed E-utilities)
- **Results Found:** 10 results returned
- **Papers Saved:** paper_023.md (Forsberg et al. 2023 — BMC Medicine, largest RCT), paper_024.md (Forbes et al. 2023 — Brain Sciences dose-response), paper_025.md (Gordjinejad et al. 2024 — Scientific Reports single-dose sleep deprivation)
- **Duplicates Skipped:** 3 within cluster (Xu 2024, Prokopidis 2023, Avgerinos 2018)
- **Notes:** Most productive query for individual RCTs. Forsberg et al. is the largest RCT to date with essentially null frequentist results (Cohen's d = 0.09-0.17). Forbes dose-response study found null results even at 20g/day. Gordjinejad et al. uniquely combines behavioral + 31P-MRS neuroimaging evidence.

## Search: 2026-03-02T00:05 — Cluster B, Query 4
- **Cluster:** B (PubMed + PMC)
- **Query:** "creatine monohydrate impact on working memory and attention human study"
- **API/Tool:** WebSearch (fallback from PubMed E-utilities)
- **Results Found:** 10 results returned
- **Papers Saved:** None new (all relevant results already captured)
- **Duplicates Skipped:** 5 within cluster (Xu, Prokopidis, Avgerinos, Forbes, Gordjinejad)
- **Notes:** Additionally surfaced Babakhani et al. (2025) — 6-week RCT of CrM (10g/d) with/without GAA in 66 healthy adults showing some benefits on sustained attention (Digit Vigilance test). Also surfaced EFSA health claim evaluation (PMC11574456). Not saved as separate papers to stay within 4-6 paper target.

## Search: 2026-03-02T00:05 — Cluster B, Query 5
- **Cluster:** B (PubMed + PMC)
- **Query:** "creatine supplementation no effect cognition null results healthy adults"
- **API/Tool:** WebSearch (fallback from PubMed E-utilities)
- **Results Found:** 10 results returned
- **Papers Saved:** None new (all relevant results already captured)
- **Duplicates Skipped:** 4 within cluster (Xu, Avgerinos, Forsberg, Forbes)
- **Notes:** Key additional null-result sources identified: (1) Behavioural Brain Research 2024 systematic review — "somewhat equivocal results"; (2) Journal of Nutrition 2025 critical review — "two of the largest and most rigorous trials found no clinical benefit"; (3) Multicenter Parkinson's trial (>1700 patients) terminated early for futility after 5 years. These are critical for evidence evaluation and will be noted in claims/contradictions analysis.

---

## Summary — Cluster B Search Activity
- **Total queries executed:** 5
- **Total unique papers saved:** 6 (paper_020.md through paper_025.md)
- **Total duplicates skipped within cluster:** 15
- **Cross-cluster duplicates noted:** Xu et al. 2024 and Gordjinejad et al. 2024 also appear in Cluster A paper files — retained in both clusters for completeness
- **Paper types saved:** 2 meta-analyses, 1 systematic review, 3 individual RCTs (1 positive under stress, 2 null in healthy young adults)
- **Full text access:** 0/6 (all blocked by network proxy — abstract-level data from WebSearch)
- **API access issue:** PubMed E-utilities API (eutils.ncbi.nlm.nih.gov) is not on the proxy allow-list. Both WebFetch and curl returned HTTP 403. All data was obtained via WebSearch as fallback, which provided substantial detail.

### Papers Saved — Cluster B
| File | Authors | Year | Type | Journal | Key Finding |
|------|---------|------|------|---------|-------------|
| paper_020.md | Xu et al. | 2024 | Meta-analysis (16 RCTs, n=492) | Frontiers in Nutrition | Memory SMD=0.31; executive function NS |
| paper_021.md | Prokopidis et al. | 2023 | Meta-analysis (10 RCTs) | Nutrition Reviews | Memory SMD=0.29; large effect in elderly (SMD=0.88) |
| paper_022.md | Avgerinos et al. | 2018 | Systematic review (6 RCTs, n=281) | Experimental Gerontology | Short-term memory + reasoning improved; most domains conflicting |
| paper_023.md | Forsberg et al. | 2023 | RCT (largest to date) | BMC Medicine | Null frequentist results; Cohen's d=0.09-0.17 |
| paper_024.md | Forbes et al. | 2023 | RCT (dose-response, n=30) | Brain Sciences | Null results at 10g/d and 20g/d in young adults |
| paper_025.md | Gordjinejad et al. | 2024 | RCT (single dose + MRS) | Scientific Reports | Positive during sleep deprivation; 31P-MRS mechanism |
