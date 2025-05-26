# Credit Default Prediction Case Study

This project presents a structured approach to predicting credit defaults using a real-world-style case study. Designed as a demonstration of end-to-end risk modeling, it includes exploratory data analysis, handling imbalanced classes, mixed data types, and deploying a neural network using Keras. This case study was a key component of my successful transition from medicine into finance and data science.

## Objective

To build a predictive model that accurately estimates the likelihood of credit default, enabling lenders to optimize their loan portfolios and minimize risk exposure.

## Key Concepts Covered

- Credit risk modeling
- Handling class imbalance (SMOTE)
- Data preprocessing for mixed data types
- Feature selection via logistic models
- Predictive modeling using Keras
- Model evaluation using ROC curves and cross-validation
- Production strategy planning

## Tools & Libraries

- Python
- Pandas, NumPy, Matplotlib
- Scikit-learn
- Imbalanced-learn (SMOTE)
- Keras (TensorFlow backend)

## Modeling Workflow

1. **Exploratory Data Analysis**
   - Addressed class imbalance (70/30) with SMOTE.
   - Identified categorical, binary, and numerical variables.

2. **Feature Engineering**
   - Logistic regression per variable type to select significant predictors.
   - Merged engineered features for training.

3. **Modeling Strategy**
   - Compared Linear Regression, Random Forest, and Keras.
   - Chose Keras for its ability to handle complex, nonlinear patterns.

4. **Evaluation**
   - K-Fold Cross Validation.
   - ROC/AUC analysis to assess model performance.

5. **Production Readiness**
   - Considered REST API deployment.
   - Highlighted update and monitoring plans.

## Supporting Documentation

See accompanying PDF `MB_Case_Study.pdf` for a narrated visual explanation of the process, rationale, and findings.

## Future Considerations

- Expand training dataset
- Address multicollinearity
- Advanced hyperparameter tuning
- Real-time API integration
