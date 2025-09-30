# 📊 Complete Guide to A/B Testing (A → B)

This repository contains a reproducible, end-to-end A/B testing walkthrough using the Cookie Cats dataset. The analysis is implemented as a Jupyter Notebook (`complete-guide-to-a-b-testing-a-to-z.ipynb`) and demonstrates best practices for experiment design, preprocessing, hypothesis testing, and interpreting results.

---

## Project summary

- Goal: demonstrate how to design and analyse A/B tests for both binary (retention) and continuous (game rounds) outcomes.
- Includes: EDA, hypothesis formulation, sample-size calculations, randomization checks, statistical tests, confidence intervals, effect-size interpretation and visualization.

## Dataset

- File: `Cookie_Cats_cleaned_v01.csv`
- Main columns used:
  - `version` — experiment group (`gate_30` = control, `gate_40` = treatment)
  - `sum_gamerounds` — total game rounds per user (continuous, skewed)
  - `retention_1` — 1-day retention (0/1)
  - `retention_7` — 7-day retention (0/1)
- Size: ~90k users (approx.)

## Key questions / hypotheses

1. Continuous outcome — Has the average number of game rounds increased by a target lift?
2. Binary outcome (1-day retention) — Is there an increase in 1-day retention (e.g., +2%)?
3. Binary outcome (7-day retention) — Is there an increase in 7-day retention (e.g., +5%)?

Each hypothesis is evaluated with H0/H1, confidence intervals, p-values and discussion of practical significance.

## Methodology (high level)

- Data cleaning: missing values, types, and outlier handling (IQR trimming for `sum_gamerounds`).
- Randomization checks to ensure balance across `version` groups.
- Error rates: α = 0.05, target power = 0.80 (β = 0.20).
- Sample-size calculations for proportions and means; cross-checked with statsmodels.
- Tests used: two-sample z-test for proportions, two-sample t-test (Welch) for means, and non-parametric alternatives when appropriate.

## How to run

1. (Optional) Create and activate a virtual environment:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

2. Start Jupyter and open the notebook:

```bash
jupyter notebook complete-guide-to-a-b-testing-a-to-z.ipynb
```

3. Run the notebook cells in order. Cells are annotated with explanations and visualizations.

## Dependencies (typical)

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- statsmodels

If you'd like, I can create a `requirements.txt` with pinned versions.

## Outputs & files

- `complete-guide-to-a-b-testing-a-to-z.ipynb` — main analysis notebook
- `Cookie_Cats_cleaned_v01.csv` — cleaned input dataset
- `ab_summary.csv`, `ab_retention_detail.csv` — optional derived outputs

## Results (summary)

The notebook produces a concise, reproducible summary of experiment results. Typical outputs include:

- Descriptive statistics comparing control (`gate_30`) and treatment (`gate_40`) groups (means, medians, counts).
- Visualizations: distribution plots for `sum_gamerounds`, retention bar charts (1-day and 7-day), box/violin plots, and balance checks.
- Hypothesis test outputs: p-values, 95% confidence intervals, and effect-size estimates for each tested hypothesis (continuous and binary outcomes).
- Derived CSVs (`ab_summary.csv`, `ab_retention_detail.csv`) containing aggregated metrics and test results that can be used for reporting or downstream analysis.

Notes:

- The notebook emphasizes both statistical significance (p-values and CIs) and practical/business significance (lift, absolute difference, and expected impact).
- I intentionally did not hard-code final decisions in the README — please open the notebook to see the computed results and plots for your dataset.

## Contributing

Contributions welcome. Open an issue or submit a pull request for:

- Reproducible scripts to run the analysis (non-notebook)
- Improved preprocessing or power-simulation code
- Tests or CI to reproduce results automatically

Author: Vraj Shah

---



