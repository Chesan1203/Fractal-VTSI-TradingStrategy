# 📈 Fractal-VTSI Trading Strategy (2020–2024 Backtest)

A Python-based backtesting framework that combines **Fractal-based signals** with **Volatility Triggered Strategy Index (VTSI)** to identify profitable long opportunities in Indian stock markets.

---

## 🧠 Project Overview

This project explores an **adaptive trend-following strategy**. It combines:
- **Price Action** (Fractals: identifying reversal points)
- **Volatility Shifts** (via a custom VTSI metric)

Trades are triggered only when both indicators align on the same day — ensuring high-probability entries. The strategy is **backtested** from **Jan 2020 to Jan 2024** across selected Indian stocks.

---

## 🚀 Features

- ✅ Fractal detection (bullish and bearish)
- 📉 VTSI computation and filtering
- 📊 Performance metric generation (Return, Volatility, Sharpe)
- 📤 Automatic export to **Google Sheets**
- 📁 CSV export of trade logs and metrics
- 📈 Power BI dashboard for analysis & visualization

---

## 📂 Data Source

- **Yahoo Finance** via `yfinance` Python library  
  Used to fetch historical EOD data for stocks from **2020-01-01 to 2024-01-01**

---

## 📌 Strategy Explanation

### 🔹 1. Fractal Detection  
Identifies:
- **Bullish Fractal:** Local bottom — potential entry signal  
- **Bearish Fractal:** Local top — exit filter / invalidation

### 🔹 2. VTSI (Volatility Triggered Strategy Index)  
A custom index derived from recent price volatility and trend acceleration.  
Used to **confirm strong directional momentum**.

### 🔹 3. Entry Conditions  
- A **valid fractal (bullish)** appears **AND**
- **VTSI crosses +0.7 or +0.6 threshold** (stock-dependent)

Trades are **initiated at the next day's open price**.

---

## 📊 Selected Stocks

Backtested on Indian equities known for momentum/volatility:

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

Metrics are compiled into both:
- 📄 CSV files (per run)
- 📄 Google Sheet (connected via API)

---

## 📁 Output & File Handling

### ✅ Files Generated:
- `fractal_signals_<stock>.csv` — All valid trade entries  
- `summary_metrics.csv` — Overall performance metrics  
- Data automatically sent to **Google Sheets**

### ❌ Not Uploaded:
> Full CSVs are excluded from GitHub to avoid clutter.  
A sanitized version (`sample_results.csv`) is available inside `/sample_output/`.

---

## 📊 Power BI Dashboard

A separate Power BI report visualizes:
- Trade distributions
- Cumulative P&L
- Stock-wise Sharpe Ratios
- Strategy win-rate

📁 Available in `/visuals/Fractal_VTSI_PowerBI.pbix` *(optional upload)*

---

## 🧪 How to Run

1. **Install dependencies** (see below)
2. Set up Google Sheets API credentials (JSON file)
3. Update placeholder fields in the notebook:
   - `"your_credentials.json"` → path to your JSON file  
   - `"your_sheet_url"` → your Google Sheet URL  
4. Run the notebook: `Fractal-VTSI-Trading.ipynb`

---

## 🔒 Privacy & Security

All API keys, secrets, and personal data are:
- 🔐 **Removed from the repo**
- ✅ Replaced with placeholders
- 📄 Not tracked (via `.gitignore`)

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
