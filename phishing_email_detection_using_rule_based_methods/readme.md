# Phishing Email Detection (Rule-Based Approach)

This project explores how interpretable rule-based methods can be used to detect phishing emails.  
It builds a strong baseline for email threat detection using feature statistics, threshold analysis, and simple logical rules.  
The project serves as a foundation for later machine-learning comparisons.

---

## Project Overview

| Aspect | Details |
|---------|----------|
| **Goal** | Identify structural and linguistic signals that distinguish phishing from legitimate emails. |
| **Dataset** | 13,898 emails with 9 engineered features. |
| **Approach** | Data exploration → ANOVA feature ranking → rule definition → ensemble evaluation. |
| **Focus** | High interpretability and lightweight detection logic. |

---

## Dataset and Features

Each email record includes numerical indicators of its structure and language characteristics:

- `num_words`: Total words in the email body  
- `num_unique_words`: Lexical diversity  
- `num_stopwords`: Stopword count  
- `num_links`: Number of URLs in the message  
- `num_unique_domains`: Count of distinct link domains  
- `num_email_addresses`: Addresses detected in text  
- `num_spelling_errors`: Misspelled word count  
- `num_urgent_keywords`: Urgency cues (e.g., verify, urgent, update)  
- `label`: 1 = Phishing, 0 = Legitimate  

---

## Exploratory Data Analysis (EDA)

- Confirmed dataset balance (50% phishing / 50% legitimate).  
- Reviewed feature distributions and outliers.  
- Verified feature data types for downstream statistical tests.  

The dataset showed high variance in text-based features, indicating that phishing messages often differ in length, link density, and urgency language.

---

## Feature Importance via ANOVA

Using Analysis of Variance (ANOVA) with `f_classif`, numerical features were ranked by their ability to explain variance between phishing and legitimate emails.

| Rank | Feature | p-value (significance) |
|------|----------|------------------------|
| 1 | `num_email_addresses` | 6.38 × 10⁻⁴² |
| 2 | `num_urgent_keywords` | 1.05 × 10⁻¹⁷ |
| 3 | `num_links` | 4.48 × 10⁻¹³ |
| 4 | `num_spelling_errors` | 1.36 × 10⁻⁶ |
| 5 | `num_words` | 2.15 × 10⁻² |

These variables capture both behavioral (links, email addresses) and linguistic (spelling, urgency) phishing signals.

---

## Rule-Based Detection System

Five individual rules were defined based on the top-ranked features and optimized thresholds:

| Rule | Feature | Condition | Accuracy |
|------|----------|------------|-----------|
| A | `num_email_addresses` | `< 1` | 60.8% |
| B | `num_urgent_keywords` | `≥ 1` | 52.4% |
| C | `num_links` | `< 1` | 52.3% |
| D | `num_spelling_errors` | `< 18` | 53.9% |
| E | `num_words` | `≥ 37` | 54.1% |

---

## Ensemble Decision Strategies

To improve reliability, multiple rules were combined using logical aggregation.

| Strategy | Logic | Accuracy | Key Takeaways |
|-----------|--------|-----------|----------------|
| **OR Rule** | Phishing if any rule triggers | 50% | Extremely sensitive, many false positives |
| **AND Rule** | Phishing if all rules trigger | 54% | High precision, low recall |
| **Majority (3 of 5)** | Phishing if three or more rules trigger | **62%** | Best trade-off between recall and precision |

---

## Results Summary

- Best performing configuration: Majority voting (3 of 5 rules)  
- Overall accuracy: approximately 62%  
- Precision (phishing): 0.62  
- Recall (phishing): 0.63  
- Interpretability: 100% (each rule corresponds to a transparent, human-readable heuristic)

---

## Discussion

**Advantages:**  
- Easy to interpret and deploy  
- Zero-training baseline for phishing detection  
- Identifies clear behavioral patterns such as link and urgency frequency  

**Limitations:**  
- Rule thresholds are dataset-specific  
- Moderate accuracy compared to ML classifiers  
- Limited handling of nuanced phishing language  

**Real-World Application:**  
In a real-world email security system, this rule-based model could serve as a lightweight pre-filter before machine-learning or NLP-based classification.  
It provides immediate interpretability and computational efficiency for low-latency threat screening.
 

---

## Future Work

- Integrate machine-learning models (e.g., logistic regression, random forest) for comparison  
- Expand linguistic feature set with TF-IDF and email header metadata  
- Test hybrid models that combine rule-based filters with learned features  

---

## Tech Stack

- Python 3  
- Pandas, NumPy  
- Matplotlib, Seaborn  
- Scikit-learn  

---

## Folder Structure

Phishing_Email_Detection_Rule_Based/
│
├── phishing_rule_based.ipynb # Main analysis notebook
├── phishing_emails.csv # Dataset
├── requirements.txt # Dependencies
├── /figures/ # Visual outputs
│ ├── anova_feature_importance.png
│ ├── rule_threshold_sweeps.png
│ └── confusion_matrices.png
└── README.md # Project overview (this file)
