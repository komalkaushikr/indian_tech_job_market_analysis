# Indian Tech Job Market — Salary Tier Classification

>  **Note:** This is a personal practice/learning project, not a production system or a claim of state-of-the-art results. It's built to sharpen my end-to-end ML skills — data cleaning, feature engineering, and multi-class classification — and to have a project I can explain in depth, not just run.

## Overview

This project predicts **salary tier** (5 classes) for tech jobs in India using job title, skills, experience, location, and company as features. The goal is practice with the full pipeline: cleaning messy real-world data, engineering features from categorical/text fields, and building a defensible multi-class classifier — along with being deliberate about avoiding common pitfalls like data leakage.

## Dataset

- **Source:** [Indian Tech Job Market 2026 | 23K+ Records](https://www.kaggle.com/datasets/shree0910/india-tech-job-market-2026-23k-records) (Kaggle)
- Originally 23,201 tech job listings scraped from Naukri.com across 10 cities and 6 roles.
- After cleaning (deduplication, handling missing values, filtering unusable rows), the working dataset is **~2,683 rows**.

## Problem Framing

- **Target:** Salary tier, a 5-class label derived from fixed LPA (Lakhs Per Annum) ranges.
  - *(Fill in your actual bins here, e.g.: Tier 1: 0–5 LPA · Tier 2: 5–10 LPA · Tier 3: 10–15 LPA · Tier 4: 15–25 LPA · Tier 5: 25+ LPA)*
- **Features:** Job title, skills, experience, location, company.
- **Why tiers instead of regression:** Framed as classification to practice multi-class evaluation (precision/recall per class, confusion matrices) and because salary data scraped from postings is often noisy/imprecise at the exact-number level — tiers are a more honest target than a specific figure.

## Approach So Far

1. **Data cleaning** — deduplication, missing value handling, filtering unusable/incomplete listings.
2. **Train/test split** — stratified split to preserve class balance across the 5 salary tiers, given likely class imbalance in raw job postings.
3. **Categorical encoding** *(in progress)* — deciding encoding strategy per feature based on cardinality (e.g. job title and company are high-cardinality; location is lower-cardinality), with care taken to fit any encoding that uses target information only on the training fold, to avoid leakage into the test set.

## Tools

`pandas` · `scikit-learn` · `matplotlib` / `seaborn`

## Status / Next Steps

- [x] Data cleaning
- [x] Stratified train/test split
- [ ] Categorical encoding
- [ ] Model training (baseline → tuned)
- [ ] Evaluation (per-class precision/recall, confusion matrix)
- [ ] Write-up of leakage checks and encoding decisions

## Limitations

- Dataset is scraped job-posting data, not verified compensation — salary tiers reflect what's listed, not necessarily what's actually paid.
- Sample size (~2,683 rows) is modest for a 5-class problem; results should be read as a learning exercise, not a market-representative model.
