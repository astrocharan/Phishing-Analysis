# Phishing-Analysis

Code for *Beyond 99.9% Accuracy: Feature Engineering and Dataset Artifacts in Phishing URL Detection*.

| Notebook | Contents |
|---|---|
| `Phishing_Analysis.ipynb` | All main experiments: feature configurations, cross-validation, statistical tests, cross-dataset validation, feature importance, SHAP, and computational cost |
| `Phishing_Analysis_TrivialBaseline.ipynb` | `https://www.` baseline across the six datasets |
| `Phishing_Analysis_PR_Curves.ipynb` | ROC and precision-recall curves |

## Errata

**Rank-biserial effect size.** `compare_models_wilcoxon` in `Phishing_Analysis.ipynb` computes the matched-pairs rank-biserial correlation as

```python
r = 1 - (2 * stat) / (n * (n + 1))
```

The correct formula is

```python
r = 1 - (4 * stat) / (n * (n + 1))
```

This affects one printed value. For RF (URL + HTML) vs. RF (All Features), the notebook prints r = 0.750. The correct value is r = 0.500 (W = 2.5, n = 4 non-tied folds). The manuscript reports the corrected value.
