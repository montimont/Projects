# Drug Decision Tree Classifier

This project showcases a basic decision tree classifier built on a healthcare dataset to predict drug prescriptions based on patient features. It demonstrates model tuning, pruning, and explainability using Python's scikit-learn library.

## Context

With a background in medical data analysis—particularly in oncology and the treatment of Acute Promyelocytic Leukemia (APL)—this project reflects how clinical decision logic can be modeled using machine learning.

Although the dataset is sourced from Kaggle and not proprietary clinical data, it serves as a proxy for showcasing techniques commonly applied in healthcare analytics.

## Technologies Used

- Python
- scikit-learn (Decision Trees, GridSearchCV, RandomizedSearchCV)
- matplotlib (for confusion matrix and tree visualizations)
- pandas and numpy (data handling)

## What This Project Covers

- Data preprocessing and cleaning
- Decision tree model with controlled `max_depth`
- Evaluation using classification report and confusion matrix
- Hyperparameter tuning with Grid Search, Random Search, and K-Fold CV
- Tree pruning with cost complexity pruning path
- Performance tuning with simplified models

## Key Takeaways

- Demonstrates how to use interpretable models for healthcare decision support
- Highlights trade-offs between model complexity and performance
- Emphasizes good modeling practices even with small datasets

## Future Enhancements

- Extend to real-world healthcare or prescription data
- Deploy as a web app or API for real-time decision support
- Integrate SHAP/LIME for local model explainability
- Test with ensemble classifiers (e.g., Random Forest, XGBoost)

This project represents both technical competency and practical alignment with real-world use cases in healthcare analytics.
