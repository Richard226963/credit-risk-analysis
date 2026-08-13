# Credit Risk Analysis

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![pandas](https://img.shields.io/badge/pandas-2.x-150458?style=flat-square&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-1.x-013243?style=flat-square&logo=numpy&logoColor=white)](https://numpy.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.x-0091BD?style=flat-square)](https://xgboost.ai/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat-square&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![CRISP-DM](https://img.shields.io/badge/Methodology-CRISP--DM-6C5CE7?style=flat-square)](https://en.wikipedia.org/wiki/Cross-industry_standard_process_for_data_mining)

Predicting loan default risk for a fintech lending business — end-to-end binary
classification following the **CRISP-DM** framework, from messy raw data to a
production-ready model comparison.

> Final project, Case 1 — Inteligo ID 2026 Data Science Bootcamp.

## Highlights

- **Best model: Logistic Regression** — strong baseline that beats the complex models
- **Clean, real-world data pipeline** — handles messy Indonesian currency formats
  (`Rp`, `IDR`, `%`, comma decimals), missing values, and feature engineering
- **Full CRISP-DM structure** — business understanding → data → EDA → modeling → evaluation

## Results

| Model | Accuracy | Precision (Default) | Recall (Default) | F1 (Default) | ROC-AUC | PR-AUC |
|---|---|---|---|---|---|---|
| **Logistic Regression** | **0.760** | 0.727 | 0.777 | **0.751** | **0.845** | **0.811** |
| Random Forest | 0.732 | 0.680 | **0.803** | 0.736 | 0.827 | 0.785 |
| XGBoost | 0.746 | **0.717** | 0.751 | 0.734 | 0.821 | 0.782 |

## Repository structure

```
credit-risk-analysis/
├── Credit_Risk_Prediction_Notebook.ipynb   # full analysis (35 cells, CRISP-DM)
├── README.md
└── data/
    └── case1_credit_risk.csv               # 2,500 borrowers × 15 features
```

## Dataset

`data/case1_credit_risk.csv` — 2,500 loan records, 15 columns:

`customer_id, usia, jenis_kelamin, pendidikan, status_pekerjaan, pendapatan_tahunan_idr,
jumlah_pinjaman_idr, tenor_bulan, tujuan_pinjaman, credit_score, jumlah_pinjaman_aktif,
rasio_utang_pendapatan, riwayat_telat_bayar, nilai_agunan_idr, status_kredit`

- **Target:** `status_kredit` — `Default` / `Tidak Default` (binary)
- Numeric fields arrive with Indonesian formatting and are cleaned in the notebook

## Approach

1. **Data cleaning** — strip `Rp`/`IDR`/`%` formatting, convert to numeric, drop duplicates
2. **Exploratory analysis** — target distribution, univariate & bivariate analysis, correlation heatmap
3. **Feature engineering** — missing-value flags, loan-to-income ratio, monthly installment (PTI), log transforms
4. **Modeling** — Logistic Regression (baseline), Random Forest, XGBoost; stratified 80/20 split, standard scaling
5. **Evaluation** — accuracy, precision/recall/F1, ROC-AUC, PR-AUC, 5-fold cross-validation

## Getting started

```bash
git clone https://github.com/Richard226963/credit-risk-analysis.git
cd credit-risk-analysis
jupyter notebook Credit_Risk_Prediction_Notebook.ipynb
```

Or run it in [Google Colab](https://colab.research.google.com/) — the notebook reads
`data/case1_credit_risk.csv` relative to the repo root.

**Requirements:** `pandas`, `numpy`, `matplotlib`, `seaborn`, `scikit-learn`, `xgboost`

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost
```

## Notes

- The presentation deck and QA materials from the original submission are intentionally
  excluded — this repository contains the code and data only.
- Notebook text is in Indonesian; figures and evaluation outputs are self-explanatory.
