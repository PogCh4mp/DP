
Forecasting Bitcoin Closing Prices with Classical and Modern Time-Series Methods

Research Question:
How accurately can we  predict Bitcoin’s daily closing price one month  ahead using various models , and how do they compare to the actual forecast?

Motivation:
Bitcoin’s pronounced volatility and rapid regime shifts make it an ideal test case for evaluating forecasting techniques. By combining both classical statistical approaches and a modern, user-friendly framework (Prophet), this project aims to:

Data Sources:
Binance (via ccxt) Daily OHLCV (“Open/High/Low/Close/Volume”) for BTC/USDT.


Scope: April 20, 2024–April 20, 2025 for model training; April 21–May 20, 2025 for out-of-sample testing.



Methodology Overview


Exploratory Data Analysis (EDA):

Plot the one‐year price series and volume.
Compute summary statistics (mean, volatility) and check for missing/irregular timestamps.
Test for stationarity using the Augmented Dickey–Fuller (ADF) test.


Baseline Forecasting:


Implement naïve “last‐value” forecast: the previous day’s closing price as the forecast for each of the next 30 days.
Compute RMSE and MAPE on the test period.


ARIMA Modeling:


Difference the series once (d = 1) to achieve stationarity.
Examine ACF/PACF plots to propose initial p/q orders; fit an ARIMA(5,1,0).
Perform a manual grid search over p,q ∈ {0…5} to minimize AIC; refit the optimal model.
Forecast 30 days ahead.


Prophet Modeling:


Reformat data into Prophet’s required “ds” (date) and “y” (value) columns.
Fit with default changepoint settings and daily seasonality enabled.
Generate a 30-day forecast.
Holt–Winters Exponential Smoothing
Specify additive trend and seasonality components.
Fit on the full training series; forecast the next 30 days.


Theta Method:

Decompose the series into two Theta lines (θ = 0 and θ = 2) and recombine.
Produce a 30-day forecast.
Ensemble Forecast
Average the daily predictions from ARIMA, Prophet, Holt–Winters, and Theta.
Evaluate ensemble accuracy against each individual model.


Model Evaluation & Visualization:


Calculate RMSE, MAE, and MAPE for all forecasts (baseline, four models, ensemble).
Plot actual vs. forecasted closing prices for each method.
Chart error metrics over the 30-day horizon to observe error growth.


