# Drug Type Prediction (Decision Tree Model)

This project applies supervised machine learning to predict the most effective drug for a patient based on demographic and medical attributes.  
Using a decision tree classifier, the model learns from patterns in clinical data to support data-driven drug assignment and healthcare recommendations.

---

<details>
<summary><strong>1. Project Overview</strong></summary>

**Objective:**  
Predict the appropriate drug type for a patient using key physiological and biochemical indicators.

**Dataset:**  
200 patient records containing the following features:
- Age  
- Sex  
- Blood Pressure (BP)  
- Cholesterol  
- Sodium-to-Potassium Ratio (Na_to_K)  
- Drug (target variable)

**Goal:**  
Develop an interpretable decision tree model capable of identifying drug classes efficiently and accurately.

</details>

---

<details>
<summary><strong>2. Data Exploration</strong></summary>

**Initial Findings:**
- No missing values; dataset is clean and structured.  
- Class imbalance observed across five drug categories.  
- Strong influence from sodium-to-potassium ratio and blood pressure levels.

**Visualization Steps:**
- Count plots and histograms for feature distribution by drug class.  
- Correlation heatmaps and bar plots to identify significant predictors.  
- Categorical variables encoded numerically using `LabelEncoder`.

</details>

---

<details>
<summary><strong>3. Feature Engineering</strong></summary>

New engineered features were added to improve model learning:

- **Na_to_K_bin:** Binned continuous values into Low, Medium, High, Very High.  
- **Age_Group:** Categorized patients as Young, Adult, Senior, Elderly.  
- **BP_Cholesterol:** Interaction term to capture the combined effect.  
- **NaK_BP:** Product of sodium–potassium ratio and blood pressure encoding.

These features enhanced pattern recognition and provided meaningful interpretability for medical decision logic.

</details>

---

<details>
<summary><strong>4. Model Training and Optimization</strong></summary>

**Base Model:**  
Decision Tree Classifier trained using stratified 80/20 split.

**Hyperparameter Tuning:**  
- Used `RandomizedSearchCV` with `StratifiedKFold` cross-validation.  
- Search space included `max_depth`, `min_samples_split`, `criterion`, and `class_weight`.  
- Optimal parameters achieved perfect cross-validation accuracy (1.00).

**Training Results:**  
- **Macro ROC-AUC:** 0.927  
- **Weighted ROC-AUC:** 0.968  
- **Macro F1-score:** 0.893  
- **Weighted F1-score:** 0.947  
- **Test Accuracy:** 0.95  

</details>

---

<details>
<summary><strong>5. Random Forest Extension</strong></summary>

A Random Forest model was trained for performance comparison.

**Best Parameters:**  
`class_weight='balanced'`, `criterion='gini'`, `max_depth=8`, `n_estimators≈150`.

**Performance:**  
- **Accuracy:** 0.97  
- **Macro F1-score:** 0.942  
- **Weighted F1-score:** 0.974  
- **ROC-AUC:** 1.00 (macro and weighted)  

**Feature Importance (Top Predictors):**
1. Na_to_K  
2. NaK_BP  
3. BP  
4. Age  
5. Age_Group

</details>

---

<details>
<summary><strong>6. Model Explainability</strong></summary>

**Decision Tree Visualization:**  
- Illustrated full tree structure with color-coded branches for each drug class.  
- Showed hierarchical decision flow from biochemical features to predicted outcomes.

**Feature Importance Plot:**  
Highlighted the dominant influence of sodium–potassium ratio and blood pressure on drug classification.

**VIF Analysis:**  
Variance Inflation Factors confirmed low multicollinearity among features, supporting the reliability of model coefficients.

</details>

---

<details>
<summary><strong>7. Real-World Context</strong></summary>

This model simulates a medical decision support tool for early-stage prescription recommendation.  
In practice, such systems can assist healthcare providers by:

- Offering **data-driven guidance** on potential treatment plans.  
- Identifying **key predictors** of drug suitability (e.g., sodium–potassium balance, patient age).  
- Supporting **pharmacological screening** before more complex analysis or doctor review.

When deployed, it could serve as a **clinical pre-screening layer** that quickly suggests probable drug categories before physician validation — improving efficiency without replacing medical judgment.

</details>

---

<details>
<summary><strong>8. Tech Stack</strong></summary>

- Python 3.10  
- pandas, numpy  
- scikit-learn, imbalanced-learn  
- seaborn, matplotlib  
- statsmodels, shap  

</details>

---

<details>
<summary><strong>9. Results Summary</strong></summary>

| Model | Accuracy | Macro F1 | Weighted F1 | ROC-AUC |
|--------|-----------|-----------|--------------|----------|
| Decision Tree | 0.95 | 0.89 | 0.95 | 0.93 |
| Random Forest | **0.97** | **0.94** | **0.97** | **1.00** |

**Key Observations:**  
- Ensemble learning improved performance and stability.  
- Sodium–potassium ratio emerged as the most predictive biomarker.  
- Both models achieved strong interpretability and low bias–variance trade-off.

</details>

---

<details>
<summary><strong>10. Folder Structure</strong></summary>

Drug_Type_Prediction/  
│  
├── drug_check_decision_tree.ipynb   # Main analysis notebook  
├── drug200.csv                      # Dataset  
└── README.md                        # Project overview (this file)

</details>

---

<details>
<summary><strong>11. Conclusion</strong></summary>

This project demonstrates how machine learning can be applied to personalized medicine through interpretable models.  
By leveraging decision trees and ensemble techniques, the system achieves high accuracy while maintaining transparency in decision-making.  

It represents a practical step toward **AI-assisted prescription systems**, combining performance with explainability for responsible deployment in healthcare settings.

</details>

---
