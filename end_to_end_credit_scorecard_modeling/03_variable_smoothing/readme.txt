# Credit Risk Modeling: Variable Smoothing

This module performs **variable smoothing and binning** for continuous and categorical features in preparation for credit scorecard modeling.

## Purpose

The goal is to:
- Smooth noisy or irregular relationships between features and the target
- Ensure **monotonicity** for logistic regression compatibility
- Create interpretable bins aligned with Weight of Evidence (WOE) transformation
- Preserve key information while reducing overfitting and volatility

Smoothing is critical in credit modeling, where explainability, regulatory alignment, and production stability are top priorities.

## Key Components

### 1. Binning Strategy
- Quantile-based or domain-driven cuts
- Merges low-frequency or unstable bins
- Adjusts for minimum bin size and target rate contrast

### 2. Smoothing Logic
- Combines adjacent bins with similar default rates
- Enforces monotonic increasing or decreasing trend with respect to the target
- Reduces “jumps” in the relationship caused by noise or rare events

### 3. Evaluation Metrics
- Displays smoothed vs. raw bad rate plots
- Optionally computes WOE and IV per bin for stability checks
- Outputs smoothed bin edges and assignments for downstream modeling

---

## Output

- Cleaned, monotonic versions of key input variables
- Bin edges saved for future mapping or deployment
- Visual plots showing the impact of smoothing
- Prepared inputs for WOE encoding and scorecard modeling

## Status

**Completed and aligned.** This module is ready for integration with scorecard development pipelines.


