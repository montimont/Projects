# Hybrid Machine Learning Model for Credit Risk Classification

This project develops a **hybrid model** that integrates a rule-based heuristic with a machine learning classifier to enhance accuracy, interpretability, and fairness in credit risk prediction.

It combines transparent decision rules with a logistic regression model trained on demographic and financial indicators, ensuring both predictive performance and explainability for regulated domains such as lending and fraud prevention.

---

<details>
<summary><strong>1. Project Overview</strong></summary>

**Objective:**  
Build a hybrid system that predicts credit approval or rejection by combining domain logic (employment stability rule) with statistical learning (logistic regression).

**Dataset:**  
Credit applicant data including demographic, employment, and income information.  
- Total records: 1,548  
- After cleaning: 1,496  
- Target: `label` (0 = Approved / Low Risk, 1 = Rejected / High Risk)

**Key Innovation:**  
Integrates a **rule-based employment threshold** with a **tuned logistic regression model**, improving recall on minority (high-risk) cases while maintaining interpretability.

</details>

---

<details>
<summary><strong>2. Data Preparation and Feature Engineering</strong></summary>

- Merged applicant features with labels on `Ind_ID`.  
- Removed 523 incomplete records and dropped `Type_Occupation` due to >30% missing values.  
- Created derived features:  
  - `Age = -Birthday_count / 365`  
  - `Years_Employed = -Employed_days / 365`  
  - `Currently_Unemployed = (Employed_days > 0)`  
- Verified no duplicates; all categorical variables encoded consistently.  
- Final dataset shape: **(1496, 18)**.

</details>

---

<details>
<summary><strong>3. Exploratory Data Analysis (EDA)</strong></summary>

**Target Distribution:**  
- Approved (0): 1,336  
- Rejected (1): 160  
→ Imbalanced data (~10.7% high-risk cases).

**Insights:**  
- Shorter employment history and lower income correlate with rejection.  
- Married, property-owning applicants show higher approval rates.  
- Education and `Type_Income` strongly influence outcomes.  
- Binary indicators (`Mobile_phone`, `Phone`, `EMAIL_ID`) show little variance.

</details>

---

<details>
<summary><strong>4. Statistical Feature Significance</strong></summary>

Used **ANOVA F-test (SelectKBest)** to rank numeric predictors.

**Top Features by Significance:**

| Rank | Feature | p-value |
|------|----------|---------|
| 1 | Years_Employed | 0.0007 |
| 2 | Birthday_count | 0.1027 |
| 3 | Age | 0.1027 |
| 4 | Family_Members | 0.316 |
| 5 | Ind_ID | 0.320 |

**Conclusion:**  
`Years_Employed` is the strongest single discriminator of credit risk, motivating its use as a rule in the hybrid model.

</details>

---

<details>
<summary><strong>5. Rule-Based Baseline Model</strong></summary>

A simple heuristic was built using `Years_Employed`:

**Rule A:**  
If `Years_Employed ≥ 20.1 → Approved (0)`  
Else → Rejected (1)

**Performance:**

| Metric | Score |
|---------|--------|
| Accuracy | 0.85 |
| Recall (Low Risk) | 0.95 |
| Recall (High Risk) | 0.04 |

**Interpretation:**  
The rule is highly precise for approvals but fails to detect most risky applicants — ideal for combination with a statistical model.

</details>

---

<details>
<summary><strong>6. Categorical Encoding & Multicollinearity Reduction</strong></summary>

- Encoded 7 categorical variables via **One-Hot Encoding**.  
- Dropped redundant columns:  
  - `Birthday_count`, `Employed_days` (correlated with `Age`, `Years_Employed`)  
  - `Mobile_phone`, `Ind_ID`, `CHILDREN`, `Work_Phone`, `Phone`  
- Conducted **VIF analysis** to ensure independence — all VIF < 5.  
- Removed highly correlated features:  
  `Type_Income_Pensioner`, `EDUCATION_Secondary / secondary special`

**Final Feature Count:** 24 predictors.

</details>

---

<details>
<summary><strong>7. Model Training & Hyperparameter Optimization</strong></summary>

**Model:** Logistic Regression (scikit-learn)

- Scaled numerical features using Min–Max normalization.  
- Addressed imbalance with `class_weight='balanced'`.  
- Tuned parameters via **RandomizedSearchCV (5-fold Stratified CV)**.

**Best Hyperparameters:**
```
C = 2.34
max_iter = 1062
solver = 'lbfgs'
class_weight = 'balanced'
```

**Performance:**

| Metric | Score |
|---------|--------|
| Accuracy | 0.62 |
| Precision (High Risk) | 0.14 |
| Recall (High Risk) | 0.50 |
| F1 Score (High Risk) | 0.22 |
| AUC | 0.60 |

**Key Outcome:**  
Balanced detection of high-risk applicants without major loss in interpretability.

</details>

---

<details>
<summary><strong>8. Precision–Recall and Threshold Tuning</strong></summary>

- Evaluated thresholds between 0.05 and 0.90.  
- At **threshold = 0.50**, recall = 0.50 and precision = 0.14.  
- Lowering threshold to **≈0.20** increases recall (up to 0.50–0.60) with acceptable precision loss.

**Average Precision (AP):** 0.21  
→ Indicates limited precision but reasonable trade-off for recall optimization in imbalanced datasets.

</details>

---

<details>
<summary><strong>9. Feature Importance and Interpretability</strong></summary>

Top coefficients from logistic regression:

| Feature | Coefficient | Impact |
|----------|--------------|--------|
| Years_Employed | -2.31 | Lower risk |
| Housing_type_House / apartment | -1.85 | Lower risk |
| Type_Income_Working | -1.44 | Lower risk |
| EDUCATION_Lower secondary | +1.63 | Higher risk |
| Marital_status_Single / not married | +1.47 | Higher risk |
| Age | -1.12 | Lower risk |

**Interpretation:**  
Employment stability, home ownership, and higher education correlate with approval, while youth, lower education, and single status increase rejection risk.

</details>

---

<details>
<summary><strong>10. Hybrid Decision Framework</strong></summary>

**Logic:**
1. **Rule A Override:**  
   - If `Years_Employed < 0.2 (scaled)` → Auto classify as Fraud (High Risk).  
2. **Logistic Regression:**  
   - Applied to remaining cases using tuned probability threshold.

**Outputs:**
- Predicted label (`Fraud` / `Genuine`)  
- Fraud probability  
- Decision source (Rule or Model)  
- Confidence level (High / Moderate)

**Example Output:**
```
Predicted Label     : Fraud
Fraud Probability   : 1.0
Decision Source     : Triggered Rule A (Years_Employed below threshold)
Model Confidence    : High
```

This hybrid logic enhances fairness by combining hard interpretability rules with probabilistic reasoning.

</details>

---

<details>
<summary><strong>11. Model Serialization and Deployment</strong></summary>

All components saved as a single artifact:
```python
model_artifact = {
    "scaler": scaler,
    "logreg_model": best_model,
    "logreg_model_threshold": 0.50
}
joblib.dump(model_artifact, "model.joblib")
```

This enables reproducible inference, batch predictions, and portability to production environments.

</details>

---

<details>
<summary><strong>12. Batch Prediction Utility</strong></summary>

Implements `hybrid_batch_predict(df_input)` to process multiple records simultaneously.

**Outputs:**
- `Predicted_Label`
- `Fraud_Probability`
- `Decision_Threshold`
- `Decision_Source`
- `Model_Confidence`

**Example Results:**

| Predicted_Label | Fraud_Probability | Decision_Source | Confidence |
|------------------|-------------------|-----------------|-------------|
| Fraud | 1.0 | Rule A | High |
| Genuine | 0.42 | Model | Moderate |

</details>

---

<details>
<summary><strong>13. Tech Stack</strong></summary>

- Python 3.10  
- pandas, numpy, seaborn, matplotlib  
- scikit-learn, statsmodels  
- imbalanced-learn, joblib  
- Jupyter / Google Colab  

</details>

---

<details>
<summary><strong>14. Project Structure</strong></summary>

```
Hybrid_Model_Credit_Risk/
│
├── hybrid_model_draft.ipynb        # Main analysis notebook
├── Credit_card.csv                 # Feature dataset
├── Credit_card_label.csv           # Target labels
├── model.joblib                    # Trained model artifact
├── figures/                        # Visual outputs
│   ├── correlation_heatmap.png
│   ├── anova_feature_ranking.png
│   ├── roc_curve.png
│   ├── pr_curve.png
│   └── top_features.png
└── README.md                       # Documentation (this file)
```

</details>

---

<details>
<summary><strong>15. Conclusion</strong></summary>

This hybrid model demonstrates how combining interpretable domain rules with machine learning significantly enhances performance and fairness in credit risk classification.

- **Rule A** captures long-tenure applicants with high precision.  
- **Logistic Regression** complements it with probabilistic reasoning for nuanced cases.  
- Achieves balance between accuracy (0.62), recall (0.50), and transparency — essential for real-world financial screening.  

Future improvements include integrating resampling methods (e.g., SMOTE) or ensemble stacking to further strengthen recall on minority cases.

</details>

---
