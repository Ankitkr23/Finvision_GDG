
import yfinance as yf
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd

btc = yf.download("BTC-USD", period="1y", interval="1d") 

# Ensure data is available
if btc.empty:
    print("No BTC-USD data fetched. Check your internet or ticker symbol.")
    exit()

prices = btc["Close"].values  # Extract closing prices
dates = btc.index  # Extract dates

def calculate_stock_span(prices):
    span = np.zeros(len(prices), dtype=int)
    stack = []  # Stack stores (price, index)
    for i in range(len(prices)):
        while stack and stack[-1][0] <= prices[i]:
            stack.pop()
        span[i] = (i - stack[-1][1]) if stack else (i + 1)
        stack.append((prices[i], i))
    return span

stock_span = calculate_stock_span(prices)

btc["MA_50"] = btc["Close"].rolling(window=50).mean()
btc["MA_200"] = btc["Close"].rolling(window=200).mean()

btc["Trend"] = np.where(btc["MA_50"] > btc["MA_200"], "Uptrend", "Downtrend")

threshold = np.mean(stock_span) + 2 * np.std(stock_span)
btc["Breakout"] = np.where(stock_span > threshold, "Yes", "No")

plt.figure(figsize=(14, 7))
plt.plot(dates, prices, label="BTC-USD Price", color='blue', linewidth=1.2)
plt.plot(dates, stock_span * 100, label="Stock Span (Scaled)", color='red', linestyle='--', alpha=0.6)
plt.plot(dates, btc["MA_50"], label="50-day MA", color='green', linewidth=1)
plt.plot(dates, btc["MA_200"], label="200-day MA", color='orange', linewidth=1)

plt.title(" BTC-USD Stock Span & Trend Analysis")
plt.xlabel("Date")
plt.ylabel("Price / Span Value")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

breakout_days = btc[btc["Breakout"] == "Yes"]
print("\n Breakout Signals Detected on These Dates:")
print(breakout_days[["Close", "Breakout"]])
