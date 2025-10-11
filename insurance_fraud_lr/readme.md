# Insurance Fraud Detection (Logistic Regression)

This project applies logistic regression to identify fraudulent insurance claims using interpretable, auditable machine learning.  
It demonstrates the full workflow from data cleaning and feature reduction to model tuning, threshold calibration, and deployment preparation.

---

<details>
<summary><strong>1. Project Overview</strong></summary>

**Objective:**  
Detect fraudulent insurance claims from structured policyholder and incident data using a transparent, linear model.

**Dataset:**  
1,000 claim records with 28 attributes covering demographics, policy details, and incident characteristics.

**Goal:**  
Build an interpretable fraud detection model that achieves balanced precision and recall while providing coefficient-based insights.

</details>

---

<details>
<summary><strong>2. Data Exploration and Cleaning</strong></summary>

- Verified data completeness and consistency (no missing values except `authorities_contacted`, imputed as “None”).  
- Removed duplicates and standardized categorical types.  
- Converted 16 categorical variables into numeric form using `LabelEncoder`.  
- Balanced dataset using `RandomUnderSampler` to address 75:25 genuine-to-fraud ratio.  

**Dataset Summary:**  
- Total records: 1,000  
- Final columns after encoding: 28  
- Target variable: `fraud_reported` (0 = Genuine, 1 = Fraud)

</details>

---

<details>
<summary><strong>3. Exploratory Data Analysis (EDA)</strong></summary>

**Key Observations:**
- Fraud frequency: 24.7% of records.  
- Fraudulent claims often involved **low-severity incidents**, **property damage reports**, and **police involvement**.  
- Features such as `incident_severity`, `property_damage`, `collision_type`, and `authorities_contacted` showed distinct distributions.

**Insights:**
- Low correlation between most features (|r| < 0.1), ideal for logistic regression.  
- Strong correlations:
  - `months_as_customer` ↔ `age` (~0.92)  
  - `incident_severity` ↔ `collision_type` (~–0.44)

</details>

---

<details>
<summary><strong>4. Feature Selection</strong></summary>

**Methods Applied:**
- Correlation analysis (removed highly correlated features).  
- Variance Inflation Factor (VIF) check for multicollinearity.  
- Hierarchical clustering and dendrogram grouping to confirm redundancy.

**Removed Features:**
- `age` — redundant with `months_as_customer`.  
- `number_of_vehicles_involved` — overlaps with `incident_type`.  
- `incident_date`, `auto_make`, `auto_year` — low predictive power.  
- `capital-gains`, `capital-loss` — near-zero correlation with fraud.

**Final Feature Count:** 21 independent predictors.

</details>

---

<details>
<summary><strong>5. Model Training and Evaluation</strong></summary>

**Model:** Logistic Regression (L2 regularization)

**Baseline Performance:**
| Metric | Score |
|---------|--------|
| Accuracy | 0.79 |
| Precision (Fraud) | 0.55 |
| Recall (Fraud) | 0.25 |
| F1 Score (Fraud) | 0.34 |
| ROC-AUC | 0.83 |

**Interpretation:**  
Good separability but modest recall — expected for a linear model on moderately overlapping classes.

</details>

---

<details>
<summary><strong>6. Hyperparameter Tuning</strong></summary>

- Used `RandomizedSearchCV` with 5-fold stratified cross-validation.  
- Tuned over regularization parameter `C` and `max_iter`.  
- Enabled `class_weight='balanced'` to address fraud underrepresentation.  

**Best Parameters:**  
`C = 0.216`, `max_iter = 1269`, `solver = lbfgs`

**Tuned Model Performance:**
| Metric | Score |
|---------|--------|
| Accuracy | 0.76 |
| Precision (Fraud) | 0.47 |
| Recall (Fraud) | 0.80 |
| F1 Score (Fraud) | 0.59 |
| ROC-AUC | 0.83 |

**Result:**  
The recall increased significantly from 0.25 to 0.80, achieving strong fraud detection with acceptable precision tradeoff.

</details>

---

<details>
<summary><strong>7. Threshold Optimization</strong></summary>

- Analyzed precision–recall trade-offs across probability cutoffs.  
- Selected **threshold = 0.40** for optimal balance.

**Final Metrics at Threshold 0.40:**
| Metric | Score |
|---------|--------|
| Accuracy | 0.85 |
| Precision | 0.64 |
| Recall | 0.73 |
| F1 Score | 0.68 |

**Confusion Matrix:**
[[138 18]
[ 12 32]]

yaml
Copy code

**Business Interpretation:**  
Captures 73% of frauds while maintaining 64% precision — a practical operating point prioritizing fraud detection with manageable false positives.

</details>

---

<details>
<summary><strong>8. Feature Importance and Explainability</strong></summary>

**Top Predictive Features:**
1. `incident_severity`  
2. `collision_type`  
3. `property_damage`  
4. `authorities_contacted`  
5. `incident_type`  
6. `umbrella_limit`  
7. `policy_deductable`  
8. `insured_occupation`  
9. `witnesses`  
10. `months_as_customer`

Visualizations include:
- **Correlation heatmap** — verifies low multicollinearity.  
- **Coefficient bar plot** — highlights strongest positive and negative contributors.  
- **Top 10 Influential Features** — demonstrates interpretable model behavior.

</details>

---

<details>
<summary><strong>9. Model Deployment</strong></summary>

- Exported trained model, scaler, and optimal threshold as `model.joblib`.  
- Created reusable inference functions:
  - `pre_process()` — prepares raw input features.  
  - `make_prediction()` — computes fraud probability and label.  
  - `post_process()` — converts numeric outputs to readable classes.  
- End-to-end testing confirmed consistent predictions on new claim inputs.

</details>

---

<details>
<summary><strong>10. Real-World Application</strong></summary>

In an enterprise insurance system, this model could:
- Serve as a **fraud pre-screening layer** before human review.  
- Generate **fraud probability scores** to prioritize investigations.  
- Operate under regulatory constraints thanks to full interpretability.  

By adjusting the probability threshold, organizations can tune the model toward higher recall (risk tolerance) or precision (review efficiency).

</details>

---

<details>
<summary><strong>11. Tech Stack</strong></summary>

- Python 3.10  
- pandas, numpy  
- scikit-learn, statsmodels, imbalanced-learn  
- seaborn, matplotlib  
- joblib  

</details>

---

<details>
<summary><strong>12. Folder Structure</strong></summary>

Insurance_Fraud_Detection/  
│  
├── Log_Reg_Fraud.ipynb              # Main analysis notebook  
├── insurance_fraud_cleaned.csv      # Dataset  
├── model.joblib                     # Saved model and scaler  
├── figures/                         # Visual outputs  
│   ├── correlation_heatmap.png  
│   ├── top_features.png  
│   ├── roc_curve.png  
│   └── confusion_matrix.png  
└── README.md                        # Project documentation (this file)

</details>

---

<details>
<summary><strong>13. Conclusion</strong></summary>

This project demonstrates a fully interpretable fraud detection pipeline using logistic regression.  
It balances predictive power and transparency, achieving an AUC of 0.83 with strong recall at a tuned threshold.  
The methodology provides a foundation for integrating more advanced ensemble or deep learning models while retaining explainability for regulated environments.

</details>

---
