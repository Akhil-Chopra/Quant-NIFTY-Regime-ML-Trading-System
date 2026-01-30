📈 Quantitative Trading System — NIFTY 50 (5-Minute Data)
Project Overview

This project implements an end-to-end quantitative trading system for the NIFTY 50 index using 5-minute interval data.
It demonstrates practical expertise in:

Financial data engineering

Feature engineering with derivatives data

Market regime detection using Hidden Markov Models

Algorithmic trading strategy design

Machine learning–based trade filtering (XGBoost & LSTM)

Statistical analysis of high-performance trades

The system integrates spot, futures, and options market data to create a regime-aware, ML-enhanced trading strategy with detailed performance and trade behavior analysis.

🎯 Objective

Build a complete quantitative trading pipeline covering:

Data acquisition & cleaning

Feature engineering (technical + derivatives-based)

Market regime detection

Rule-based trading strategy

Machine learning enhancement

Advanced trade performance analysis

🧾 Part 1: Data Acquisition & Engineering
Data Sources

NIFTY 50 Spot

OHLCV (5-minute)

NIFTY Futures

Current month contract

Monthly rollover handling

OHLCV + Open Interest

NIFTY Options Chain

ATM, ATM±1, ATM±2

Call & Put

LTP, IV, Open Interest, Volume

Deliverables

nifty_spot_5min.csv

nifty_futures_5min.csv

nifty_options_5min.csv

Data Cleaning

Missing value handling

Outlier removal

Timestamp alignment

Futures contract rollover adjustment

Dynamic ATM strike calculation

Outputs:

Cleaned datasets

data_cleaning_report.txt

Data Merging

Spot, futures, and options merged on timestamp

Output:

nifty_merged_5min.csv

🧠 Part 2: Feature Engineering
Technical Indicators

EMA(5) — Fast EMA

EMA(15) — Slow EMA

(Used exclusively for trade signals)

Options Greeks (Black-Scholes)

Computed using risk-free rate = 6.5%:

Delta

Gamma

Theta

Vega

Rho

For ATM Call & Put options.

Derived Features

Average IV

IV Spread (Call IV − Put IV)

PCR (OI-based)

PCR (Volume-based)

Futures Basis

Spot & Futures Returns

Delta Neutral Ratio

Gamma Exposure

Final Feature Set

Output:

nifty_features_5min.csv

🔄 Part 3: Market Regime Detection
Hidden Markov Model (HMM)

Library: hmmlearn

Number of states: 3

Training data: First 70%

Regimes
Label	Description
+1	Uptrend
0	Sideways
−1	Downtrend
HMM Input Features

Average IV

IV Spread

PCR (OI)

ATM Delta

ATM Gamma

ATM Vega

Futures Basis

Spot Returns

Visualizations

Price chart with regime overlay

Regime transition matrix

Regime statistics

Regime duration histogram

📊 Part 4: Trading Strategy
Strategy Logic (EMA 5/15)
Long Entry

EMA(5) crosses above EMA(15)

Regime = +1

Enter next candle open

Short Entry

EMA(5) crosses below EMA(15)

Regime = −1

Enter next candle open

Exit

Opposite EMA crossover

🚫 No trades in Regime 0

Backtesting

Train: First 70%

Test: Last 30%

Metrics

Total Return

Sharpe Ratio

Sortino Ratio

Calmar Ratio

Max Drawdown

Win Rate

Profit Factor

Avg Trade Duration

Total Trades

🤖 Part 5: Machine Learning Enhancement
Problem Definition

Binary classification:

Target: Trade profitable (1) or not (0)

Features

Engineered features

Regime label

Time features

Lagged returns

Signal strength

Models
Model A — XGBoost

TimeSeriesSplit CV

Gradient boosting classifier

Model B — LSTM

Sequence length: 10 candles

Architecture:

LSTM → Dropout → Dense → Sigmoid

ML-Enhanced Backtest

Trades executed only when:

ML confidence > 0.5

Performance compared:

Baseline EMA

Regime + XGBoost

LSTM-filtered strategy

🔍 Part 6: High-Performance Trade Analysis
Outlier Detection

Z-score > 3

Focus on highly profitable trades

Feature Analysis

Regime

IV

ATR

Time of day

Greeks

Trade duration

EMA gap

PCR

Visualizations

PnL vs Trade Duration scatter

Box plots

Correlation heatmaps

Time-of-day analysis

Key Insights

Percentage of outlier trades

PnL comparison (outliers vs normal)

Regime concentration

Time-of-day effects

Volatility characteristics

Distinguishing features of top trades

⚙️ Installation
pip install -r requirements.txt

▶️ How to Run

Run notebooks sequentially from 1_data_acquisition.ipynb

Models are saved automatically to /models

Results & plots saved to /results and /plots

📌 Key Results Summary

Regime-aware trading significantly reduces drawdowns

ML filtering improves trade quality

LSTM captures temporal dependencies missed by static models

High-performing trades show strong regime & volatility alignment

📚 Technologies Used

Python, Pandas, NumPy

XGBoost

TensorFlow / Keras

hmmlearn

Matplotlib, Seaborn

Scikit-learn

📜 Disclaimer

This project is for educational and research purposes only.
Not financial advice.