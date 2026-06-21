# Credit Risk Modeling — Data Preparation

This module contains the **completed data preparation stage** for an end-to-end credit risk modeling pipeline. It structures raw data into model-ready development, validation, and holdout sets, and prepares features for both linear (e.g., logistic regression) and non-linear (e.g., tree-based) models.

## Key Steps

- **Data Splitting**  
  Stratified split into:
  - Development set (70%)
  - Validation set (20%)
  - Holdout set (10%)  
  These splits support model building, tuning, and future score monitoring.

- **Univariate Feature Prep**  
  Creates a cleaned version of the dataset for logistic regression and scorecard-based models optimized for:
  - WoE transformation
  - IV filtering
  - Missing value handling

- **Multivariate Feature Prep**  
  Builds a parallel dataset for use in XGBoost, Random Forest, etc., keeping original variable structure for models that manage correlation and nonlinearity.

## Role in the Overall Pipeline

This module feeds directly into:
- Feature selection (XGBoost importance, Spearman, Hoeffding D)
- Variable smoothing (next phase)
- Scorecard training and evaluation
- Monitoring for drift (PSI/CSI)

## Status

Completed and stable, ready for modeling steps downstream.

---


