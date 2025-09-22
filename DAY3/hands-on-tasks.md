# ⏳ Time-Series Analytics 
**Theme:** Understanding and analyzing temporal data for trends, seasonality, and forecasting.

---

## 🎯 Objective

This session introduces **Time-Series Analysis** using Python. You'll learn how to work with datetime objects, apply smoothing techniques, analyze patterns, and forecast future values using models like ARIMA.


---

## 📦 Required Libraries

```bash
pip install pandas matplotlib statsmodels yfinance
````

```python
import pandas as pd
import matplotlib.pyplot as plt
import statsmodels.api as sm
from statsmodels.tsa.stattools import adfuller
from statsmodels.tsa.arima.model import ARIMA
```

---

## 1️⃣ Datetime Indexing & Resampling

### 📌 Convert Column to Datetime

```python
# https://www.kaggle.com/datasets/just4jcgeorge/stock-prices-csv
df = pd.read_csv("stock_prices.csv")
df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)
df = df.sort_index()
df.head()
```

### 🔄 Resampling (Upsampling vs. Downsampling)

```python
# Weekly average closing price
weekly = df['Close'].resample('W').mean()

# Monthly sum of volume
monthly = df['Volume'].resample('M').sum()

weekly.plot(title='Weekly Average Close')
plt.show()
```

---

## 2️⃣ Rolling & Window Functions

### 📊 Moving Averages & Smoothing

```python
df['MA_20'] = df['Close'].rolling(window=20).mean()
df['MA_50'] = df['Close'].rolling(window=50).mean()

df[['Close', 'MA_20', 'MA_50']].plot(figsize=(12,6), title="Moving Averages")
plt.xlabel("Date")
plt.ylabel("Price")
plt.grid(True)
plt.show()
```

### 📉 Rolling Std & EWMA

```python
df['Rolling_Std'] = df['Close'].rolling(20).std()
df['EWMA_20'] = df['Close'].ewm(span=20, adjust=False).mean()
```

---

## 3️⃣ Decomposition & Stationarity

### ⚙️ Seasonal Decomposition

```python
decomp = sm.tsa.seasonal_decompose(df['Close'], model='additive', period=30)
decomp.plot()
plt.show()
```

* **Trend**: Long-term progression.
* **Seasonal**: Repeating short-term cycle.
* **Residual**: Random noise or irregularities.

---

### 📈 ADF Test for Stationarity

```python
result = adfuller(df['Close'].dropna())
print(f"ADF Statistic: {result[0]}")
print(f"p-value: {result[1]}")

if result[1] < 0.05:
    print("✅ Series is stationary")
else:
    print("❌ Series is non-stationary")
```

---

### 🔁 Differencing to Achieve Stationarity

```python
df['Close_diff'] = df['Close'] - df['Close'].shift(1)
df['Close_diff'].dropna().plot(title="Differenced Series")
plt.show()
```

---

## 4️⃣ Forecasting with ARIMA

### ⚠️ ARIMA(p,d,q) Model Overview

* **p**: Lag order (AR)
* **d**: Degree of differencing
* **q**: Moving average order

```python
# Fit ARIMA model
model = ARIMA(df['Close'], order=(5,1,2))
model_fit = model.fit()

# Summary
print(model_fit.summary())

# Forecast next 30 days
forecast = model_fit.forecast(steps=30)
forecast.plot(title="30-Day Forecast")
plt.show()
```

---

## 💻 Hands-On Activity

Use a dataset such as **Apple (AAPL) stock price history** via `yfinance`:

```python
import yfinance as yf
apple = yf.download('AAPL', start='2020-01-01', end='2023-12-31')
apple.to_csv('aapl_stock.csv')
```

### Tasks:

1. ✅ Resample stock price to **weekly frequency**.
2. ✅ Plot **20-day and 50-day** moving averages on closing prices.
3. ✅ Decompose the time-series into **trend, seasonal, residual**.
4. ✅ Test for **stationarity** using ADF.
5. ✅ Forecast the **next month’s** prices using **ARIMA**.

---

## 🧠 Recap

| Concept              | Description                                   |
| -------------------- | --------------------------------------------- |
| Resampling           | Aggregate data into new time buckets          |
| Rolling Stats        | Smooth data for trend detection               |
| Decomposition        | Split time-series into components             |
| Stationarity Testing | Check if data has constant mean/variance      |
| ARIMA Forecasting    | Predict future values using past dependencies |

---

## 📚 Resources

* [📘 Statsmodels Docs](https://www.statsmodels.org/stable/tsa.html)
* [📈 ADF Test Explanation](https://machinelearningmastery.com/time-series-data-stationary-python/)
* [📊 ARIMA Guide](https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/)
* [📦 yfinance API](https://pypi.org/project/yfinance/)

---

🔍 *Time-Series lets you not only analyze the past but also anticipate the future — one trend at a time.*

