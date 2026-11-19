## Dissertation Writing Plan

### UEL-DS-7010 \| MSc Data Science Dissertation

------------------------------------------------------------------------

**Topic (stated for orientation)**

*The Explainability-Performance Frontier in Insurance Risk Models: A Decision Framework for Actuarial Model Selection*

**Research Questions**

1.  How do predictive performance and explanation fidelity co-vary across GLM, GBM, and Neural Network model classes on French MTPL insurance data?
2.  Can a structured multi-criteria framework operationalise model selection under actuarial and regulatory constraints?
3.  Does SHAP sensitivity variation across model classes constitute measurable actuarial model risk?

------------------------------------------------------------------------

### Constraints from the Brief

- **10,000 words** ± 10% (excluding references and appendices)
- **Harvard referencing** throughout the dissertation body (a change from APA in the proposal)
- **Summative** — 100% of the module grade; passing grade is 50%
- **Format**: Arial, size 12, 1.5 line spacing, page numbers centred in the footer
- **File types accepted**: PDF or Word (.docx)
- Structure: Preliminary Pages → Introduction → Review of the Literature → Methodology → Findings → Discussion (may span limitations, conclusion, recommendations) → References → Appendices
- Submitted via Turnitin; draft submission recommended first to check originality
- Individual assessment — supervisor sign-off targeted for **16 October** (per the agreed timetable)

The dissertation is roughly 3.3× the length of the proposal, but the marking weight shifts: Content (40) and Critical Analysis (10) now dominate, alongside Structure/Presentation (20), Language (10), Level of Competency (10), and Referencing (10). Every expanded section should visibly deepen critical engagement, not just add words.

------------------------------------------------------------------------

### Building on the Proposal

The proposal's approved Table of Contents becomes the skeleton for the Introduction, Literature Review, and Methodology chapters. Each subsection below is expanded, not rewritten from scratch — the proposal drafts are the starting point.

| Proposal Section (word count in ToC) | Dissertation Chapter | Status |
|----|----|----|
| Introduction (p.4) | Chapter 1: Introduction | Expand |
| Purpose of the Study | §1.1 | Expand |
| Importance of the Study | §1.2 | Expand |
| Scope | §1.3 | Expand |
| Preliminary Literature Review (p.7) | Chapter 2: Review of the Literature | Expand significantly |
| Predictive Analytics in Risk Pricing | §2.1 | Expand |
| Model Complexity and Performance | §2.2 | Expand |
| Model Risk | §2.3 | Expand |
| Explainability and XAI Methods | §2.4 | Expand |
| Research Gap | §2.5 | Expand, sharpen |
| Experimental Design and Methodology (p.13) | Chapter 3: Methodology | Expand with implementation detail |
| Research Design | §3.1 | Expand |
| Dataset | §3.2 | Expand |
| Model Specifications | §3.3 | Expand |
| Evaluation Framework | §3.4 | Expand |
| Proposed Timetable (p.16) | — | Retained as project management record, not a dissertation chapter |
| *(new)* | Chapter 4: Findings | Write from scratch — depends on empirical results |
| *(new)* | Chapter 5: Discussion, Limitations, Conclusion, Recommendations | Write from scratch |

------------------------------------------------------------------------

### Section-by-Section Plan

------------------------------------------------------------------------

**Step 1 — Preliminary Pages** - Title Page (module code, supervisor, submission date, university) - Table of Contents (update page numbers once final) - List of Tables - List of Figures - List of Abbreviations (GLM, GBM, SHAP, LIME, MTPL, IAA, SR 11-7, etc.)

*No word count. Rebuild once chapter structure is stable — leave until last.*

------------------------------------------------------------------------

**Step 2 — Chapter 1: Introduction (approximately 1,200 words)**

Builds directly on the approved proposal Introduction. Re-open with a short background/problem framing (folded into §1.0, not separately headed in the proposal ToC but necessary scaffolding for a standalone dissertation chapter), then carry forward the three approved subsections:

- **§1.0 Background and Problem Statement** *(new framing, \~300 words)*
  - Restate the shift from GLM to GBM/Neural Network pricing models and the resulting opacity problem
  - Sharpen the falsifiable gap: no validated multi-criteria framework integrates performance, explanation fidelity, and model risk
- **§1.1 Purpose of the Study** *(expand from proposal, \~300 words)*
  - Restate all three research questions explicitly
  - Reaffirm the study does not aim to crown a universally superior model class
- **§1.2 Importance of the Study** *(expand from proposal, \~300 words)*
  - Professional, academic, and regulatory significance — strengthen with any new supervisor feedback received since the proposal
- **§1.3 Scope** *(expand from proposal, \~300 words)*
  - Confirm the three model classes, single dataset, and SHAP/LIME-only explanation scope
  - State exclusions explicitly (Random Forest as a footnote possibility only, regulatory frameworks as scaffolding not primary analysis)

------------------------------------------------------------------------

**Step 3 — Chapter 2: Review of the Literature (approximately 2,400 words)**

The proposal's preliminary literature review (900 words) was necessarily compressed. Each subsection now needs full critical engagement — not just citation-stacking, but comparison, tension-holding, and explicit linkage back to the research questions.

- **§2.1 Predictive Analytics in Risk Pricing** *(\~450 words)*
  - GLMs as the actuarial pricing standard; why predictive accuracy and interpretability have historically coexisted
  - Extend with more precedent (Henckaerts et al., Noll et al., Wüthrich & Buser) and critical comparison, not just listing
- **§2.2 Model Complexity and Performance** *(\~500 words)*
  - Empirical evidence for GBM/Neural Network performance gains
  - Critically weigh performance gains against interpretability costs — where does the literature disagree?
- **§2.3 Model Risk** *(\~500 words)*
  - Define model risk via SR 11-7 and IAA guidance
  - Argue complexity amplifies model risk; develop the discrimination-vs-bias tension (Wüthrich & Buser) further than the proposal did
- **§2.4 Explainability and XAI Methods** *(\~600 words)*
  - SHAP and LIME mechanics (Lundberg & Lee; Ribeiro et al.)
  - Critical treatment of instability findings (Slack et al., Alvarez-Melis, Visani) — this is where model risk and explainability intersect, so give it real weight
  - Regulatory basis: Solvency II, GDPR, EU AI Act — as scaffolding, not the analytical centre
- **§2.5 Research Gap** *(\~350 words)*
  - Sharpen the gap statement from the proposal into its final form
  - Explicitly state how each research question responds to a specific piece of the gap

*Every subsection should end closer to the gap than the proposal version did. This chapter's job has shifted from "make the RQs feel inevitable" to "prove you've engaged critically enough to justify them."*

------------------------------------------------------------------------

**Step 4 — Chapter 3: Methodology (approximately 2,200 words)**

Expands the proposal's Experimental Design and Methods section with full implementation detail — this is where "practical element" credit is earned.

- **§3.1 Research Design** *(\~300 words)*
  - Quantitative, empirical, controlled comparative design using secondary data
  - Restate why this design answers all three RQs
- **§3.2 Dataset** *(\~500 words)*
  - CASdatasets French MTPL: full structure (frequency and severity components), variable definitions
  - Data quality handling: missing values, exposure variable treatment, class imbalance
  - Preprocessing pipeline: feature engineering, train/test split, cross-validation strategy
  - Ethical considerations: anonymised public data, no PII
- **§3.3 Model Specifications** *(\~600 words)*
  - GLM: Poisson frequency / Gamma severity — formal specification
  - GBM: LightGBM — hyperparameters, tuning approach
  - Neural Network: architecture, layers, regularisation
  - Justify each choice against the literature reviewed in Chapter 2
- **§3.4 Evaluation Framework** *(\~800 words)*
  - Predictive performance metrics: Gini coefficient, log-likelihood, RMSE — formal definitions
  - Explanation fidelity: SHAP consistency score across repeated subsamples
  - Explanation stability: LIME instability index (variance of local approximations)
  - Multi-criteria decision matrix: scoring weights, regulatory scenario construction — this is the core original contribution, so give it the most space and precision

------------------------------------------------------------------------

**Step 5 — Chapter 4: Findings (approximately 1,900 words)**

New chapter — written only once empirical modelling work is complete (Phases 3–5 of the timetable).

- **§4.1 Predictive Performance Results** *(\~500 words)*
  - Gini, log-likelihood, RMSE across GLM, GBM, Neural Network — tables and figures
- **§4.2 Explanation Fidelity Results** *(\~500 words)*
  - SHAP consistency scores across model classes
- **§4.3 Explanation Stability Results** *(\~400 words)*
  - LIME instability index results
- **§4.4 Decision Matrix Output** *(\~500 words)*
  - The scored multi-criteria matrix itself — the dissertation's primary deliverable — presented in full with weighting rationale

*Findings should be reported neutrally here — interpretation and argument belong in Chapter 5.*

------------------------------------------------------------------------

**Step 6 — Chapter 5: Discussion, Limitations, Conclusion, Recommendations (approximately 2,100 words)**

New chapter. The brief allows this to span multiple sub-themes within one chapter.

- **§5.1 Discussion** *(\~900 words)*
  - Interpret findings against each research question in turn
  - Tie explanation fidelity/stability results back to the model risk literature (§2.3–2.4) — is SHAP sensitivity measurable model risk?
  - Compare against Henckaerts et al., Noll et al., and other precedent results
- **§5.2 Limitations** *(\~400 words)*
  - Three model classes, single dataset — acknowledge generalisability limits
  - Regulatory frameworks used as scaffolding only — note as a bounded scope decision, not an oversight
- **§5.3 Conclusion** *(\~400 words)*
  - Directly answer all three research questions
  - Restate the core contribution: a structured, evidence-based, repeatable model selection framework
- **§5.4 Recommendations** *(\~400 words)*
  - For actuarial practice: how a firm might adopt the decision matrix
  - For future research: proprietary data validation, Random Forest as a robustness check, additional XAI methods

------------------------------------------------------------------------

**Step 7 — References**

- **Harvard style throughout** — this is a deliberate change from the proposal's APA 7th Edition; recheck every carried-over citation from the proposal for reformatting
- Every in-text citation must appear in the reference list and vice versa
- Not included in the word count — expand as needed for full academic rigour
- Pull from the existing Zotero library; expect the reference count to roughly double from the proposal's 10–12 as Chapters 4–5 add new sources

------------------------------------------------------------------------

**Step 8 — Appendices (optional, not counted in word limit or grade)**

- Full SHAP/LIME plots not included in the main body
- Extended model hyperparameter tables
- Code excerpts or repository link (GitHub: explainability-vs-performance)

------------------------------------------------------------------------

### Word Budget

| Chapter | Target Words |
|----|----|
| Chapter 1: Introduction | 1,200 |
| Chapter 2: Review of the Literature | 2,400 |
| Chapter 3: Methodology | 2,200 |
| Chapter 4: Findings | 1,900 |
| Chapter 5: Discussion, Limitations, Conclusion, Recommendations | 2,100 |
| **Total** | **9,800** |

That leaves roughly 200 words of buffer against the 10,000-word ceiling (before the ±10% allowance is even applied) — enough room for connective material between chapters without risking an overrun.

------------------------------------------------------------------------

### Timetable Cross-Reference

The writing plan maps onto the previously agreed schedule (Weeks 7–19, 20 July – 15 October, submission 16 October):

| Phase | Weeks | Dissertation Deliverable |
|----|----|----|
| 1 | 7–8 | Chapter 2 full draft (literature review) |
| 2 | 9 | Chapter 3 data/preprocessing notes |
| 3 | 10–11 | Chapter 3 model specification subsections |
| 4 | 12–13 | Chapter 3 evaluation framework subsections |
| 5 | 14–15 | Chapter 4 (findings, decision matrix) |
| 6 | 16–18 | Full first draft: Chapters 1, 4, 5 complete; all chapters integrated |
| 7 | 19 | Proofreading, Turnitin check, final submission |
