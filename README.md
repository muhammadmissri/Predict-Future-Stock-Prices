Predict Future Stock Prices (Short-Term)
![Python](https://img.shields.io/badge/Python-3.9+-blue) ![yfinance](https://img.shields.io/badge/yfinance-API-yellow) ![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-green) ![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
---
Projet Objective
Use historical stock market data to predict the next day's closing price of a stock using regression models. This Project covers real-world time series data handling, feature engineering, model training, and performance evaluation — all essential skills for financial data science.
---
Dataset Used
Property	Details
Stock Ticker	AAPL (Apple Inc.)
Source	Yahoo Finance via `yfinance` Python library
Period	Last 3 years of historical data
Frequency	Daily OHLCV (Open, High, Low, Close, Volume)
Approx. Rows	~756 trading days
Features Used for Prediction
Feature	Description
`Open`	Opening price of the day
`High`	Highest price of the day
`Low`	Lowest price of the day
`Volume`	Number of shares traded
`Price\\\_Range`	High minus Low (engineered)
`Close\\\_OpenDiff`	Close minus Open (engineered)
`MA\\\_5`	5-day moving average (engineered)
`MA\\\_20`	20-day moving average (engineered)
`Volatility`	5-day rolling standard deviation (engineered)
Target Variable: Next day's `Close` price (shifted by -1)
---
Models Applied
Model	Library	Type
Linear Regression	`sklearn.linear\\\_model`	Baseline regression
Random Forest Regressor	`sklearn.ensemble`	Ensemble regression
Training Strategy
Split: Chronological 80/20 (no shuffling — to respect time order)
Scaling: StandardScaler applied to all features
Train size: ~605 samples
Test size: ~151 samples
---
Key Results and Findings
Model Performance Comparison
Metric	Linear Regression	Random Forest
MAE	Higher	Lower ✅
RMSE	Higher	Lower ✅
R² Score	Good	Better ✅
Feature Importance (Random Forest)
MA_5 and MA_20 — Moving averages are the most powerful predictors, confirming momentum-based price behavior.
Close_OpenDiff — Intraday price movement is a strong short-term signal.
Volume — Lower importance, but contributes to breakout detection.
Key Findings
Random Forest significantly outperforms Linear Regression due to its ability to capture non-linear patterns.
The actual vs predicted plot shows predictions closely tracking real prices.
Moving averages confirm that short-term momentum is the dominant price driver.
For production use, adding sentiment analysis or technical indicators (RSI, MACD) would improve accuracy further.
---
How to Run
```bash
# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn yfinance

# Open the notebook
jupyter notebook \\\_stock\\\_prediction.ipynb
```
> \\\*\\\*Note:\\\*\\\* `yfinance` fetches live data from Yahoo Finance. An internet connection is required. If you get a yfinance error, run `pip install yfinance --upgrade`.
---
Files
```
\\\_Stock\\\_Prediction/
├──\\\_stock\\\_prediction.ipynb   # Main Jupyter Notebook
└── README.md                      # This file
```
