# Phishing Email Detection (Machine Learning Approach)

This project develops and evaluates supervised machine learning models for detecting phishing emails.  
It builds on insights from earlier rule-based approaches by applying scalable algorithms capable of learning complex, non-linear patterns.  
The goal is to enhance accuracy and adaptability in real-world email security systems.

---

<details>
<summary><strong>1. Project Overview</strong></summary>

**Objective:**  
Create predictive models that classify phishing and legitimate emails using engineered linguistic and structural features.  

**Dataset:**  
13,600 labeled email samples containing attributes such as word counts, link density, and urgency indicators.  

**Methodology:**  
Data exploration → Feature scaling → Model training → Hyperparameter tuning → Performance evaluation.  

**Focus:**  
Improving model accuracy and operational readiness for integration into enterprise email filtering systems.

</details>

---

<details>
<summary><strong>2. Workflow Summary</strong></summary>

**Steps:**
1. **Exploratory Data Analysis (EDA):**  
   - Reviewed feature distributions and relationships.  
   - Verified class balance between phishing and legitimate samples.  
   - Identified high link density and urgency language as strong phishing signals.

2. **Baseline Model (Logistic Regression):**  
   - Accuracy: 0.53  
   - Provided a simple interpretability benchmark.

3. **Hyperparameter Tuning:**  
   - Applied `RandomizedSearchCV` with 5-fold cross-validation.  
   - Tuned parameters for accuracy, recall, and runtime efficiency.

4. **Algorithms Evaluated:**

| Model | Accuracy | Notes |
|--------|-----------|-------|
| Logistic Regression (Baseline) | 0.53 | Linear reference model |
| Logistic Regression (Tuned) | 0.59 | Improved regularization and convergence |
| K-Nearest Neighbors (Tuned) | 0.60 | Moderate accuracy, slower inference |
| Decision Tree (Tuned) | 0.73 | Clear rule interpretation |
| Random Forest (Tuned) | **0.78** | Highest overall performance |
| XGBoost (Tuned) | 0.75 | Similar accuracy, faster training |

</details>

---

<details>
<summary><strong>3. Model Deployment</strong></summary>

**Final Model:** XGBoost (tuned)  
**Accuracy:** 0.75  
**Prediction latency:** approximately 0.004 seconds per email  

The trained model was exported using `joblib` for reuse and integrated into a lightweight Python inference function.  
This setup supports real-time scanning and batch classification, making it adaptable for operational email systems.

</details>

---

<details>
<summary><strong>4. Key Insights</strong></summary>

- Linear models captured general trends but underperformed on complex patterns.  
- Tree-based methods (Decision Tree, Random Forest, XGBoost) significantly improved classification accuracy.  
- Ensemble models were more resilient to noise and feature variance.  
- Precision and recall trade-offs can be adjusted based on deployment priorities (user protection vs. false positives).  

</details>

---

<details>
<summary><strong>5. Real-World Context</strong></summary>

Phishing remains one of the most prevalent cybersecurity threats, responsible for a large share of data breaches and credential theft incidents.  
In enterprise environments, detection systems must analyze thousands of emails per second, balancing accuracy with processing speed.

This project models how a **production-grade phishing detection pipeline** could function in practice:

- **Initial Filtering:** A lightweight set of structural checks (e.g., link count, domain mismatch, urgency keywords) quickly screens out high-risk messages.  
- **Machine Learning Classifier:** Models like Random Forest or XGBoost process uncertain cases, leveraging learned relationships across multiple engineered features.  

By layering these components, organizations can achieve:
- Real-time classification with low latency  
- High accuracy for complex phishing attempts  
- Continuous retraining based on new email samples  

Such a system could integrate with corporate email gateways, security orchestration tools, or incident response dashboards, providing a flexible and adaptive defense against evolving phishing techniques.

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
- Random Forest achieved the best precision-recall balance.  
- XGBoost provided near-equal accuracy with faster model training.  
- Logistic Regression served as a transparent baseline for comparison.  

</details>

---

<details>
<summary><strong>8. Folder Structure</strong></summary>

Phishing_Email_Detection_ML/  
│  
├── phishing_ml_classification.ipynb  # Main analysis notebook  
├── phishing_emails.csv               # Dataset  
├── model_rf_xgb.joblib               # Saved ML models  
└── README.md                         # Project overview (this file)

</details>

---

<details>
<summary><strong>9. Conclusion</strong></summary>

This project demonstrates a complete end-to-end machine learning workflow for phishing detection, from EDA and model training to evaluation and deployment preparation.  
It illustrates how predictive modeling can scale traditional rule-based methods into data-driven, adaptable email defense systems.  

By combining structured feature engineering with ensemble learning, the resulting models achieve strong accuracy and practical deployment readiness — suitable for integration into corporate email filters, security applications, or early-warning systems.

</details>

---
