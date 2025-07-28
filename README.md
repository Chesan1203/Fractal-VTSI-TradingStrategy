# 📈 Fractal-VTSI Volatility Strategy: Backtest, Analytics, and Visualization

A Python-based backtesting framework that combines **Fractal-based signals** with **Volatility Triggered Strategy Index (VTSI)** (custom indicator) to identify profitable trade opportunities in Indian stock markets.

---

## 🧠 Project Overview

This project explores an **Adaptive trend-following strategy**. It combines:
- **Price Action** (Fractals: identifying reversal points)
- **Volatility Shifts** (via a custom VTSI metric)

Trades are triggered only when both indicators **align on the same day** — ensuring high-probability entries. 
This strategy is applied to **handpicked NSE stocks** using historical data **(2020-01-01 to 2024-01-01)**, and the results are evaluated using key **performance metrics like Sharpe Ratio, Annualized Return, and Volatility.**
The outputs are visualized via **Google Sheets** and an **interactive Power BI dashboard**.


---

## 🚀 Features

- ✅ **Fractal** detection (bullish and bearish)
- 📉 **VTSI** computation and filtering
- 📊 **Performance metric** generation (Return, Volatility, Sharpe Ratio)
- 📤 Automated export of **stock-wise metrics** to Google Sheets and local `.csv` files
- 📁 CSV export of **trade logs** for all stocks.
- 📈 **Power BI dashboard** for analysis & visualization

---

## 📂 Data Source

- Historical daily stock data was sourced from **Yahoo Finance** using the `yfinance` Python library.  
- The dataset spans from **January 1, 2020** to **January 1, 2024**, covering End-of-Day (EOD) prices for selected NSE stocks.

---

## 📌 Strategy Explanation

### 🔹 1. Fractal Detection  
Identifies:
- **Bullish Fractal :** Local bottom — Long signal  
- **Bearish Fractal :** Local top — Short signal

### 🔹 2. VTSI (Volatility Triggered Strategy Index)  
A custom index derived from recent price volatility and trend acceleration.  
Used to **confirm strong directional momentum**.

### 🔹 3. Entry Conditions  
- A **Bullish Fractal** (local bottom) appears 
- **VTSI crosses +0.7 or +0.6 threshold** (stock-dependent)
  
### 🔹 4. Exit Conditions  
- A **Bearish Fractal** (local top) appears 
- The trade is already in an open position  

Trades are **initiated at the Closing price of the same day**.

---

## 📊 Target Stocks

Based on detailed analysis of momentum patterns and VTSI signal behavior, the following **NSE-listed equities** were finalized for backtesting. 
These stocks demonstrated consistent volatility and trend reversals, making them well-suited for this strategy.

### 🔸 VTSI > 0.7 Threshold
- `ADANIENT.NS`
- `ADANIPOWER.NS`
- `HINDALCO.NS`
- `M&M.NS`

### 🔸 VTSI > 0.6 Threshold
- `JSWSTEEL.NS`
- `TATAMOTORS.NS`
- `RELIANCE.NS`


---

## 📈 Result Metrics

Each stock's performance is evaluated on:

| Metric                  | Description |
|-------------------------|-------------|
| **Total Return**        | Net return over 4 years |
| **Annualized Return (%)** | CAGR-style growth rate |
| **Annualized Volatility (%)** | Risk (std dev of daily returns) |
| **Sharpe Ratio**        | Risk-adjusted return |

The computed metrics for all stocks are programmatically uploaded to a [Google Sheet](https://docs.google.com/spreadsheets/d/1q59yBxa2XyC5PvaDHATyyfM6BlNdN5QeTWMcEkRCHus/edit?usp=sharing) for further visualization and analysis.

---

## 📁 Output & File Handling

### ✅ Files Generated:
- `fractal_signals_<stock>.csv` — All valid trade entries  
- `summary_metrics.csv` — Overall performance metrics  

> Full CSVs are excluded from GitHub to avoid clutter.  
📁 A **sanitized sample** of the daily results is available here: [`/Results/`](./Results/)  
📦 Download all 7 CSVs in one archive: [`Fractal-VTSI-CSVs.zip`](./sample_output/Fractal-VTSI-CSVs.zip)

---

## 📊 Power BI Dashboard

This interactive Power BI report provides a complete visual summary of the **Fractal-VTSI trading strategy**, including:

- **Stock Price Trends**: View how each stock performed from 2020–2023.
- **Portfolio Value Over Time**: Combined performance of all trades executed under the strategy.
- **Final Portfolio Metrics**:  
  - 💰 Final Portfolio Value  
  - 📈 Total Long Trades  
  - 📉 Total Short Trades
- **Portfolio Value by Stock**: Pie chart showing stock-wise capital allocation and growth.
- **Trade Opportunities by Stock**: Bar chart visualizing how many times valid trade signals were triggered for each stock.
- **Final Returns by Stock**: Breakdown of absolute profit/loss from each stock.
- **Interactive Filters**: Toggle individual stocks to isolate their impact across all charts.

📊 A fully interactive Power BI dashboard is available here: 
[🔗 Fractal_VTSI Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNmM4YjM4YWQtMzk4My00MWNmLTkwNTMtYmFjZTlmYjJmOWMzIiwidCI6IjkyYzI0YjQ4LTEzMDQtNGMyZi1iMTZjLWQ5MWRhNjY3MTVkOSIsImMiOjl9)
> 💡 **Tip**: For the best viewing experience, try selecting **one stock at a time** using the left-hand filter. This helps you clearly see how each stock performed across all charts without clutter.


---

## 🧪 How to Run

1. Install required Python libraries
2. Set up Google Sheets API credentials (JSON file)
3. Update placeholder fields in the notebook:
   - `"your_credentials.json"` → path to your JSON file  
   - `"your_sheet_url"` → your Google Sheet URL  
4. Run the notebook: `Fractal-VTSI-Trading.ipynb`

---

## 🧰 Dependencies

Although `requirements.txt` is not included, here are the key libraries:
```bash
pandas
numpy
matplotlib
gspread
oauth2client
yfinance
