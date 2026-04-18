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

---

## Key Findings

- **Practice volume is a stronger predictor than tutor usage** — total questions seen explains ~37% of variance in learning gains vs ~18% for tutor requests alone.
- **Pretest score is the dominant predictor** in all models — a consistent ceiling effect where higher-starting students show smaller measured gains.
- **Topic area drives question difficulty** — significant performance differences across course zones, independent of student ability.
- **Student heterogeneity is substantial** — mixed-effects random intercepts confirm that individual baseline differences account for meaningful score variance, making OLS inadequate for question-level data.
- **High tutor usage among non-improving students likely signals difficulty**, not engagement — an actionable insight for platform intervention design.

---

## Files

```
scripts/
├── 01_student_level_analysis.Rmd       # OLS + logistic regression, student-level
└── 02_question_level_mixed_effects.Rmd # lme4 mixed-effects, question-level

output/               # Generated report outputs
figures/              # Saved plots (if re-run)
```

---

## Tools & Stack

- **R** (tidyverse, dplyr, ggplot2, readxl, lme4, broom.mixed)
- **R Markdown** (HTML output with floating TOC)
- **Statistical methods:** OLS regression, logistic regression, linear mixed-effects models (random intercepts)

---

## Context

This analysis was conducted as part of my role as a Data Analyst & Research Assistant at Vocareum in collaboration with the UCSD Cognitive Science Lab. Findings were used to inform product decisions around AI tutor design and student engagement features.
