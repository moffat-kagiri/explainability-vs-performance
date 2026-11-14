# Chapter 4 and discussion figure chunks

The figure script constructs ggplot objects in memory and does not write image files. Source it once in each chapter document, then print each required object in its own chunk. By default, the script is expected beside the `.Rmd`; if it remains in Downloads, the setup chunk falls back to `~/Downloads/chapter4_figures.R`. The results `.rds` files must be available from the notebook's working directory.

```{r figure-setup, include=FALSE}
figure_script <- Sys.getenv("CHAPTER4_FIGURES_R", "chapter4_figures.R")
if (!file.exists(figure_script)) {
  figure_script <- path.expand("~/Downloads/chapter4_figures.R")
}
if (!file.exists(figure_script)) {
  stop("Figure script not found: ", figure_script)
}
source(figure_script, local = knitr::knit_global())
```

## Recommended for Chapter 4: Findings

Place Figure 1 after the paired-bootstrap comparison of test deviance. It visualizes the direction and uncertainty of pairwise performance differences.

```{r fig1-paired-deviance-differences, fig.cap="Paired differences in mean test deviance, with 95% group-bootstrap intervals. Negative values favor the first model.", fig.width=7, fig.height=4.5, out.width="100%"}
fig1
```

Place Figure 2 immediately after the SHAP fidelity summary at the current line 264. It is the best fit there: it shows the relationship between predictive performance and SHAP faithfulness across models, with uncertainty in both dimensions.

```{r fig2-performance-versus-fidelity, fig.cap="Predictive performance versus SHAP faithfulness. Horizontal and vertical intervals show test-deviance and faithfulness uncertainty, respectively.", fig.width=7, fig.height=4.5, out.width="100%"}
fig2
```

Place Figure 3 with the test-performance results, after the calibration discussion. It shows calibration across predicted-risk deciles rather than only portfolio-wide calibration.

```{r fig3-calibration-by-risk-decile, fig.cap="Predicted-to-observed claims by predicted-risk decile; the dashed line indicates exact calibration.", fig.width=7, fig.height=4.5, out.width="100%"}
fig3
```

Place Figure 4 after the global SHAP-importance results. It compares average absolute attribution magnitudes across models.

```{r fig4-global-shap-importance, fig.cap="Mean absolute SHAP attribution by feature and model, measured in log-frequency units.", fig.width=7.5, fig.height=5, out.width="100%"}
fig4
```

Place Figures 5a–5c in the SHAP stability subsection, alongside the table of refit-stability metrics. The black marks indicate the explainer-noise reference level.

```{r fig5a-attribution-variability, fig.cap="Across-refit standard deviation in feature attributions, expressed as a premium-equivalent percentage. Black marks indicate explainer noise.", fig.width=7, fig.height=4.5, out.width="100%"}
fig5a
```

```{r fig5b-attribution-profile-distance, fig.cap="Attribution-profile distance across refits; larger values indicate more reallocation among features. Black marks indicate explainer noise.", fig.width=7, fig.height=4.5, out.width="100%"}
fig5b
```

```{r fig5c-attribution-sign-agreement, fig.cap="Agreement in attribution signs across refits for material contributions. Black marks indicate explainer noise.", fig.width=7, fig.height=4.5, out.width="100%"}
fig5c
```

Figure 5d belongs after the ANN stability results. It separates estimated attribution variance associated with refitting from variation associated with ANN training seed.

```{r fig5d-ann-variance-decomposition, fig.cap="Decomposition of ANN attribution variance into data sensitivity and training-seed variation.", fig.width=6.5, fig.height=2.5, out.width="90%"}
fig5d
```

## Appendix or supplemental discussion figures

Figure A1 is a visual companion to the fidelity-by-risk-decile table; put it in the appendix if the table already appears in the main text.

```{r figA1-shap-fidelity-by-risk-decile, fig.cap="Mean SHAP faithfulness correlation by predicted-risk decile. Deciles are defined using GBM-selected predicted risk.", fig.width=7.5, fig.height=4.5, out.width="100%"}
figA1
```

Figure A2 supports the LIME sensitivity analysis by comparing surrogate fit and local-rank stability across binning choices.

```{r figA2-lime-binning-sensitivity, fig.cap="LIME surrogate R-squared and local-rank stability under prespecified bins, LIME default bins, and no binning.", fig.width=8, fig.height=5, out.width="100%"}
figA2
```

Figures A3 and A3b document tuning choices underlying the locked GBM and ANN configurations. They are most useful in a methodological appendix or when discussing model-selection constraints.

```{r figA3-gbm-tuning-grid, fig.cap="Grouped-fold cross-validated GBM loss across the tuning grid. Outlined cells mark the selected and sensitivity configurations.", fig.width=8, fig.height=5, out.width="100%"}
figA3
```

```{r figA3b-ann-tuning-grid, fig.cap="ANN cross-validated loss across architectures and L2 penalties. Outlined cells mark the selected and sensitivity configurations.", fig.width=7, fig.height=4.5, out.width="100%"}
figA3b
```

Figure A4 supports the overfitting discussion by contrasting training and test metrics, but test results should remain the primary basis for model comparison.

```{r figA4-training-versus-test, fig.cap="Training and test deviance and Gini by model. Connectors link the two evaluation sets for each model.", fig.width=8, fig.height=4.5, out.width="100%"}
figA4
```

Figure A5 is useful in the discussion to make local explanations concrete. Treat the two policies as illustrative cases, not representative estimates for their risk deciles.

```{r figA5-example-shap-profiles, fig.cap="Feature-level SHAP profiles for illustrative policies from the lowest- and highest-risk deciles.", fig.width=8, fig.height=5, out.width="100%"}
figA5
```

## Discussion-chapter suggestions

The strongest discussion figures are Figure 2 (performance–fidelity relationship), Figures 5a–5d (whether explanation instability exceeds explainer noise, including ANN seed variation), and Figure A5 (examples of local attribution profiles). Use Figures A1, A2, A3, A3b, and A4 selectively or in an appendix to avoid repeating the Chapter 4 tables and plots. No separate discussion `.Rmd` was present when this guide was prepared; insert only the relevant chunks into that document when available.