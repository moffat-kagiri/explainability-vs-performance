# explainability-vs-performance

**The Explainability–Performance Frontier in Insurance Risk Models: A Decision Framework for Actuarial Model Selection**

MSc Data Science Dissertation — University of East London (UEL-DS-7010)
Author: Kagiri | Supervisor: Dr. Konstantinos Vrachimis

> ⚠️ This is a working repository, updated as the project progresses through proposal, literature review, methodology, empirical work, and write-up. Expect structural changes.

---

## Project Summary

This project investigates the trade-off between predictive performance and explainability across three model classes commonly used in insurance risk modelling — **GLM**, **GBM**, and **Neural Networks**. Models are compared on:

- **Predictive performance**: Poisson deviance, calibration (predicted / observed claims), Gini coefficient, log-likelihood
- **Explainability**: SHAP fidelity, LIME stability

The findings feed into a **multi-criteria decision framework** for actuarial model selection, intended to help practitioners weigh accuracy against interpretability in a defensible, structured way.

A secondary research thread examines whether **SHAP sensitivity variation across model classes constitutes measurable actuarial model risk**, connecting the XAI stability literature to model risk doctrine (model risk as data risk).

Regulatory frameworks (e.g. Solvency II, EU AI Act) are treated as **contextual scaffolding** rather than primary objects of analysis, per supervisor guidance.

---

## Current Status

🚧 **Phase 4: Empirical Work** — in progress

- ✅ Dataset finalised and prepared; train/test split and CV folds fixed (grouped by covariate profile)
- ✅ GLM fitted (Poisson, log-exposure offset)
- ✅ GBM tuned (LightGBM, grouped CV) and configuration locked before any test-set evaluation
- 🚧 Neural network: design and tuning next
- ⏳ Combined test-set evaluation of all three models (run once, after the ANN is fixed)
- ⏳ SHAP / LIME analysis

See [Roadmap](#roadmap) below for the full six-phase plan.

---

## Dataset

French Motor Third-Party Liability (MTPL) claim frequency data (freMTPL2freq): 677,991 policies, with claim counts, exposure, and vehicle, driver and geographic covariates. Raw data are not committed to the repository (see `.gitignore`).

### Train/test split and cross-validation

Many records share identical covariate values, plausibly the same policyholder observed over several exposure periods. Under a random split, 35.6% of test rows had an exact covariate-profile match in the training data, which would inflate the performance of flexible models more than that of a GLM.

The split and cross-validation are therefore **grouped by covariate profile**:

- 90/10 train/test split, whole profile groups assigned to one side (seed 2026); zero train/test profile overlap
- 5-fold CV with folds assigned by group and stratified by claim occurrence, shared across all tuned models
- The same split is used for the GLM, GBM and ANN

Limitation: with no customer ID, identical covariates are only a proxy for the same policyholder, so some leakage may remain.

---

## Repository Structure

*(will evolve as work progresses)*

```
explainability-vs-performance/
├── proposal/           # Research proposal drafts and supporting docs
├── literature/         # Literature review notes, synthesis tracking, seed papers
├── data/               # Raw/processed data (not committed; access notes only)
├── notebooks/          # Exploratory analysis, modelling experiments
├── src/                # Reusable code: preprocessing, modelling, SHAP/LIME pipelines
├── framework/          # Model selection decision framework development
└── writeup/            # Dissertation drafts by chapter
```

Key committed artefacts: `test_idx.rds` (test-set row indices) and `model_selection_locked.rds` (GBM configuration chosen from CV before test evaluation).

---

## Methodology (high level)

1. **Literature Review** — actuarial ML, XAI methods, SHAP/LIME stability, model risk, regulatory/governance context
2. **Data Preparation** — cleaning, feature engineering, grouped train/test split and CV folds (see Dataset)
3. **Model Development**
   - **GLM**: Poisson regression with log link and `log(Exposure)` offset
   - **GBM**: LightGBM with Poisson objective and exposure offset (`init_score`). Deterministic grid over `num_leaves` and `min_data_in_leaf` (`max_depth = -1`, other parameters at defaults), early stopping on grouped CV folds. Selection rule fixed before test evaluation: the simplest configuration (fewest total leaves, i.e. leaves per tree × trees) within one standard error of the best CV score; the best-CV configuration is reported as a sensitivity case
   - **Neural network**: Poisson loss with exposure offset, same split and folds, small pre-declared tuning grid
4. **Evaluation** — all three models scored once on the untouched test set (Poisson deviance, calibration)
5. **Explainability Analysis** — SHAP fidelity and LIME stability across model classes
6. **Framework Development** — synthesise performance + explainability metrics into a multi-criteria decision framework
7. **Model Risk Thread** — assess whether SHAP sensitivity variation constitutes measurable model risk

---

## Reproducibility

- Split seed: 2026. CV folds and LightGBM seed: 42 (`deterministic = TRUE`)
- LightGBM version: 4.7.0
- The ungrouped-fold GBM grid was kept only as a comparison to show the effect of leakage-aware CV; it is not used in model comparison

---

## Roadmap

| Phase | Focus | Status |
|---|---|---|
| 1 | Foundation & Proposal | TBC |
| 2 | Literature Review | TBC |
| 3 | Methodology & Data | ✅ Data, split and GBM tuning done |
| 4 | Empirical Work | 🚧 In progress (ANN next) |
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
- **2026-10-28**: Dataset confirmed (freMTPL2freq). Split and CV redone by covariate-profile group after finding 35.6% train/test profile overlap under a random split. LightGBM grid rerun on grouped folds; GBM configuration locked before test evaluation. Neural network is next.

---

## License

TBD
