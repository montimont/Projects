# Credit Risk Modeling: Feature Selection

This module contains a **completed feature selection pipeline** for a credit risk scorecard project. It applies multiple statistical and algorithmic methods to evaluate the predictive strength, stability, and relevance of input features.

## Purpose

The goal is to identify features that are:
- Predictive of default behavior
- Statistically significant
- Stable across time
- Low in redundancy or multicollinearity

These features will then be used for logistic regression scorecard modeling and non-linear models such as XGBoost and Random Forest.

## Feature Selection Methods Used

This module applies **diverse selection techniques** to ensure robustness:

### 1. **XGBoost Importance**
- Ranks features based on gain contribution
- Captures non-linear and interaction effects

### 2. **Hoeffding’s D**
- Measures general statistical dependence (not limited to linear or monotonic relationships)

### 3. **Spearman Correlation**
- Identifies monotonic relationships between features and the binary target
- Flags variables with weak or noisy trends

### 4. **Variable Clustering (VC)**
- Groups highly correlated features and selects representatives
- Helps reduce multicollinearity

### 5. **Logistic Regression p-values**
- Filters based on statistical significance in a univariate logistic regression
- Supports conceptual soundness and interpretability

### 6. **Random Forest Importance**
- Provides alternate non-linear importance rankings
- Complements XGBoost insights

### 7. **Weight of Evidence / Information Value (WOE/IV)**
- Quantifies feature separation between good vs. bad outcomes
- Key tool in credit scorecard design

---

## Output

Each method produces a ranked list or importance score, enabling you to compare and consolidate decisions. Results are used downstream for:

- Scorecard modeling
- Monitoring (e.g., PSI/CSI)
- Interpretation and governance documentation

## Status

Completed and aligned for integration into modeling workflows.

---

