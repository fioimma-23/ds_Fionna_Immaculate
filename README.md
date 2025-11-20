\#  Data Science Assignment

\*\*Candidate:\*\* Fionna Immaculate    
\*\*Date:\*\* 20 November 2025  

\---

\#\# Project Overview    
This project analyzes whether trader performance on Hyperliquid is influenced by Bitcoin market sentiment (Fear, Neutral, Greed).  

The workflow includes:    
\- Data cleaning    
\- Merging sentiment \+ trading data    
\- Exploratory Data Analysis (EDA)    
\- Statistical testing    
\- Predictive modeling    
\- Insights & conclusions  

\---  
\#\#  Project Structure

ds\_Fionna\_Immaculate/  
│  
├── notebook\_1.ipynb  
├── csv\_files/  
│   ├── hyperliquid\_data.csv  
│   ├── fear\_greed\_index.csv  
├── outputs/  
│   ├── daily\_total\_pnl\_with\_rolling.png  
│   ├── pnl\_by\_sentiment.png  
├── ds\_report.pdf  
└── README.md

\---

\#\# Data Sources

\#\#\# 1\. Hyperliquid Historical Trader Data    
Columns include:

\- \`Account\`    
\- \`Coin\`    
\- \`Execution Price\`    
\- \`Size Tokens\`    
\- \`Size USD\`    
\- \`Side\`    
\- \`Timestamp IST\`    
\- \`Start Position\`    
\- \`Direction\`    
\- \`Closed PnL\`    
\- \`Transaction Hash\`    
\- \`Order ID\`    
\- \`Crossed\`    
\- \`Fee\`    
\- \`Trade ID\`    
\- \`Timestamp\`  

This dataset supports daily PnL calculation and behavior analysis.

\---

\#\#\# 2\. Bitcoin Fear & Greed Index    
Columns:

\- \`timestamp\`    
\- \`value\`    
\- \`classification\`    
\- \`date\`  

Used to merge sentiment with trading performance.

\---

\#\# Data Preparation Steps

\- Renamed columns to snake\_case.    
\- Converted \`timestamp\_ist\` to datetime.    
\- Extracted dates for daily aggregation.    
\- Computed:  
  \- total trades    
  \- total volume (USD)    
  \- total PnL    
  \- win rate    
  \- buy/sell counts    
\- Merged with sentiment dataset on \`date\`.    
\- Filled missing sentiment values with \`"unknown"\`.

\---

\#\# Exploratory Data Analysis (EDA)

\#\#\# Key visual insights:  
\- Daily PnL fluctuates significantly across days.    
\- A 7-day rolling average smooths volatility.    
\- Greed days show high variance; Fear days more stable.    
\- No sentiment group shows consistently higher profitability.

All plots stored in:    
outputs/

\---

\#\# Statistical Analysis

Performed a \*\*Mann–Whitney U test\*\* comparing Fear vs Greed PnL.

\*\*Result:\*\*

Statistic: 2251.0  
p-value: 0.5872

\*\*Interpretation:\*\*    
\- No statistically significant difference.    
\- Market sentiment does \*\*not\*\* affect trader PnL in this dataset.

\---

\#\# Predictive Modeling

\#\#\# Model: Random Forest Classifier    
\*\*Features:\*\*    
\- \`total\_trades\`    
\- \`total\_volume\_usd\`    
\- \`win\_rate\`  

\*\*Target:\*\* profitable\_day (1/0)

\*\*Performance:\*\*  
Accuracy: 92.98%  
ROC AUC: 0.8004

\#\#\# Feature Importance:

win\_rate 0.503  
total\_trades 0.266  
total\_volume\_usd 0.230

\*\*Conclusion:\*\*    
Trader behavior, especially win rate, is the primary driver of profitability — not sentiment.

\---

\#\# Insights

\- Fear & Greed Index does \*\*not\*\* correlate with profit outcomes.    
\- High trader win rate strongly predicts profitable days.    
\- High PnL days align with higher liquidity/activity.    
\- Behavior-driven analytics outperform sentiment-driven strategies.

\---

\#\# How to Run This Project

1\. Open \*\*notebook\_1.ipynb\*\* in Google Colab    
2\. Upload CSVs into \`csv\_files/\`    
3\. Run all cells for cleaning \+ EDA    
5\. Run all cells for statistical analysis \+ modeling    
6\. View generated plots in \`outputs/\`    
7\. Final report is saved as \`ds\_report.pdf\`

\---

\#\# Requirements  
\- Python 3.x  
\- pandas  
\- numpy  
\- matplotlib  
\- seaborn  
\- scikit-learn  
\- scipy

\---

\#\# Final Notes

This project demonstrates end-to-end data science capability including cleaning, merging, EDA, hypothesis testing, machine learning modeling, and insights generation.

