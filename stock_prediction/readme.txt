Stock Price Prediction with LSTM Neural Network
This project demonstrates how to build a Long Short-Term Memory (LSTM) neural network to predict future stock prices using historical data from Yahoo Finance.
We use Pinduoduo Inc. (PDD) as a case study due to its high volatility and relevance during my time working in China.

Key Technologies
Python – Data manipulation and modeling

yFinance – Historical stock data retrieval

Pandas & NumPy – Data preprocessing and array handling

Matplotlib – Visualization of trends and predictions

scikit-learn – Feature scaling using MinMaxScaler

TensorFlow / Keras – LSTM-based deep learning model

Project Workflow
Data Retrieval
Fetch historical closing prices for PDD from Yahoo Finance (2012–2025).

Preprocessing
Normalize prices to a [0,1] scale using MinMaxScaler to improve model performance and convergence.

Sequence Generation
Create training sequences using a sliding 60-day window to predict the next day's closing price.

Model Architecture

Three LSTM layers with 50 units each

Dropout layers after each LSTM to reduce overfitting

Dense output layer to predict a single value

Training
Train the model for 250 epochs using the Adam optimizer and mean squared error (MSE) as the loss function.

Evaluation
Compare the model’s predictions to actual stock prices using visual plots.

Forecasting
Predict the next day’s closing price based on the most recent 60 days of data.

Outputs
Trained LSTM model capable of forecasting stock trends

Visualization comparing actual vs. predicted stock prices

Printout of predicted next-day closing price

Notes
LSTM is well-suited for financial time-series data due to its ability to capture sequential dependencies.

A 60-day lookback window balances short-term signal capture with stability.

This project highlights explainable modeling steps suitable for demonstration, prototyping, or interview preparation.
