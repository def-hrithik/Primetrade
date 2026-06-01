# Trading Performance vs Market Sentiment Analysis

This repository contains an exploratory and predictive analysis of trading activity combined with market sentiment data. The notebook analyzes 211,224 trades and 2,644 sentiment observations, then evaluates trader behavior, segment performance, and profitability prediction using sentiment-driven features [cite:1].

## Project Overview

The goal of this analysis is to understand how market sentiment affects trader behavior and outcomes. The notebook merges trade-level data with a fear/greed sentiment index, engineers trader-level features, and evaluates performance across multiple trader segments and sentiment regimes [cite:1].

The analysis also tests whether sentiment-based variables can help predict trade profitability using machine learning models [cite:1].

## Dataset Summary

### Trade Dataset
The trade dataset contains 211,224 rows and 16 columns, with no missing values and no duplicates reported in the notebook [cite:1]. Key fields include:
- Account.
- Coin.
- Execution Price.
- Size Tokens.
- Size USD.
- Side.
- Timestamp IST.
- Start Position.
- Direction.
- Closed PnL.
- Transaction Hash.
- Order ID.
- Crossed.
- Fee.
- Trade ID.
- Timestamp [cite:1].

### Sentiment Dataset
The sentiment dataset contains 2,644 rows and 4 columns, also with no missing values [cite:1]. Key fields include:
- timestamp.
- value.
- classification.
- date [cite:1].

### Merge Logic
The notebook converts both datasets to date format and performs a left merge from trades to sentiment, keeping all trade records while attaching sentiment classification by date [cite:1].

## Methodology

### 1. Data Preparation
The notebook imports pandas, numpy, matplotlib, and seaborn, then loads the trade and sentiment datasets [cite:1]. It checks dimensions, null counts, and duplicates, and converts timestamps into date-based fields for merging [cite:1].

### 2. Feature Engineering
Several analytical features are created from the merged trade-sentiment dataset [cite:1]:
- Daily PnL by account.
- Win indicator based on whether Closed PnL is positive.
- Average trade size by account.
- Trade frequency by account.
- Long/short trade split.
- Trader segmentation by frequency, consistency, and trade size.
- Sentiment flags such as greed, fear, and extreme sentiment categories [cite:1].

### 3. Trader Segmentation
The notebook groups traders into behavioral buckets such as:
- Frequent vs infrequent traders.
- Consistent vs inconsistent traders.
- Small vs large trade size groups [cite:1].

These segments are then compared across sentiment states to identify where performance changes most strongly [cite:1].

### 4. Statistical Analysis
The notebook calculates group-level metrics such as:
- Average Closed PnL.
- Win rate.
- Trade count.
- Direction counts.
- Long/short ratio [cite:1].

A key reported result is a Long/Short Ratio of 1.3, with 98,573 long trades and 75,754 short trades [cite:1].

### 5. Predictive Modeling
The notebook builds a classification target for whether a trade is profitable and uses machine learning models to predict profitability [cite:1]. The engineered features include:
- Sentiment indicators.
- Trader win rate.
- Relative trade size.
- Long/short direction [cite:1].

Two models are trained and compared:
- Random Forest Classifier.
- Gradient Boosting Classifier [cite:1].

## Key Insights

### Trade Direction
Long trades are more common than short trades, with a reported long/short ratio of 1.3 [cite:1]. This suggests the dataset is slightly tilted toward bullish positioning, which may reflect either market structure or trader preference.

### Trade Size
The notebook reports that small-size traders achieved an average PnL of 226.8K with a 44.4% win rate, while large-size traders achieved an average PnL of 416.8K with a 36.2% win rate [cite:1]. This means larger trades produced higher absolute profits, but with lower hit rates, indicating a clear risk-return tradeoff [cite:1].

### Trade Frequency
Infrequent traders performed much better during Greed conditions than frequent traders, with an average PnL of 210.2 for infrequent traders versus 25.0 for frequent traders in Greed sentiment [cite:1]. The notebook interprets this as a roughly 8.4x performance difference, showing that calmer, less active traders may benefit more from strong bullish sentiment regimes [cite:1].

### Sentiment Sensitivity
Consistent traders showed the strongest sensitivity to sentiment, with win rate peaking at 57.2% during Extreme Greed and dropping to 38.6% during Extreme Fear, a gap of 18.6 percentage points [cite:1]. This indicates that even skilled traders are heavily affected by market mood, especially at sentiment extremes [cite:1].

### Sentiment by Trader Segment
The notebook’s sentiment-segment heatmaps suggest that:
- Frequent traders tend to do better in Fear-like environments.
- Infrequent traders benefit more in Greed and Extreme Greed.
- Consistent traders gain the most from positive sentiment and struggle most in negative sentiment [cite:1].

### Profitability Distribution
The notebook states that the dataset contains 211,224 trades and 86,869 profitable trades, which is about 41.1% profitable [cite:1]. That means the classification problem is meaningfully imbalanced and should be interpreted with caution beyond raw accuracy [cite:1].

### Modeling Results
The Random Forest model achieved accuracy of 0.6655 and ROC-AUC of 0.7166, while the Gradient Boosting model achieved accuracy of 0.6564 and ROC-AUC of 0.6853 [cite:1]. The notebook therefore indicates that Random Forest performed better overall for this task [cite:1].

The most important predictive features were trader win rate and trade size relative to the trader’s average size, which suggests that trader-specific behavior matters more than simple sentiment flags alone [cite:1]. Sentiment variables still contributed, but they were weaker than behavioral and sizing features [cite:1].

## Strategy Recommendations

### 1. Use sentiment to size positions
Increase position size when sentiment is strongly aligned with the trader’s edge, especially during Greed or Extreme Greed for traders who historically perform well in those regimes [cite:1]. Reduce size when sentiment turns adverse, especially in Extreme Fear, where win rates were lowest for consistent traders [cite:1].

### 2. Differentiate by trader style
Frequent traders should focus on short-horizon opportunities and avoid overtrading during emotionally unstable conditions [cite:1]. Infrequent traders may benefit from waiting for strong Greed/Extreme Greed environments before deploying capital more aggressively [cite:1].

### 3. Protect capital in fear regimes
The notebook suggests reducing frequency and tightening risk controls during Fear and Extreme Fear [cite:1]. This is especially relevant for consistent traders, whose win rate dropped materially in fear-heavy conditions [cite:1].

### 4. Build a sentiment-aware risk engine
A practical next step is to translate sentiment classification into rules for leverage, stop-loss width, and capital allocation [cite:1]. This can be implemented as a sentiment overlay rather than a standalone strategy signal [cite:1].

### 5. Use behavior over raw sentiment
The modeling section shows that trader win rate and relative trade size are among the strongest predictors of profitability [cite:1]. That means future strategy work should combine sentiment with trader behavior features instead of relying on sentiment alone [cite:1].

## Visualizations Included

The notebook generates several useful visual outputs, including:
- Sentiment frequency heatmap.
- Trader segment performance charts.
- Sentiment-based profitability heatmaps.
- Model result summaries [cite:1].

These visuals support the main conclusion that market sentiment interacts strongly with trader style and trade sizing [cite:1].

## Reproducibility Notes

The notebook is structured as a complete analysis pipeline from loading raw CSVs to merging, segmentation, modeling, and visualization [cite:1]. To reproduce the analysis, ensure that the input CSV files used in the notebook are available with the same filenames and paths referenced in the code [cite:1].

## Suggested Repository Structure

```text
.
├── analysis.ipynb
├── README.md
├── data/
│   ├── ai_data.csv
│   └── ai_greed_index.csv
└── outputs/
    ├── sentiment_segment_heatmap.png
    ├── trader_segments.png
    └── other_charts.png
```

## Limitations

The notebook provides strong descriptive and predictive evidence, but it does not prove causation between sentiment and profitability [cite:1]. The sentiment dataset is daily, so intraday trade dynamics may be partially hidden when merged at the date level [cite:1]. Model scores are useful, but they are still modest enough that any live strategy should be tested with strict out-of-sample validation and transaction-cost awareness [cite:1].

## Final Takeaway

The most important finding is that trader performance is not uniform across sentiment states [cite:1]. Trader style, trade size, and market mood interact in meaningful ways, and the best strategy is likely a sentiment-aware risk framework rather than a simple directional signal [cite:1].
