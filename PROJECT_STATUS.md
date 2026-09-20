# Project Status

## Purpose
Build and evaluate baseline machine-learning models for highly imbalanced credit-card fraud detection.

## What works
- data understanding and duplicate audit
- preprocessing and scaling
- stratified train/test split
- Logistic Regression baseline
- Random Forest baseline
- fraud-class precision, recall, F1 and ROC-AUC reporting
- documented confusion matrices and business interpretation

## Deployment
Not deployed. The repository is currently best treated as an ML case study rather than a hosted application.

The newer `financial-fraud-detection-dashboard` repository is the stronger deployed fraud project, so duplicating the same idea here would add little portfolio value.

## API
No API is integrated.

## Current model snapshot
Random Forest:
- precision: 0.97
- recall: 0.73
- F1: 0.83
- ROC-AUC: 0.9239

Logistic Regression:
- precision: 0.85
- recall: 0.59
- F1: 0.70
- ROC-AUC: 0.9563

## Portfolio role
Strong evidence of imbalanced classification, fraud-specific evaluation, and progression toward the newer end-to-end fraud dashboard.

## Next improvements
- align the README project tree with files that are actually committed
- package preprocessing + model into one reproducible Pipeline
- add automated checks
- add a concise model card / limitations section
- avoid building another Streamlit app unless the inference workflow is meaningfully different
