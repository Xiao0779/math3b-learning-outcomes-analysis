# Math 3B Learning Outcomes Analysis

**Course:** Math 3B (Calculus), Fall 2025  
**Platform:** Vocareum AI Tutoring System  
**Author:** Xiao Long — Data Analyst & Research Assistant, Vocareum / UCSD Cognitive Science Lab

---

## Overview

This project analyzes student learning outcomes from a live AI-powered math tutoring platform used by real students in a UC-affiliated Math 3B (Calculus) course. The goal is to understand how tutor usage patterns — including frequency of requests and response accuracy — relate to learning gains across the quarter.

**Data:** Student-level records from the full Fall 2025 quarter, including pretest scores, midterm grades, final grades, number of AI tutor interactions, and tutor accuracy. Raw data is not shared publicly (student privacy / proprietary to Vocareum).

---

## Research Questions

1. Does AI tutor usage frequency predict learning gains?
2. Does tutor accuracy predict whether students improve?
3. What role does prior knowledge (pretest score) play in learning outcomes?

---

## Notebooks

### `01_student_level_analysis.Rmd`
Student-level analysis of learning gains (Final − Pretest) across the full quarter.
- Data cleaning (handling Excel error tokens)
- Quantile-based student grouping (Low / Middle / High tutor usage and practice volume)
- **Linear regression:** AI tutor usage (R² ≈ 0.18) vs practice volume (R² ≈ 0.37) as predictors of learning gain
- **Logistic regression:** modeling probability of any improvement
- Binary outcome comparison: tutor usage by improvement group

### `02_question_level_mixed_effects.Rmd`
Question-level analysis using the full interaction log (one row per student–question attempt).
- Topic-level difficulty ranking across all course zones
- Identification of the 10 hardest individual questions
- OLS baseline vs **linear mixed-effects model** (lme4) with random student intercepts
- Random effects distribution: quantifying individual student heterogeneity

### `03_ml_prediction.ipynb` *(Python)*
ML-based prediction of learning improvement — extends the statistical analysis with supervised learning models.
- Feature engineering from interaction logs (pretest, tutor requests, practice volume, accuracy)
- Model comparison: **Linear Regression vs Random Forest vs Neural Network (MLP)**
- Best model: **Random Forest (R² ≈ 0.45)**, outperforming both LR and MLP
- Feature importance analysis confirming practice volume > tutor usage frequency
- 5 publication-quality visualizations (distributions, correlation heatmap, model comparison, predicted vs actual, feature importance)

---

## Key Findings

- **Practice volume is a stronger predictor than tutor usage** — total questions seen explains ~37% of variance in learning gains (R analysis) and ranks as top engagement feature in ML models.
- **Pretest score is the dominant predictor** in all models — a consistent ceiling effect where higher-starting students show smaller measured gains.
- **Random Forest outperforms Linear Regression and MLP** (R² 0.453 vs 0.421 vs 0.376) — nonlinear interactions between features matter.
- **Attempting questions matters more than accuracy** — activity volume is more predictive than correctness rate, supporting iterative learning theory.
- **Topic area drives question difficulty** — significant performance differences across course zones, independent of student ability.
- **Student heterogeneity is substantial** — mixed-effects random intercepts confirm individual baseline differences account for meaningful score variance.
- **High tutor usage among non-improving students likely signals difficulty**, not engagement — an actionable insight for platform intervention design.

---

## Files

```
scripts/
├── 01_student_level_analysis.Rmd       # R: OLS + logistic regression, student-level
├── 02_question_level_mixed_effects.Rmd # R: lme4 mixed-effects, question-level
└── 03_ml_prediction.ipynb              # Python: LR vs Random Forest vs MLP

figures/              # ML notebook output plots
output/               # R Markdown HTML reports
```

---

## Tools & Stack

**R:** tidyverse, dplyr, ggplot2, readxl, lme4, broom.mixed, R Markdown  
**Python:** pandas, numpy, scikit-learn, matplotlib, seaborn, Jupyter  
**Statistical methods:** OLS regression, logistic regression, linear mixed-effects models, Random Forest, MLP

---

## Context

This analysis was conducted as part of my role as a Data Analyst & Research Assistant at Vocareum in collaboration with the UCSD Cognitive Science Lab. Findings were used to inform product decisions around AI tutor design and student engagement features.
