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

## Methods

| Method | Purpose |
|--------|---------|
| Data cleaning & validation | Handle Excel error tokens (`#N/A`, `#VALUE!`); verify pre-computed delta variable |
| Linear regression (OLS) | Predict magnitude of learning gains (continuous outcome) |
| Logistic regression | Model probability of any improvement (binary outcome) |
| Visualization (ggplot2) | Distributions, scatter plots, boxplots, logistic curves |

---

## Key Findings

- **Tutor usage is positively associated with learning gains**, but the effect is modest (Adjusted R² ≈ 0.18 in OLS model).
- **Pretest performance is the strongest predictor** — students who start with higher scores show smaller gains (ceiling effect), consistent with research on prior knowledge effects.
- **Tutor accuracy and request frequency** have positive coefficients but do not always reach statistical significance once pretest is controlled — suggesting that student baseline matters more than tutor usage alone.
- **Students who improved tend to use the tutor more** (higher median requests), but high usage among non-improving students likely reflects difficulty rather than effective engagement.

---

## Files

```
scripts/
└── Math3B.Rmd        # Full analysis — data cleaning, regression, visualization, conclusions

output/               # Generated report outputs
figures/              # Saved plots (if re-run)
```

---

## Tools & Stack

- **R** (tidyverse, dplyr, ggplot2, readxl)
- **R Markdown** (PDF and HTML output)
- **Statistical methods:** OLS regression, logistic regression, binary outcome classification

---

## Context

This analysis was conducted as part of my role as a Data Analyst & Research Assistant at Vocareum in collaboration with the UCSD Cognitive Science Lab. Findings were used to inform product decisions around AI tutor design and student engagement features.
