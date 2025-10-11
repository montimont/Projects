# Phishing Email Detection (Machine Learning Approach)

This project extends the previous rule-based phishing detection system by applying and comparing multiple machine learning models.  
The objective is to build, tune, and evaluate predictive models that can automatically identify phishing emails with improved accuracy and scalability.  
It demonstrates how data-driven automation can complement interpretable rule-based detection to support enterprise-level email security systems.

---

<details>
<summary><strong>1. Project Overview</strong></summary>

**Goal:**  
Develop and evaluate supervised machine learning models for phishing email classification that can operate efficiently in real-time systems.

**Dataset:**  
13,600 email samples with engineered linguistic and structural features derived from message text and metadata.

**Approach:**  
Data exploration → Feature scaling → Model training → Hyperparameter tuning → Evaluation → Real-world interpretation.

</details>

---

<details>
<summary><strong>2. Workflow Summary</strong></summary>

**Steps:**
1. **Exploratory Data Analysis (EDA):**  
   - Examined feature distributions and correlations.  
   - Verified balanced dataset (equal phishing and legitimate emails).  
   - Identified structural patterns such as higher link density and urgency keywords in phishing messages.

2. **Baseline Model (Logistic Regression):**  
   - Accuracy: 0.53  
   - Served as a simple linear benchmark for interpretability and feature sensitivity.

3. **Hyperparameter Tuning:**  
   - Used `RandomizedSearchCV` with 5-fold cross-validation.  
   - Optimized model parameters for generalization and efficient inference.

4. **Algorithms Evaluated:**

| Model | Accuracy | Notes |
|--------|-----------|-------|
| Logistic Regression (Baseline) | 0.53 | Fast, low recall |
| Logistic Regression (Tuned) | 0.59 | Improved with optimized regularization |
| K-Nearest Neighbors (Tuned) | 0.60 | Moderate accuracy, slower prediction speed |
| Decision Tree (Tuned) | 0.73 | Interpretable decision logic |
| Random Forest (Tuned) | **0.78** | Best overall performance and robustness |
| XGBoost (Tuned) | 0.75 | Competitive performance with fast training time |

</details>

---

<details>
<summary><strong>3. Model Deployment</strong></summary>

**Deployed Model:** XGBoost (tuned)  
**Accuracy:** 0.75  
**Prediction latency:** approximately 0.004 seconds per email  

The model was exported using `joblib` for reusability and integrated into a simple Python inference function to simulate real-time email scanning.  
This design allows the model to process streaming input and classify new messages dynamically with low computational overhead.

</details>

---

<details>
<summary><strong>4. Key Insights</strong></summary>

- The rule-based 3-of-5 model achieved higher recall (0.93) but lower precision.  
- Machine learning models improved overall accuracy and stability.  
- Tree-based methods (Decision Tree, Random Forest, XGBoost) handled non-linear feature relationships effectively.  
- Logistic models offered explainability but struggled with complex interactions.  
- Combining rule-based and ML models yields balanced detection with interpretable decision logic and robust generalization.

</details>

---

<details>
<summary><strong>5. Real-World Context</strong></summary>

Phishing attacks remain one of the most significant entry points for security breaches in organizations.  
Email security systems must process thousands of messages per minute, requiring **low-latency and high-accuracy detection pipelines**.

This project models how a **two-stage phishing detection architecture** can function in production:

- **Stage 1: Rule-Based Filter**  
  A lightweight, interpretable system that flags emails based on structural anomalies (e.g., link count, urgent phrases, multiple sender domains).  
  This stage ensures immediate rejection of high-confidence phishing attempts with minimal computation.

- **Stage 2: Machine Learning Classifier**  
  Advanced classifiers such as Random Forest or XGBoost re-evaluate uncertain cases, leveraging statistical patterns across multiple features.  
  This layer provides adaptive learning and captures subtle phishing behaviors unseen in static rule sets.

In enterprise environments, such a system can be integrated with:
- **Email gateways** (e.g., Microsoft Exchange, Gmail APIs) for automated message scoring.  
- **Incident response dashboards** for monitoring false positives and retraining.  
- **Threat intelligence pipelines** that continuously update models based on new phishing samples.

By combining interpretability, accuracy, and computational efficiency, this framework aligns with the operational constraints of real-time cybersecurity systems.

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
- Random Forest achieved the best trade-off between precision and recall.  
- XGBoost provided similar performance with faster training time.  
- Logistic Regression remained valuable for baseline interpretability.  
- Ensemble methods demonstrated the scalability required for real-world deployment.

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

This project demonstrates a complete machine learning workflow for phishing detection, from EDA to model tuning and evaluation.  
It highlights how machine learning enhances accuracy and adaptability over rule-based systems while preserving interpretability.  

When integrated into a real-world email filtering pipeline, this approach enables organizations to detect phishing attempts faster and more reliably, reducing user exposure to malicious links and credential theft.  
Together, the rule-based and ML-based systems form a **hybrid, production-ready detection framework** capable of continuous learning and rapid response.

</details>

---
