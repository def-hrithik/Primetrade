
# Cryptocurrency Market Sentiment and Trading Activity Dataset

## Overview

This repository contains two complementary cryptocurrency datasets:

1. **Fear & Greed Index Dataset**
2. **Historical Cryptocurrency Trading Dataset**

Together, these datasets enable the analysis of how market sentiment influences trading behavior, profitability, risk-taking, and market participation across different crypto assets.

---

## Dataset Structure

```text
.
├── fear_greed_index.csv
└── historical_data.csv
```

---

# Dataset 1: Fear & Greed Index

## Description

The Fear & Greed Index is a widely used sentiment indicator that measures investor emotions within cryptocurrency markets.

The index ranges from **0 to 100**:

| Range | Classification |
|--------|---------------|
| 0–24 | Extreme Fear |
| 25–44 | Fear |
| 45–54 | Neutral |
| 55–74 | Greed |
| 75–100 | Extreme Greed |

Higher values indicate optimistic market sentiment, while lower values suggest panic and risk aversion.

---

## Dataset Statistics

| Metric | Value |
|----------|--------|
| Records | 2,644 |
| Time Period | Feb 2018 – May 2025 |
| Minimum Value | 5 |
| Maximum Value | 95 |
| Average Value | 46.98 |
| Median Value | 46 |

---

## Features

| Column | Description |
|----------|------------|
| timestamp | Unix timestamp |
| value | Fear & Greed score |
| classification | Sentiment category |
| date | Observation date |

---

## Sentiment Distribution

| Classification | Count |
|---------------|--------|
| Fear | 781 |
| Greed | 633 |
| Extreme Fear | 508 |
| Neutral | 396 |
| Extreme Greed | 326 |

---

## Potential Research Questions

- How does market sentiment affect trading volume?
- Do traders perform better during greed or fear periods?
- Can sentiment predict future profitability?
- Are extreme market emotions followed by reversals?

---

# Dataset 2: Historical Trading Data

## Description

This dataset contains detailed cryptocurrency trading records, including trade execution information, position management, fees, realized profits and losses, and transaction metadata.

The dataset captures both spot and derivatives trading activity across a diverse set of crypto assets.

---

## Dataset Statistics

| Metric | Value |
|---------|---------|
| Total Trades | 211,224 |
| Unique Assets | 246 |
| Buy Trades | 102,696 |
| Sell Trades | 108,528 |
| Total Realized PnL | $10,296,958.94 |
| Total Trading Fees | $245,857.72 |
| Trading Year | 2024 |

---

## Top Traded Assets

| Asset | Trade Count |
|---------|------------|
| HYPE | 68,005 |
| @107 | 29,992 |
| BTC | 26,064 |
| ETH | 11,158 |
| SOL | 10,691 |
| FARTCOIN | 4,650 |
| MELANIA | 4,428 |
| PURR/USDC | 2,774 |
| WLD | 1,983 |
| SUI | 1,979 |

---

## Features

| Column | Description |
|----------|------------|
| Account | Trader account identifier |
| Coin | Cryptocurrency symbol |
| Execution Price | Trade execution price |
| Size Tokens | Quantity traded |
| Size USD | Trade size in USD |
| Side | Buy or Sell |
| Timestamp IST | Trade timestamp |
| Start Position | Position size before execution |
| Direction | Trading action type |
| Closed PnL | Realized profit/loss |
| Transaction Hash | Blockchain transaction reference |
| Order ID | Exchange order identifier |
| Crossed | Whether order crossed the book |
| Fee | Trading fee paid |
| Trade ID | Unique trade identifier |
| Timestamp | Unix timestamp |

---

## Trading Action Categories

The dataset includes several trading activities:

- Open Long
- Close Long
- Open Short
- Close Short
- Buy
- Sell
- Position Reversal
- Liquidation Events
- Auto-Deleveraging
- Settlement Operations

---

# Combined Analysis Opportunities

Because the datasets share a common temporal dimension, they can be merged for advanced behavioral and quantitative finance research.

---

## 1. Sentiment vs Profitability

Investigate whether traders generate higher returns during:

- Extreme Fear
- Fear
- Neutral
- Greed
- Extreme Greed

### Metrics

- Average PnL
- Win Rate
- Sharpe Ratio
- Risk-Adjusted Returns

---

## 2. Sentiment vs Trading Volume

Analyze whether sentiment affects:

- Number of trades
- Average trade size
- Daily volume
- Market participation

---

## 3. Risk-Taking Behavior

Measure changes in:

- Position size
- Leverage usage
- Long/Short exposure
- Asset selection

during different sentiment regimes.

---

## 4. Market Timing Analysis

Evaluate whether traders:

- Buy during fear
- Sell during greed
- Successfully exploit sentiment extremes

---

## 5. Asset-Specific Behavior

Compare how sentiment impacts major assets:

- Bitcoin (BTC)
- Ethereum (ETH)
- Solana (SOL)
- Emerging altcoins

---

# Example Use Cases

## Quantitative Finance

- Alpha generation
- Signal engineering
- Factor modeling

## Behavioral Finance

- Investor psychology
- Herd behavior
- Fear-driven selling

## Machine Learning

- Trade outcome prediction
- Profitability forecasting
- Sentiment-aware trading models

## Time Series Analysis

- Regime detection
- Volatility modeling
- Market cycle identification

---

# Data Quality Notes

## Fear & Greed Dataset

- Daily frequency
- No missing sentiment categories observed
- Covers multiple bull and bear market cycles

## Trading Dataset

- Large-scale transaction-level data
- Multiple assets represented
- Includes execution costs and realized profitability
- Suitable for aggregation at trade, asset, daily, weekly, or monthly levels

---

# Suggested Feature Engineering

## Sentiment Features

- Lagged sentiment values
- Sentiment momentum
- Rolling sentiment averages
- Sentiment volatility

## Trading Features

- Daily volume
- Trade frequency
- Net exposure
- Position duration
- Realized returns
- Fee-adjusted profitability

## Combined Features

- Sentiment-adjusted returns
- Fear-period performance
- Greed-period performance
- Sentiment regime indicators

---

# Conclusion

This dataset provides a unique opportunity to study the interaction between cryptocurrency market sentiment and real-world trading activity. By combining investor psychology indicators with detailed execution-level trading records, researchers can investigate behavioral finance dynamics, develop predictive trading models, and evaluate sentiment-driven market strategies across multiple crypto market cycles.

---

# Citation

If you use this dataset in academic research, trading strategy development, or machine learning projects, please cite the dataset repository appropriately.

---

# License

Specify the appropriate license for dataset usage and redistribution before publishing.
