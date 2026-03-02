# DELAY OF GERMINATION1 requires PP2C phosphatases of the ABA signalling pathway to control seed dormancy

## Metadata
- **Authors:** Nee G, Kramer K, Nakabayashi K, Yuan B, Xiang Y, Miatton E, Finkemeier I, Soppe WJJ
- **Year:** 2017
- **Source:** Nature Communications
- **URL:** https://www.nature.com/articles/s41467-017-00113-6
- **DOI:** 10.1038/s41467-017-00113-6
- **PMID:** 28706187
- **Citation Count:** N/A
- **Source Database:** Cluster A — WebSearch

## Abstract
This study demonstrates that DELAY OF GERMINATION1 (DOG1) controls seed dormancy by converging with ABA signaling at the level of clade A PP2C phosphatases. Four phosphatases interact with DOG1 in seeds, including two clade A PP2Cs: ABA-HYPERSENSITIVE GERMINATION 1 (AHG1) and AHG3. These phosphatases have redundant but essential roles in the release of seed dormancy, epistatic to DOG1. DOG1 acts upstream of AHG1 and impairs the PP2C activity of AHG1 in vitro. The ABA and DOG1 dormancy pathways converge at clade A PP2Cs. In the core ABA signaling mechanism, PP2Cs are key negative regulators: in the absence of ABA, PP2Cs dephosphorylate/inactivate SnRK2 kinases, suppressing ABA responses and allowing germination. In the presence of ABA, PYR/PYL receptors inhibit PP2C activity, activating SnRK2 kinases and maintaining dormancy. DOG1 provides a parallel inhibitory input on specific PP2Cs (especially AHG1), reinforcing dormancy independently of, but convergently with, ABA signaling. This dual regulation makes PP2Cs the critical integration point for hormonal (ABA) and genetic (DOG1) dormancy signals.

## Full Text Status
- [ ] Full text retrieved
- [x] Abstract only

## Full Text
N/A — WebFetch returned 403.

---

## Deep Reading Notes

> **Note: Analysis based on abstract only. Evidence confidence is reduced.**

### Key Findings
- DOG1 protein controls seed dormancy by converging with ABA signaling at the level of clade A PP2C phosphatases
- Four phosphatases interact with DOG1 in seeds; two are clade A PP2Cs: AHG1 and AHG3
- AHG1 and AHG3 have redundant but essential roles in the release of seed dormancy, and are epistatic to DOG1
- DOG1 acts upstream of AHG1 and impairs the PP2C activity of AHG1 in vitro — providing a parallel inhibitory input on PP2Cs independent of ABA-PYR/PYL receptor-mediated inhibition
- In the core ABA signaling model: no ABA → PP2Cs dephosphorylate/inactivate SnRK2 → no ABA responses → germination permitted; ABA present → PYR/PYL receptors inhibit PP2Cs → SnRK2 active → dormancy maintained
- DOG1 provides a second, ABA-independent mechanism to inhibit PP2Cs (especially AHG1), reinforcing dormancy
- PP2Cs are therefore the critical integration point for hormonal (ABA) and genetic (DOG1) dormancy signals

### Methodology
- **Study Type:** Molecular genetics / biochemistry (protein interaction, genetic epistasis, in vitro phosphatase assay)
- **Sample Size:** N/A (Arabidopsis genetic study)
- **Population/Model:** Arabidopsis thaliana seed dormancy mutants
- **Key Methods:** Co-immunoprecipitation/protein interaction screen, genetic epistasis analysis (dog1 vs. ahg1/ahg3 mutants), in vitro PP2C activity assay
- **Statistical Methods:** Not fully assessable from abstract
- **Duration:** N/A

### Evidence Strength Assessment
- **Tier:** Silver (downgraded from Gold due to abstract-only access)
- **Reasoning:** Published in Nature Communications (high-impact, peer-reviewed). Combines genetic epistasis with biochemical activity assays — strong evidence design. Multiple independent lines of evidence (interaction, epistasis, activity). However, full methodology and statistical details not accessible.
- **Risk of Bias:** Low — published in a top-tier journal with rigorous peer review; combines in vivo and in vitro approaches

### Specific Claims

1. **Claim:** "DOG1 controls seed dormancy by converging with ABA signaling at the level of clade A PP2C phosphatases"
   - **Evidence:** Protein interaction screen identified 4 phosphatases interacting with DOG1; genetic epistasis shows PP2Cs are downstream of DOG1
   - **Confidence:** Medium (abstract only, but multi-line evidence)
   - **Section/Page:** Abstract

2. **Claim:** "AHG1 and AHG3 have redundant but essential roles in the release of seed dormancy, epistatic to DOG1"
   - **Evidence:** Genetic epistasis analysis (ahg1/ahg3 mutants vs. dog1 mutant)
   - **Confidence:** Medium
   - **Section/Page:** Abstract

3. **Claim:** "DOG1 impairs the PP2C activity of AHG1 in vitro"
   - **Evidence:** In vitro phosphatase activity assay with purified DOG1 and AHG1
   - **Confidence:** Medium
   - **Section/Page:** Abstract

4. **Claim:** "The ABA and DOG1 dormancy pathways converge at clade A PP2Cs"
   - **Evidence:** Dual regulatory model: ABA → PYR/PYL → PP2C inhibition; DOG1 → direct PP2C inhibition. Both converge on same PP2C targets.
   - **Confidence:** Medium
   - **Section/Page:** Abstract

### CRITICAL ANALYSIS: PP2C Clade Identity and Implications for xRNA PP2C47 Targeting

**This paper establishes that clade A PP2Cs (AHG1, AHG3) are NEGATIVE REGULATORS of ABA signaling — they PERMIT germination by keeping SnRK2 inactive.**

The logic chain is:
- PP2C active → SnRK2 dephosphorylated/inactive → no ABA response → germination proceeds
- PP2C inhibited (by ABA-PYR/PYL or by DOG1) → SnRK2 active → ABA response ON → dormancy maintained

**Therefore: PP2C LOSS-OF-FUNCTION (LOF) or downregulation = constitutive SnRK2 activation = ABA hypersensitivity = ENHANCED DORMANCY = DELAYED germination**

This is the OPPOSITE of what the xRNA brief assumes. The brief states PP2C47 downregulation should accelerate germination. If PP2C47 is a clade A PP2C, its downregulation would DELAY germination by enhancing ABA signaling.

**Clade question:** The brief describes PP2C47 as a "negative regulator of ABA signaling via SnRK2 dephosphorylation" — this description matches clade A PP2Cs exactly. However, "PP2C47" as a numbering designation in genome-wide studies (e.g., Xue et al. 2008) refers to the 47th PP2C gene identified, and in Medicago truncatula PP2C47 maps to clade B (MAPK phosphatases, not ABA signaling). The clade assignment is SPECIES-DEPENDENT. In lettuce (Lactuca sativa), the gene called "PP2C47" could be from any clade depending on the genome annotation system used. The functional description in the brief ("SnRK2 dephosphorylation") unambiguously places it in clade A.

**Implication:** If PP2C47 in lettuce is indeed a clade A PP2C that dephosphorylates SnRK2, then xRNA-mediated downregulation would ENHANCE ABA signaling and DELAY germination — the opposite of the desired effect. This is a fundamental contradiction that must be resolved.

### Limitations
- **Stated by authors:** Not accessible from abstract
- **Additional concerns:** Study conducted in Arabidopsis; direct extrapolation to lettuce (Lactuca sativa) requires caution. Lettuce has a much larger genome and potentially different PP2C family composition. The DOG1-PP2C interaction may differ between species.

### Relevance to Research Brief
- **Directly addresses:** Research Question 1 (ABA/GA balance and PP2C47 role); the critical question of whether PP2C47 downregulation accelerates or delays germination
- **Partially addresses:** The broader ABA signaling mechanism relevant to lettuce thermoinhibition
- **Novel contribution:** Establishes that PP2C loss-of-function DELAYS germination (ABA hypersensitivity), directly contradicting the premise that PP2C47 downregulation accelerates germination. This is the single most important finding for evaluating the xRNA PP2C47 target.

### Key References to Chase
- Nee et al. (2017) cites the core ABA signaling papers establishing PYR/PYL-PP2C-SnRK2 module — foundational for understanding PP2C function
- Ma et al. (2009) "Regulators of PP2C phosphatase activity function as abscisic acid sensors" — original PYR/PYL receptor discovery
- Bentsink et al. (2006) original DOG1 gene identification — connects to lettuce dormancy biology
- Nakamura et al. (2007) AHG1 characterization — seed-specific PP2C regulation

### Connections to Other Session Papers
- Agrees with paper_005 on: clade A PP2C LOF = ABA hypersensitivity during germination
- Agrees with paper_020 on: PP2Cs as "gatekeepers" of SnRK2 activation via dephosphorylation
- Agrees with paper_021 on: SnRK2 kinases are essential for dormancy maintenance (loss = reduced dormancy)
- Extends paper_048 by: providing the genetic framework (DOG1-PP2C convergence) that paper_048 (MUSHER lncRNA) builds upon
- Contradicts brief's assumption that PP2C47 downregulation accelerates germination — if PP2C47 is clade A, its LOF should delay germination
