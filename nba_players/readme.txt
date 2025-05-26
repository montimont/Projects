# NBA Player Performance Analysis & Forecasting

This project explores NBA player statistics using a combination of data analysis, machine learning, and deep learning techniques. It aims to identify trends, evaluate player performance, forecast future performance, and classify players based on various metrics.

## Data Source
Dataset: [NBA Player Data from Kaggle](https://www.kaggle.com/datasets/justinas/nba-players-data)  
It contains season-by-season performance data for NBA players.

## Technologies Used
- Python (pandas, NumPy, matplotlib, seaborn)
- Scikit-learn (regression, clustering, classification)
- Statsmodels (ARIMA modeling)
- TensorFlow/Keras (LSTM and deep learning regression)
- KaggleHub (data loading)

## Key Components
- **Data Cleaning & Exploration**: Handling missing values, encoding categorical features, and computing summary statistics.
- **Visualization**: Histograms, box plots, correlation heatmaps, and PCA scatter plots for cluster analysis.
- **Regression**: Linear regression and neural networks to predict player points per game.
- **Classification**: Random forest model classifies colleges into high/low impact based on player performance.
- **Clustering**: K-means used to group players with similar metrics.
- **Time Series Forecasting**: Both ARIMA and LSTM used to forecast future scoring for selected players.

##  Sample Output
- Predicted next-season points for Ja Morant using ARIMA and LSTM.
- Regression loss from a deep learning model predicting player points.
- Cluster breakdown of player roles based on performance metrics.

## Why This Project Matters
This project showcases end-to-end data science skills with real sports data:
- Structured EDA
- Predictive modeling
- Model interpretability and business context
- Deep learning application to time series forecasting

## Potential Improvements
- Add player comparison dashboards
- Integrate shot location or play-by-play data
- Deploy as an interactive web app with Streamlit
