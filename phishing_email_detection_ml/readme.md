# Phishing Email Detection (Machine Learning Approach)

This project extends the previous rule-based phishing detection system by applying and comparing multiple machine learning models.  
The objective is to build, tune, and evaluate predictive models that can automatically identify phishing emails with improved accuracy and scalability.

---

<details>
<summary><strong>1. Project Overview</strong></summary>

**Goal:**  
Develop and evaluate supervised machine learning models for phishing email classification.

**Dataset:**  
13,600 email samples with engineered linguistic and structural features.

**Approach:**  
Data exploration → Feature scaling → Model training → Hyperparameter tuning → Evaluation.

</details>

---

<details>
<summary><strong>2. Workflow Summary</strong></summary>

**Steps:**
1. **Exploratory Data Analysis (EDA):**  
   - Examined feature distributions and correlations.  
   - Confirmed balanced dataset (phishing and legitimate emails).  

2. **Baseline Model (Logistic Regression):**  
   - Accuracy: 0.53  
   - Served as a simple linear benchmark.

3. **Hyperparameter Tuning:**  
   - Used `RandomizedSearchCV` with 5-fold cross-validation.  
   - Optimized model parameters for performance and runtime.

4. **Algorithms Evaluated:**

| Model | Accuracy | Notes |
|--------|-----------|-------|
| Logistic Regression (Baseline) | 0.53 | Fast, weak recall |
| Logistic Regression (Tuned) | 0.59 | Improved with regularization tuning |
| K-Nearest Neighbors (Tuned) | 0.60 | Moderate accuracy, higher runtime |
| Decision Tree (Tuned) | 0.73 | Strong, interpretable rules |
| Random Forest (Tuned) | **0.78** | Best performer overall |
| XGBoost (Tuned) | 0.75 | Nearly as strong, faster to train |

</details>

---

<details>
<summary><strong>3. Model Deployment</strong></summary>

**Deployed Model:** XGBoost (tuned)  
**Accuracy:** 0.75  
**Prediction latency:** approximately 0.004 seconds per email  

The model was exported using `joblib` for reusability and integrated into a simple inference function for real-time prediction testing.

</details>

---

<details>
<summary><strong>4. Key Insights</strong></summary>

- The rule-based 3-of-5 model achieved higher recall (0.93) but lower accuracy.  
- Machine learning models achieved higher overall accuracy and generalization.  
- Decision Tree, Random Forest, and XGBoost captured non-linear interactions effectively.  
- Logistic models offered interpretability but lacked performance on complex feature interactions.

</details>

---

<details>
<summary><strong>5. Real-World Application</strong></summary>

In an enterprise email security pipeline, these models could be layered as follows:

- **Rule-Based Filter:** Fast, interpretable pre-filter to block high-confidence phishing emails.  
- **ML Classifier (Random Forest or XGBoost):** Secondary screening for more nuanced detections.  

This hybrid structure combines interpretability, precision, and computational efficiency for low-latency phishing detection.

</details>

---

<details>
<summary><strong>6. Tech Stack</strong></summary>

- Python 3.10  
- pandas, numpy  
- scikit-learn, scipy  
- xgboost, joblib  
- matplotlib, seaborn

</details>

---

<details>
<summary><strong>7. Results Summary</strong></summary>

| Metric | Best Model (Random Forest) |
|---------|-----------------------------|
| Accuracy | 0.78 |
| Precision | 0.79 |
| Recall | 0.77 |
| F1-Score | 0.78 |

**Observations:**  
- Random Forest achieved the best balance of precision and recall.  
- XGBoost provided comparable performance with reduced training time.  
- Logistic Regression served as a strong interpretability benchmark.

</details>

---

<details>
<summary><strong>8. Folder Structure</strong></summary>

Phishing_Email_Detection_ML/
│
├── phishing_ml_classification.ipynb # Main analysis notebook
├── phishing_emails.csv # Dataset
├── model_rf_xgb.joblib # Saved ML models
├── /figures/ # Visual outputs
│ ├── feature_importance.png
│ ├── model_comparison.png
│ └── confusion_matrix.png
└── README.md # Project overview (this file)

yaml
Copy code

</details>

---

<details>
<summary><strong>9. Conclusion</strong></summary>

This project demonstrates a complete machine learning workflow for phishing detection, from EDA to model tuning and evaluation.  
It highlights how machine learning improves over rule-based systems in accuracy and adaptability, while rule-based models remain valuable for interpretability and recall.  
Together, they form a hybrid detection system suitable for production-grade email filtering.

</details>

---
