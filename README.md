# explainability-vs-performance

**The Explainability–Performance Frontier in Insurance Risk Models: A Decision Framework for Actuarial Model Selection**

MSc Data Science Dissertation — University of East London (UEL-DS-7010)
Author: Kagiri | Supervisor: Dr. Konstantinos Vrachimis

> ⚠️ This is a working repository, updated as the project progresses through proposal, literature review, methodology, empirical work, and write-up. Expect frequent structural changes in the early phases.

---

## Project Summary

This project investigates the trade-off between predictive performance and explainability across three model classes commonly used in insurance risk modelling — **GLM**, **GBM**, and **Neural Networks**. Models are compared on:

- **Predictive performance**: Gini coefficient, log-likelihood
- **Explainability**: SHAP fidelity, LIME stability

The findings feed into a **multi-criteria decision framework** for actuarial model selection, intended to help practitioners weigh accuracy against interpretability in a defensible, structured way.

A secondary research thread examines whether **SHAP sensitivity variation across model classes constitutes measurable actuarial model risk**, connecting the XAI stability literature to model risk doctrine (model risk as data risk).

Regulatory frameworks (e.g. Solvency II, EU AI Act) are treated as **contextual scaffolding** rather than primary objects of analysis, per supervisor guidance.

---

## Current Status

🚧 **Phase 1: Foundation & Proposal** — in progress

Immediate priority: finalising the research proposal and establishing a solid literature review base to support topic justification and methodology choices.

See [Roadmap](#roadmap) below for the full six-phase plan.

---

## Dataset

**Status: under review.** The project was originally scoped around the **French Motor Third-Party Liability (MTPL)** dataset, but access/quality issues are being worked through. The dataset may change as the project develops — this section will be updated once finalised, along with any implications for methodology or scope.

---

## Repository Structure

*(will evolve as work progresses)*

```
explainability-vs-performance/
├── proposal/           # Research proposal drafts and supporting docs
├── literature/         # Literature review notes, synthesis tracking, seed papers
├── data/               # Raw/processed data (or data access notes, if not committed)
├── notebooks/          # Exploratory analysis, modelling experiments
├── src/                # Reusable code: preprocessing, modelling, SHAP/LIME pipelines
├── framework/           # Model selection decision framework development
└── writeup/            # Dissertation drafts by chapter
```

---

## Methodology (high level)

1. **Literature Review** — actuarial ML, XAI methods, SHAP/LIME stability, model risk, regulatory/governance context
2. **Data Preparation** — cleaning, feature engineering, train/test splits (dataset TBC, see above)
3. **Model Development** — GLM, GBM (LightGBM), Neural Network, tuned for comparable predictive performance
4. **Explainability Analysis** — SHAP fidelity and LIME stability across model classes
5. **Framework Development** — synthesise performance + explainability metrics into a multi-criteria decision framework
6. **Model Risk Thread** — assess whether SHAP sensitivity variation constitutes measurable model risk

---

## Roadmap

| Phase | Focus | Status |
|---|---|---|
| 1 | Foundation & Proposal | 🚧 In progress |
| 2 | Literature Review | ⏳ Not started |
| 3 | Methodology & Data | ⏳ Not started |
| 4 | Empirical Work | ⏳ Not started |
| 5 | Framework Development | ⏳ Not started |
| 6 | Writing & Submission | ⏳ Not started |

Writing proceeds concurrently with each phase — the introduction chapter is written last, once findings and framing are settled.

---

## References & Citation Style

- **Proposal**: APA 7
- **Dissertation body**: Harvard

Literature managed in Zotero; synthesis tracked separately (Author/Year | Core Argument | Relevance to RQs | Connects To).

---

## Notes / Changelog

- **2026-07-02**: Repo initialised. Proposal work underway; literature review being prioritised to support proposal. Dataset (French Motor MTPL) under review due to access issues — may switch.

---

## License

TBD
