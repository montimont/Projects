# Stock Price Prediction with LSTM Neural Network

This project demonstrates how to build a Long Short-Term Memory (LSTM) neural network to predict future stock prices using historical data from Yahoo Finance. 
Specifically, we use Pinduoduo Inc. (PDD) as a case study due to its high volatility and relevance during my time in China.

## Key Technologies

- **Python** (Data manipulation and modeling)
- **yFinance** (Historical stock data retrieval)
- **Pandas & NumPy** (Data processing)
- **Matplotlib** (Data visualization)
- **scikit-learn** (Feature scaling)
- **TensorFlow / Keras** (Deep learning LSTM model)

## Project Workflow

1. **Data Retrieval:** Fetch historical closing prices from Yahoo Finance (2012–2025).
2. **Preprocessing:** Normalize data using MinMaxScaler for LSTM efficiency.
3. **Sequence Generation:** Use a sliding window of 60 days to predict the next day’s price.
4. **Model Architecture:**
   - Three LSTM layers with dropout for regularization.
   - Final dense layer to output the predicted price.
5. **Training:** 250 epochs using MSE loss and Adam optimizer.
6. **Evaluation:** Compare actual vs predicted stock prices visually.
7. **Forecasting:** Predict the next day’s closing price.

## Outputs

- Trained LSTM model
- Line plot comparing actual vs. predicted stock prices
- Next-day closing price forecast

## Notes

- LSTM was chosen due to its strength in modeling time-series dependencies.
- 60-day window was selected for balance between short-term trends and noise reduction.
- MinMaxScaler was used to improve training convergence.

