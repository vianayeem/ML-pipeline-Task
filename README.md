# Crypto Trader Behavior vs Market Sentiment Analysis

<!--
This README documents the analysis performed for the assignment.
The project studies how trader performance and behavior change under different
market sentiment conditions (Fear vs Greed).
-->

---

# Project Overview

This project analyzes cryptocurrency trading behavior using historical trade data combined with the Fear & Greed sentiment index.

The objective of the analysis is to:

- Understand whether trader performance changes under different sentiment conditions
- Analyze how trader behavior (frequency, leverage, trade size) varies with sentiment
- Segment traders into behavioral groups
- Derive actionable strategy recommendations

The analysis was conducted using Python in a Jupyter Notebook environment.

---

# Repository Structure

```
crypto-trader-sentiment-analysis/

data/
    fear_greed_index.csv
    trader_historical_data.csv

notebooks/
    analysis.ipynb

outputs/
    Trade_Frequency_Sentiment.png
    Trade_Size_Sentiment.png
    Trade_Size_Distribution.png
    Drawdown_proxy.png
    Trade_Frequency_vs_Market_Sentiment.png
    Long_vs_Short_Behavior_Sentiment.png
    Leverage_Distribution.png
    Average_PnL_Trade_Size_Segment.png

README.md
requirements.txt
```

<!--
The outputs folder contains charts generated from the notebook using plt.savefig().
-->

---

# Dataset Description

Two datasets were used in this project.

## 1. Trader Historical Data

This dataset contains trade-level execution information including:

- account ID
- coin traded
- execution price
- trade size in tokens
- trade size in USD
- trade direction
- closed PnL
- trade timestamp
- transaction identifiers

This dataset represents the trading activity of multiple crypto traders.

---

## 2. Market Sentiment Dataset

The second dataset contains the Fear & Greed Index, which represents overall cryptocurrency market sentiment.

Sentiment categories include:

- Fear
- Neutral
- Greed

The sentiment data is recorded daily and was aligned with trading data at the daily level.

---

# Data Preparation

The following preprocessing steps were performed before analysis:

1. Loaded both datasets using Pandas
2. Checked number of rows and columns
3. Identified missing values
4. Checked duplicate records
5. Converted timestamp columns into datetime format
6. Aggregated trading data to daily level
7. Merged trading data with sentiment dataset using date alignment

These steps ensured both datasets were properly structured for analysis.

---

# Feature Engineering

Several features were created to analyze trader behavior.

## Win Indicator

A binary variable was created to indicate profitable trades.

```python
merged["win"] = (merged["closed_pnl"] > 0).astype(int)
```

---

## Leverage Proxy

A leverage proxy was created using trade size relative to the starting position.

```python
merged["leverage"] = merged["size_usd"] / (merged["start_position"].abs() + 1)
```

This helps estimate trader risk exposure.

---

## Behavioral Metrics

Additional metrics created for analysis include:

- trade frequency per day
- average trade size
- long vs short trade ratio
- leverage distribution
- daily PnL per trader

These metrics help identify behavioral patterns in trading activity.

---

# Analysis

The analysis focuses on understanding how trader behavior changes depending on market sentiment.

---

# Trader Performance vs Market Sentiment

Trader performance was compared across Fear and Greed market conditions.

Metrics analyzed include:

- Profit and Loss (PnL)
- Win rate
- Drawdown proxy

Visualization generated:

- Drawdown_proxy.png

This helps determine whether trader profitability varies with market sentiment.

---

# Behavioral Changes Based on Sentiment

Trader behavior was analyzed using multiple metrics.

Metrics studied:

- trade frequency
- trade size
- position direction (long vs short)
- leverage usage

Generated charts include:

- Trade_Frequency_Sentiment.png
- Trade_Size_Sentiment.png
- Trade_Size_Distribution.png
- Trade_Frequency_vs_Market_Sentiment.png
- Long_vs_Short_Behavior_Sentiment.png
- Leverage_Distribution.png

These visualizations illustrate how trader behavior shifts across sentiment regimes.

---

# Trader Segmentation

Traders were segmented into behavioral groups to better understand performance differences.

---

## Segment 1 — High vs Low Trade Size Traders

Traders were classified based on median trade size.

Groups:

- High trade size traders
- Low trade size traders

Performance comparison chart:

- Average_PnL_Trade_Size_Segment.png

---

## Segment 2 — Frequent vs Infrequent Traders

Traders were categorized based on number of trades executed.

- Frequent traders perform higher numbers of trades.
- Infrequent traders trade less often.

This segmentation helps identify how trading activity impacts performance.

---

## Segment 3 — Consistent vs Inconsistent Traders

Trader consistency was measured using win rate.

Groups:

- Consistent winners (win rate above threshold)
- Inconsistent traders

This analysis helps identify traders with stable performance patterns.

---

# Key Insights

## Insight 1 — Trading Activity Increases During Greed

Traders tend to increase trading frequency during Greed periods, indicating higher confidence and speculative activity.

---

## Insight 2 — Larger Trades Lead to Higher Volatility

Traders executing larger position sizes show greater PnL variability, indicating higher risk exposure.

---

## Insight 3 — Consistent Traders Demonstrate Better Risk Management

Traders with higher win rates tend to exhibit more stable performance patterns compared to inconsistent traders.

---

# Strategy Recommendations

Based on the analysis, the following strategy ideas were proposed.

---

## Strategy 1 — Risk Reduction During Fear Markets

During Fear sentiment periods:

- reduce leverage usage
- reduce trade sizes
- avoid excessive trading frequency

This helps limit losses during uncertain market conditions.

---

## Strategy 2 — Controlled Participation During Greed Markets

During Greed sentiment periods:

- increase participation in strong market trends
- maintain controlled leverage levels
- avoid excessive risk exposure

This allows traders to capture opportunities while managing downside risk.

---

# How to Run the Project

Install dependencies:

```
pip install -r requirements.txt
```

Run the notebook:

```
jupyter notebook notebooks/analysis.ipynb
```

---

# Tools Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook

---

# Conclusion

This project demonstrates how combining trading data with market sentiment indicators can reveal useful insights into trader behavior.

The results show that market sentiment influences trading activity, risk exposure, and profitability patterns. Understanding these relationships can help develop more effective trading strategies and risk management approaches.

<!--
End of README
-->