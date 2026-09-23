# Sleep Stage Patterns as Non-Invasive Biomarkers for Early Alzheimer's Disease Risk Screening

A machine learning project exploring whether sleep architecture (from polysomnography) and cognitive assessment scores can help screen for early Alzheimer's disease risk, without invasive or costly diagnostic procedures.

Originally completed as an independent research project for BA889 (Boston University, Summer 2026).

## Overview

- Built a 3-class classifier (Cognitively Normal / MCI / Alzheimer's Disease) using cognitive assessment and demographic data from **ADNI** (Alzheimer's Disease Neuroimaging Initiative)
- Independently analyzed sleep architecture data from **SHHS** (Sleep Heart Health Study, via NSRR) to explore age-related changes in sleep and their potential link to cognitive decline
- Compared Logistic Regression, Random Forest, and XGBoost; the tuned Random Forest achieved a macro AUC-ROC of **0.8925**
- Feature importance showed MMSE and ADAS-Cog total score as the strongest predictors

## Data

This repository does **not** include the underlying datasets, since both require a data use agreement / access approval:

- **ADNI**: apply for access at [adni.loni.usc.edu](https://adni.loni.usc.edu)
- **SHHS / NSRR**: apply for access at [sleepdata.org](https://sleepdata.org)

To reproduce the analysis, download the ADNI Diagnostic Summary, MMSE, ADAS-Cog, and Subject Demographics files, plus the SHHS harmonized dataset, and update the file paths in the notebook to point to your own data location.

## Repository contents

- `Sleep_Stage_Patterns_...ipynb` — full analysis pipeline: data preprocessing, exploratory data analysis, feature selection, model training/tuning, and evaluation
- Research paper (PDF) — write-up of methods, results, and discussion

## Methods summary

- **ADNI preprocessing**: baseline visits only, merged across 4 files, group-wise median imputation for missing ADAS scores → 1,887 participants (736 CN, 857 MCI, 294 AD)
- **SHHS preprocessing**: baseline visits only, restricted to ages 40–89 → 5,576 participants
- **Models**: Logistic Regression, Random Forest, XGBoost, with 5-fold GridSearchCV tuning and `class_weight='balanced'` to address class imbalance

## Results

| Model | AUC-ROC |
|---|---|
| Logistic Regression | 0.881 |
| Random Forest | 0.888 |
| XGBoost | 0.885 |
| **Random Forest (Tuned)** | **0.8925** |
| XGBoost (Tuned) | 0.891 |

## Tech stack

Python, pandas, scikit-learn, XGBoost, matplotlib, seaborn (developed in Google Colab)

## Author

Suji Kim — MS Business Analytics, Boston University Questrom School of Business
