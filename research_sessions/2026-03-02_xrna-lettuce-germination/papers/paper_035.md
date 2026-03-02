# ALKBH10B, an mRNA m6A Demethylase, Modulates ABA Response During Seed Germination in Arabidopsis

## Metadata
- **Authors:** Tang J, Yang J, Lu Q, Tang Q, Chen S, Jia G
- **Year:** 2021
- **Source:** Frontiers in Plant Science
- **URL:** https://pmc.ncbi.nlm.nih.gov/articles/PMC8353332/
- **DOI:** 10.3389/fpls.2021.712713
- **PMID:** 34394161
- **Citation Count:** N/A
- **Source Database:** Cluster B — PubMed/PMC (WebSearch)

## Abstract
N6-methyladenine (m6A) is the most abundant and reversible chemical modification in eukaryotic mRNA. The expression of ALKBH10B, an m6A demethylase, is increased in response to abscisic acid (ABA), osmotic, and salt stress. The alkbh10b mutants showed hypersensitivity to ABA, osmotic, and salt stress during seed germination. Transcriptome analysis revealed that the expression of several ABA response genes is upregulated in alkbh10b-1 compared to wild type, indicating ALKBH10B negatively affects the ABA signaling. m6A sequencing showed that ABA signaling genes, including PYR1, PYL7, PYL9, ABI1, and SnRK2.2, are m6A hypermethylated in alkbh10b-1 after ABA treatment. This demonstrates a direct molecular link between m6A epitranscriptomics and ABA signaling during seed germination.

## Full Text Status
- [ ] Full text retrieved
- [x] Abstract only

## Full Text


---

## Deep Reading Notes

> **Note: Analysis based on abstract only. Evidence confidence is reduced.**

### Key Findings
- ALKBH10B is an mRNA m6A demethylase (eraser) in Arabidopsis — it removes m6A marks deposited by the writer complex (MTA/MTB/FIP37/VIR/HAKAI)
- ALKBH10B expression is INDUCED by ABA, osmotic stress, and salt stress — meaning the m6A eraser is activated under stress conditions
- alkbh10b loss-of-function mutants show HYPERSENSITIVITY to ABA, osmotic stress, and salt stress during seed germination — i.e., seeds germinate more poorly under stress when ALKBH10B is absent
- This indicates ALKBH10B normally acts to promote germination under stress by removing m6A marks from ABA signaling gene mRNAs, reducing their stability/expression
- Transcriptome analysis: several ABA response genes are UPREGULATED in alkbh10b-1 compared to wild type — loss of demethylase leads to higher expression of ABA response genes, strengthening ABA signaling
- m6A-seq revealed that key ABA signaling genes are m6A HYPERMETHYLATED in alkbh10b-1 after ABA treatment: PYR1 (ABA receptor), PYL7 (ABA receptor), PYL9 (ABA receptor), ABI1 (PP2C phosphatase), and SnRK2.2 (kinase in ABA signaling)
- The hypermethylated m6A peaks are predominantly in CDS (67.58%), then 3'UTR (15.72%) and 5'UTR (15.33%)
- ALKBH10B expression induction depends on ABI1 — creating a feedback loop between m6A erasure and ABA signaling
- GO/KEGG analysis: genes with hypermethylated m6A peaks in alkbh10b-1 are enriched in abiotic stress responses (water deprivation, cold, ABA, heat) and metabolic pathways (amino acid biosynthesis, pyruvate metabolism, plant hormone signal transduction)
- ALKBH10B had previously been shown to regulate floral transition (Duan et al. 2017), demonstrating it has developmental roles beyond stress

### Methodology
- **Study Type:** Primary research article (molecular biology/genetics/genomics)
- **Sample Size:** Not fully assessable from abstract; multiple mutant lines (at least alkbh10b-1)
- **Population/Model:** Arabidopsis thaliana — alkbh10b loss-of-function mutants vs. wild-type Col-0; seed germination assays under ABA/osmotic/salt stress
- **Key Methods:** Seed germination assays under varying ABA/osmotic/salt concentrations; RNA-seq (transcriptome analysis); m6A-seq (m6A-IP followed by sequencing); gene expression analysis; GO/KEGG pathway enrichment
- **Statistical Methods:** Not assessable from abstract; likely includes standard germination rate statistics and differential expression analysis with multiple testing correction
- **Duration:** Germination assays (typically 5-7 days); ABA treatment duration not specified in abstract

### Evidence Strength Assessment
- **Tier:** Silver (primary research with both transcriptomic and epitranscriptomic data; reduced from potential Gold due to abstract-only access)
- **Reasoning:** The paper provides a rare direct molecular link between m6A epitranscriptomics and ABA signaling during seed germination — a highly relevant finding for the research brief. The combination of genetic (mutant phenotyping), transcriptomic (RNA-seq), and epitranscriptomic (m6A-seq) approaches is strong. Published in Frontiers in Plant Science (respectable but not top-tier journal). The specific identification of ABA signaling genes (PYR1, PYL7, PYL9, ABI1, SnRK2.2) as m6A targets is a key mechanistic finding.
- **Risk of Bias:** Low-Medium — the study uses appropriate controls (WT vs. mutant) and orthogonal methods (RNA-seq + m6A-seq); however, single mutant characterization (alkbh10b only) without complementation data in abstract limits certainty

### Specific Claims

1. **Claim:** "ALKBH10B expression is increased in response to ABA, osmotic, and salt stress"
   - **Evidence:** Gene expression analysis (likely RT-qPCR) showing induced ALKBH10B transcript levels under stress
   - **Confidence:** Medium (abstract-only; exact fold changes and significance values not available)
   - **Section/Page:** Abstract

2. **Claim:** "alkbh10b mutants showed hypersensitivity to ABA, osmotic, and salt stress during seed germination"
   - **Evidence:** Germination assays showing reduced germination rates in alkbh10b-1 under stress conditions
   - **Confidence:** Medium (phenotype described but quantitative data not available from abstract)
   - **Section/Page:** Abstract

3. **Claim:** "ABA signaling genes including PYR1, PYL7, PYL9, ABI1, and SnRK2.2 are m6A hypermethylated in alkbh10b-1 after ABA treatment"
   - **Evidence:** m6A-seq (m6A-immunoprecipitation followed by sequencing) comparing alkbh10b-1 vs. WT under ABA
   - **Confidence:** Medium (specific genes identified, but peak calling parameters and statistical thresholds not available from abstract)
   - **Section/Page:** Abstract

4. **Claim:** "ALKBH10B negatively affects ABA signaling"
   - **Evidence:** Upregulation of ABA response genes in alkbh10b-1; hypersensitivity to ABA; inference that m6A removal by ALKBH10B destabilizes ABA signaling transcripts
   - **Confidence:** Medium (mechanistic inference from correlative data; direct causal chain not fully established in abstract)
   - **Section/Page:** Abstract

5. **Claim:** "ALKBH10B expression induction depends on ABI1"
   - **Evidence:** Gene expression analysis in abi1 mutant background (details not in abstract)
   - **Confidence:** Medium (described but not detailed in abstract)
   - **Section/Page:** Abstract

### Limitations
- **Stated by authors:** "Further studies are needed to explain the specific mechanism of how ALKBH10B modulates the expression of ABA response genes" — authors acknowledge that the mechanism linking m6A hypermethylation to gene expression changes is not fully resolved
- **Additional concerns:** (1) The paper shows what happens when the m6A ERASER is lost (increased m6A → increased ABA signaling → germination inhibition), but the xRNA model proposes downregulating the m6A WRITER (VIR). The opposite manipulation (reduced writer activity) should REDUCE m6A on ABA signaling genes, which based on this paper's logic would DECREASE ABA signaling transcript stability → promote germination. However, the relationship may not be perfectly symmetrical. (2) No data on which specific m6A sites on ABA genes are critical for mRNA stability vs. splicing vs. translation. (3) Arabidopsis-specific — lettuce ABA signaling pathway may differ. (4) The xRNA target is PP2C47 (a PP2C phosphatase like ABI1), which is one of the m6A targets identified here — creating a potentially confounding dual effect.

### Relevance to Research Brief
- **Directly addresses:** Research Questions 1 and 4. This paper is the most directly relevant to the core mechanistic question: "Would virilizer downregulation lead to reduced m6A marking → destabilization of specific transcripts → transcriptomic reprogramming favoring germination?"
  - The paper demonstrates that m6A marks ABA signaling transcripts (PYR1, PYL7, PYL9, ABI1, SnRK2.2)
  - When m6A is INCREASED on these transcripts (alkbh10b mutant), ABA signaling is strengthened and germination is inhibited
  - By logical extension, when m6A is DECREASED on these transcripts (e.g., via VIR downregulation), ABA signaling transcripts should be destabilized, weakening ABA response and potentially promoting germination
  - This is precisely the mechanism proposed in the research brief: VIR downregulation → reduced m6A → destabilization of ABA signaling transcripts → shifted ABA/GA balance → faster germination

- **Partially addresses:** Research Question 3 (defense reallocation) — the GO/KEGG enrichment shows m6A-regulated genes include stress response pathways; reducing m6A could destabilize defense/stress transcripts, freeing resources for growth.

- **Novel contribution:** This is the ONLY paper in this batch that directly links m6A to ABA signaling during SEED GERMINATION. It provides the molecular logic for why VIR downregulation could promote germination through the ABA pathway. The identification of specific ABA signaling genes (PYR1, PYL7, PYL9, ABI1, SnRK2.2) as m6A targets creates testable predictions for the xRNA model.

### Key References to Chase
- Duan HC et al. (2017). "ALKBH10B is an RNA N6-methyladenosine demethylase affecting Arabidopsis floral transition." — Why: Establishes ALKBH10B as a bona fide m6A demethylase; shows its role in development
- Zhong S et al. (2008). "MTA is an Arabidopsis messenger RNA adenosine methylase." — Why: Writer complex identification; essential context for understanding writer-eraser balance
- Shen L et al. (2016). "N6-methyladenosine RNA modification regulates shoot stem cell fate." — Why: Shows m6A-mediated mRNA stability control in developmental context
- Anderson SJ et al. (2018). "N6-methyladenosine inhibits local ribonucleolytic cleavage to stabilize mRNAs in Arabidopsis." — Why: Direct mechanism — m6A stabilizes mRNAs by inhibiting cleavage; this would mean VIR downregulation → reduced m6A → increased cleavage → destabilization of specific transcripts
- Ma Y et al. (2019). "The pivotal role of m6A in the ABA signaling." — Why: Additional evidence for m6A-ABA axis (if it exists)

### Connections to Other Session Papers
- Directly linked to paper_006 (Arribas-Hernandez & Brodersen review): The writer complex described in paper_006 deposits the m6A marks that ALKBH10B removes. Together, they establish the dynamic m6A landscape on ABA signaling genes during germination. The review's discussion of m6A promoting mRNA stability/degradation is the mechanism through which ALKBH10B's effects operate.
- Directly linked to paper_024 (Ruzicka et al. HAKAI): The writer complex (including VIR and HAKAI) from paper_024 is the opposing force to ALKBH10B. VIR downregulation by xRNA would phenocopy some aspects of ALKBH10B overexpression — both would reduce m6A on target mRNAs.
- Provides the mechanistic bridge to paper_044 (ECT1/germination): ALKBH10B removes m6A from ABA gene mRNAs, while ECT1 reads m6A on other germination-related mRNAs. The xRNA model predicts VIR downregulation would affect both pathways simultaneously — reducing m6A on ABA genes (promoting germination via ABA pathway weakening) AND reducing m6A on ECT1 targets like PHYB (potentially opposing germination via the GA pathway). This tension is central to the key question.
- Complements paper_025 (JMJ24/JMJ25): ALKBH10B operates at the RNA level (m6A erasure) while JMJ25 operates at the chromatin level (H3K9me2 erasure). Both are "erasers" in different epigenetic systems. IBM1/JMJ25 is required for defense gene expression, and ALKBH10B modulates ABA/stress genes — downregulation of both (as proposed in xRNA model) could converge on suppressing the stress transcriptome.
