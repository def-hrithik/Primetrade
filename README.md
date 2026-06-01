<div align="center">

# 📈 PrimeTrade

### Trader Behaviour & Sentiment Intelligence Platform

A data-science pipeline that fuses **options trading activity** with **market sentiment signals** to segment traders, predict profitability, and surface actionable P&L insights — powered by Python, scikit-learn, and Jupyter.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?logo=scikitlearn&logoColor=white)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## 📖 Table of Contents

1. [Project Overview](#-project-overview)
2. [Why Sentiment + Trading Data?](#-why-sentiment--trading-data)
3. [Architecture & Pipeline](#-architecture--pipeline)
4. [Data Flow](#-data-flow)
5. [Tech Stack](#-tech-stack)
6. [Project Structure](#-project-structure)
7. [Installation & Setup](#-installation--setup)
8. [Analysis Walkthrough](#-analysis-walkthrough)
9. [Model Reference](#-model-reference)
10. [Key Visualisations](#-key-visualisations)
11. [Results & Insights](#-results--insights)
12. [License](#-license)

---

## 🎯 Project Overview

**PrimeTrade** is an end-to-end data analysis and machine learning project that explores the relationship between **trader behaviour on options markets** and **external market sentiment**. By clustering traders into behavioural segments and training a classifier to predict profitable vs. unprofitable traders, PrimeTrade answers a core question:

> *Does market sentiment actually influence individual trader P&L — and can we predict who will profit?*

### Key Features

| Feature | Description |
|---|---|
| 🧠 **Sentiment Integration** | Merges external sentiment signals with trade-level data for richer feature engineering |
| 👥 **Trader Segmentation** | Unsupervised clustering groups traders by behaviour — frequency, size, timing, and risk appetite |
| 📊 **P&L Attribution** | Breaks down profit/loss by sentiment regime, trader segment, and trade characteristics |
| 🤖 **Predictive Classifier** | Supervised ML model predicts trader profitability with feature importance analysis |
| 📉 **ROC & Confusion Analysis** | Model evaluated end-to-end with ROC curve, AUC score, and confusion matrix |
| 🌡️ **Sentiment Heatmaps** | Cross-tabulated sentiment × segment heatmaps reveal where alpha concentrates |

---

## 🧠 Why Sentiment + Trading Data?

Most trading analyses look at price action in isolation. PrimeTrade takes a different approach:

| Problem | Approach |
|---|---|
| **Sentiment is noisy** | Discretised into regimes (e.g. Fear / Neutral / Greed) and matched to trade timestamps — reducing noise while preserving signal |
| **Traders behave differently** | K-Means clustering surfaces distinct archetypes (e.g. high-frequency small-cap traders vs. low-frequency large-position holders) without labelling bias |
| **P&L is multi-causal** | Feature engineering captures trade size, timing, instrument type, and sentiment context — giving the model a holistic view |
| **Black-box models are hard to trust** | Feature importance plots make the classifier interpretable so results are actionable, not just accurate |

> **Result:** A reproducible, interpretable pipeline that turns raw trade logs and sentiment feeds into structured behavioural intelligence.

---


---

## 🛠 Tech Stack

### Analysis & Modelling (`analysis.ipynb`)

| Library | Version | Purpose |
|---|---|---|
| Python | 3.10+ | Core runtime |
| Pandas | 2.x | Data wrangling & aggregation |
| NumPy | 1.x | Numerical operations |
| scikit-learn | 1.x | K-Means clustering, classifier, metrics |
| Matplotlib | 3.x | Static visualisations |
| Seaborn | 0.x | Heatmaps and styled statistical plots |

### Data

| File / Folder | Description |
|---|---|
| `dataset/` | Raw trade logs and sentiment signal CSVs |

### Outputs

| File | Description |
|---|---|
| `trader_segments.png` | Cluster scatter plot — trader archetypes visualised |
| `pnl_by_sentiment.png` | Bar/box plot of P&L distributions across sentiment regimes |
| `sentiment_segment_heatmap.png` | 2D heatmap: trader segment × sentiment regime |
| `model_roc_confusion.png` | ROC curve + confusion matrix for the classifier |
| `model_feature_importance.png` | Ranked feature importances from the trained model |

---

## 📂 Project Structure

```
Primetrade/
│
├── dataset/                          # Raw input data
│   ├── trades.csv                    # Options trade log (timestamp, size, PnL…)
│   └── sentiment.csv                 # Sentiment signal feed (date, score, regime)
│
├── analysis.ipynb                    # End-to-end analysis notebook
│
├── trader_segments.png               # Output: K-Means cluster visualisation
├── pnl_by_sentiment.png              # Output: P&L by sentiment regime
├── sentiment_segment_heatmap.png     # Output: Segment × Sentiment heatmap
├── model_roc_confusion.png           # Output: Classifier evaluation plots
└── model_feature_importance.png      # Output: Feature importance rankings
```

---

## 🚀 Installation & Setup

### Prerequisites

| Requirement | Notes |
|---|---|
| **Python** ≥ 3.10 | [Download](https://python.org/) |
| **Jupyter** | Comes with Anaconda or install via pip |

### Step 1 — Clone the Repository

```bash
git clone https://github.com/def-hrithik/Primetrade.git
cd Primetrade
```

### Step 2 — Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows
```

### Step 3 — Install Dependencies

```bash
pip install pandas numpy scikit-learn matplotlib seaborn jupyter
```

> Or if a `requirements.txt` is present:
> ```bash
> pip install -r requirements.txt
> ```

### Step 4 — Launch the Notebook

```bash
jupyter notebook analysis.ipynb
```

> Run all cells top-to-bottom. All five output PNGs will be regenerated in the project root.

---

## 📘 Analysis Walkthrough

The `analysis.ipynb` notebook is organised into the following sections:

### 1 · Data Loading & Inspection
Loads trade logs and sentiment data from `dataset/`. Initial shape checks, dtype inspection, and missing-value audit.

### 2 · Preprocessing & Feature Engineering
Parses timestamps, computes per-trade P&L where absent, merges sentiment regimes by date, and engineers rolling trader-level metrics (win rate, average size, trade frequency).

### 3 · Trader Segmentation
Applies K-Means clustering on the engineered feature matrix. The elbow curve guides k selection. Cluster profiles are summarised and saved as `trader_segments.png`.

### 4 · P&L Attribution
Breaks down realised P&L by sentiment regime (`pnl_by_sentiment.png`) and cross-tabulates segment × sentiment to reveal where profitability concentrates (`sentiment_segment_heatmap.png`).

### 5 · Profitability Classification
Labels each trader as profitable or not. Trains a classifier with stratified train/test split. Evaluates with ROC-AUC and confusion matrix (`model_roc_confusion.png`), then extracts and ranks feature importances (`model_feature_importance.png`).

---

## 🤖 Model Reference

### Clustering — K-Means

| Parameter | Value | Notes |
|---|---|---|
| Algorithm | K-Means | Euclidean distance, random init |
| k (clusters) | Tuned via elbow | Typical range 3–6 |
| Features | Win rate, avg size, frequency, sentiment score | Standardised with `StandardScaler` |

### Classification

| Component | Detail |
|---|---|
| Target | Binary — profitable (1) / unprofitable (0) |
| Model | Random Forest / Gradient Boosting (see notebook) |
| Split | Stratified 80/20 train-test |
| Metrics | ROC-AUC, Precision, Recall, F1, Confusion Matrix |
| Interpretability | Feature importance plot (top predictors ranked) |

---

## 📊 Key Visualisations

| Plot | File | What It Shows |
|---|---|---|
| Trader Segments | `trader_segments.png` | 2D cluster scatter of trader archetypes |
| P&L by Sentiment | `pnl_by_sentiment.png` | How sentiment regime shifts realised P&L |
| Sentiment × Segment Heatmap | `sentiment_segment_heatmap.png` | Which trader types profit in which sentiment environments |
| ROC + Confusion Matrix | `model_roc_confusion.png` | Classifier discrimination ability and error types |
| Feature Importance | `model_feature_importance.png` | Top drivers of trader profitability |

---

## 📝 Results & Insights

The analysis surfaces three headline findings:

**Sentiment regime matters.** P&L distributions shift materially across Fear / Neutral / Greed regimes, suggesting sentiment is a genuine edge variable rather than noise.

**Trader archetypes are distinct.** Clustering reveals well-separated behavioural groups — high-frequency small-position traders behave fundamentally differently from low-frequency large-position holders, and their P&L profiles reflect this.

**Profitability is predictable.** The classifier achieves meaningful AUC above a random baseline, with trade size and sentiment score consistently ranking as the top predictive features.

---

## 📝 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with ❤️ using Python, scikit-learn & Jupyter**

</div>
