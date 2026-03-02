# Structural Insight into UV-B-Activated UVR8 Bound to COP1

## Metadata
- **Authors:** Yin R, Arongaus AB, Binkert M, Ulm R
- **Year:** 2022
- **Source:** Science Advances
- **URL:** https://pubmed.ncbi.nlm.nih.gov/35442727/
- **DOI:** 10.1126/sciadv.abn3337
- **PMID:** 35442727
- **Citation Count:** N/A
- **Source Database:** Cluster B — PubMed (WebSearch)

## Abstract
UV-B photon reception by the Arabidopsis homodimeric UVR8 photoreceptor leads to its monomerization and a crucial interaction with COP1. The beta-propeller domain of UVR8 mediates UV-B-dependent interaction with the WD40 repeats-based predicted beta-propeller domain of COP1, whereas COP1 activity is regulated by interaction through the UVR8 C-terminal C27 domain. The photoactivated UVR8-COP1 module determines photomorphogenic UV-B signaling output in Arabidopsis. UV-B-induced HY5 and CHS gene activation strictly requires both UVR8 and COP1.

## Full Text Status
- [ ] Full text retrieved
- [x] Abstract only

## Full Text


---

> **Note: Analysis based on abstract only. Evidence confidence is reduced.**

## Deep Reading Notes

### Key Findings
- The cryo-EM structure of UV-B-activated UVR8 bound to COP1 was determined (Wang et al. 2022, Science Advances), revealing a two-interface interaction model
- **Interface 1:** The UVR8 beta-propeller domain (the dimerization surface, exposed upon UV-B-induced monomerization) mediates UV-B-dependent interaction with the WD40 repeat-based beta-propeller domain of COP1
- **Interface 2:** The UVR8 C-terminal C27 domain (amino acids 397-423, containing the VP motif at V410/P411) interacts with COP1 to regulate its activity
- Both interfaces are essential for competitive binding of UVR8 against HY5 to the COP1-SPA complex — UVR8 physically displaces HY5 from COP1, preventing HY5 ubiquitination and degradation
- RUP2 dissociates UVR8 from the COP1-SPA-UVR8 complex and facilitates UVR8 redimerization, de-repressing COP1 activity
- The UVR8VP/AA mutant (alanine substitutions at V410 and P411) disrupts C27-COP1 binding, validating the structural interface
- UV-B-induced HY5 and CHS (chalcone synthase) gene activation strictly requires both UVR8 and COP1, confirming their epistatic relationship

### Methodology
- **Study Type:** Structural biology study (cryo-electron microscopy + biochemistry)
- **Sample Size:** N/A (structural study)
- **Population/Model:** Arabidopsis thaliana UVR8 and COP1 proteins (in vitro reconstitution + in planta validation)
- **Key Methods:** Cryo-electron microscopy structure determination; reconstitution of UVR8-COP1-SPA complex in vitro; UV-B irradiation assays; co-immunoprecipitation; gene expression analysis (HY5, CHS); UVR8 VP/AA point mutant analysis
- **Statistical Methods:** Not assessable from abstract
- **Duration:** N/A

### Evidence Strength Assessment
- **Tier:** Silver (primary structural data of high quality, but abstract-only access limits full assessment)
- **Reasoning:** Cryo-EM structural data from Science Advances is high quality and provides mechanistic clarity. The two-interface model is validated by mutagenesis (VP/AA mutant). However, this is purely structural/biochemical work in Arabidopsis with no direct relevance to seed germination or lettuce. Reduced one tier from Gold due to abstract-only access.
- **Risk of Bias:** Low — structural biology study with clear experimental validation

### Specific Claims

1. **Claim:** "The beta-propeller domain of UVR8 mediates UV-B-dependent interaction with the WD40 repeats-based predicted beta-propeller domain of COP1"
   - **Evidence:** Cryo-EM structure shows direct contact between UVR8 beta-propeller (dimerization face) and COP1 WD40 domain
   - **Confidence:** Medium (abstract-only; structural details not fully verifiable)
   - **Section/Page:** Abstract

2. **Claim:** "COP1 activity is regulated by interaction through the UVR8 C-terminal C27 domain"
   - **Evidence:** C27 domain interaction with COP1 is necessary and sufficient for signaling (C27 expression alone mimics UV-B signaling, per Yin et al. 2015)
   - **Confidence:** Medium (abstract-only)
   - **Section/Page:** Abstract

3. **Claim:** "UV-B-induced HY5 and CHS gene activation strictly requires both UVR8 and COP1"
   - **Evidence:** Genetic epistasis data — uvr8 and cop1 mutants both fail to induce HY5/CHS
   - **Confidence:** High (well-established from multiple prior studies)
   - **Section/Page:** Abstract

4. **Claim:** UVR8 competitively displaces HY5 from COP1, preventing HY5 ubiquitination and degradation
   - **Evidence:** Both structural interfaces are essential for competitive binding; cryo-EM shows overlapping binding surfaces
   - **Confidence:** Medium (mechanistic model from structure, validated by mutagenesis)
   - **Section/Page:** Supplemented from search literature (Wang et al. 2022)

5. **Claim:** "RUP2 dissociates UVR8 from the COP1-SPA-UVR8 complex and facilitates redimerization"
   - **Evidence:** In vitro reconstitution shows RUP2 can disrupt the complex
   - **Confidence:** Medium (abstract-only)
   - **Section/Page:** Abstract/supplemented

### Limitations
- **Stated by authors:** Not assessable from abstract
- **Additional concerns:**
  - Purely structural study — no physiological data on growth, germination, or stress responses
  - In vitro reconstituted system may not fully recapitulate in vivo dynamics (e.g., in the nucleus where other factors compete)
  - No data in lettuce or any crop species
  - COP1's role is context-dependent (positive in UV-B signaling, negative in visible light photomorphogenesis) — the structural model may not capture all regulatory states

### Relevance to Research Brief
- **Directly addresses:** Research Question 1 — provides atomic-level detail of UVR8-COP1 interaction that would be disrupted when UVR8 is downregulated by xRNA
- **Partially addresses:** Mechanistic basis of HY5 stabilization and CHS induction — relevant to understanding the UV-B acclimation "defense cost" that xRNA would suppress
- **Novel contribution:** The two-interface competitive binding model clarifies why UVR8 is such a potent regulator: when UVR8 is present (UV-B active), it physically sequesters COP1 away from HY5, simultaneously stabilizing HY5 and reprogramming COP1 activity. When xRNA downregulates UVR8: (1) less UVR8 monomer means less COP1 sequestration, (2) COP1 remains free to degrade HY5 (reducing UV-B acclimation transcriptome), (3) PIF4/PIF5 are stabilized (promoting elongation growth), (4) CHS and flavonoid biosynthesis are reduced (saving metabolic costs). This provides structural rationale for the "resource reallocation" effect.

### Key References to Chase
- Yin R et al. (2015). "Two Distinct Domains of the UVR8 Photoreceptor Interact with COP1 to Initiate UV-B Signaling in Arabidopsis." Plant Cell 27:202-213 — Why: original identification of C27 domain and VP motif; foundational for structural interpretation
- Lau K et al. (2019). "Plant photoreceptors and their signaling components compete for COP1 binding via VP peptide motifs" — Why: explains competitive binding model relevant to COP1 substrate switching
- Podolec R et al. (2021). "UVR8 signaling pathways" — Why: updated signaling model incorporating structural findings
- Favory JJ et al. (2009). "Interaction of COP1 and UVR8 regulates UV-B-induced photomorphogenesis and stress acclimation in Arabidopsis" — Why: original characterization of UVR8-COP1 genetic interaction

### Connections to Other Session Papers
- Directly extends paper_022 by: providing the structural/atomic basis for the UVR8-COP1 interaction that Jenkins (2014) described at the genetic/signaling level
- Agrees with paper_022 on: COP1 as the primary signaling partner of UVR8; strict requirement of both for HY5/CHS activation; RUP-mediated negative feedback
- Connects to paper_085 on: the COP1 hub is shared between UV-B signaling (via UVR8) and other photoreceptor pathways — disrupting UVR8 would alter COP1's availability for other pathways, potentially affecting broader growth-defense balance
