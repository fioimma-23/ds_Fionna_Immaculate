# Data Science Assignment

**Candidate:** Fionna Immaculate  
**Date:** 20 November 2025

---

## Project Overview
This project analyzes whether trader performance on Hyperliquid is influenced by Bitcoin market sentiment (Fear, Neutral, Greed).

The workflow includes:  
- Data cleaning  
- Merging sentiment and trading data  
- Exploratory Data Analysis (EDA)  
- Statistical testing  
- Predictive modeling  
- Insights & conclusions

---

## Data Sources

### 1. Hyperliquid Historical Trader Data  
Contains execution-level trade information:

- `Account`: Unique trader wallet/account identifier  
- `Coin`: Trading pair or instrument  
- `Execution Price`: Price at which the trade was executed  
- `Size Tokens`: Trade size in token units  
- `Size USD`: Trade size converted to USD  
- `Side`: BUY or SELL action  
- `Timestamp IST`: Execution timestamp in IST timezone  
- `Start Position`: Position held before this trade  
- `Direction`: Direction of the trade (Buy/Sell)  
- `Closed PnL`: Profit or loss realized upon trade closure  
- `Transaction Hash`, `Order ID`, `Trade ID`: Unique identifiers  
- `Crossed`: Boolean flag indicating crossed order  
- `Fee`: Trading fee paid  
- `Timestamp`: Additional timestamp column (verification purposes)  

Supports daily PnL calculation and trader behavior analysis.

### 2. Bitcoin Fear & Greed Index  
Daily market sentiment values:

- `timestamp`: UNIX epoch timestamp  
- `value`: Numeric Fear & Greed Index score (0–100)  
- `classification`: Market sentiment label (e.g., Fear, Greed, Neutral)  
- `date`: Human-readable date, used to merge with trader data  

---

## Data Preparation Steps

- Standardized column names to snake_case  
- Converted `timestamp_ist` to datetime format  
- Extracted dates for daily aggregation  
- Computed per-day summary metrics:  
  - Total trades  
  - Total volume (USD)  
  - Total PnL  
  - Win rate  
  - Buy vs. sell counts  
- Merged trader data with Fear & Greed Index on `date`  
- Filled missing sentiment values with `"unknown"`  

---

## Exploratory Data Analysis (EDA)

- Daily PnL varies significantly with bursts of high activity  
- 7-day rolling average smooths short-term volatility  
- Greed days exhibit higher PnL variance versus fear days  
- No sentiment category shows consistently superior profitability  

_All plots saved in `outputs/`_

---

## Statistical Analysis

Performed Mann–Whitney U test comparing PnL on Fear vs. Greed days:

| Statistic | p-value |
|-----------|----------|
| 2251.0    | 0.5872   |

Interpretation: No statistically significant difference. Market sentiment does **not** affect trader profitability in this dataset.

---

## Predictive Modeling

**Model:** Random Forest Classifier  
**Features:**  
- `total_trades`  
- `total_volume_usd`  
- `win_rate`  

**Target:** Profitable day (1 if total PnL > 0; else 0)  

**Performance:**  
- Accuracy: 92.98%  
- ROC AUC: 0.8004  

**Feature Importance:**  
| Feature         | Importance |
|-----------------|------------|
| win_rate        | 0.503      |
| total_trades    | 0.266      |
| total_volume_usd| 0.230      |

Conclusion: Trader behavior, especially win rate, dominates profitability prediction; sentiment has low predictive power.

---

## Insights

- Fear & Greed Index sentiment shows no significant correlation with trader profit outcomes  
- Win rate and trading volume strongly predict profitable days  
- High PnL days align with increased liquidity and active trading behavior  
- Behavior-focused analytics outperform sentiment-driven strategies in this context  

---

## How to Run This Project

1. Open `notebook_1.ipynb` in Google Colab  
2. Upload CSV files into `csv_files/` folder  
3. Run all cells for data cleaning and EDA  
4. Run subsequent cells for statistical analysis and predictive modeling  
5. View generated plots in `outputs/`  
6. Refer to the final report `ds_report.pdf` for comprehensive analysis  

---

## Requirements

- Python 3.x  
- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- scipy  

---

## Final Notes

This project demonstrates an end-to-end data science workflow, including data cleaning, merging, exploratory analysis, hypothesis testing, predictive modeling, and insight generation for real-world crypto trading analytics.

---

