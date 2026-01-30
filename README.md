📈 Quantitative Trading System — NIFTY 50 (5-Minute Data)

🎯 Objective - 
Build an end-to-end quantitative trading pipeline that combines market regime detection and machine learning to improve trade quality and reduce drawdowns in intraday index trading.

🔹 Project Breakdown (High Level)

1️⃣ Data Engineering

What I did:
Collected, cleaned, and aligned 5-minute NIFTY spot, futures, and options data, including contract rollovers and dynamic ATM option selection.

2️⃣ Feature Engineering

What I did:
Created trading features using EMA indicators, options Greeks, IV metrics, PCR, and futures basis to capture trend, volatility, and derivatives positioning.

3️⃣ Market Regime Detection (HMM)

What I did:
Used Hidden Markov Models to classify market regimes into Uptrend, Downtrend, and Sideways, enabling regime-aware decision making.

4️⃣ Trading Strategy (EMA 5/15)

What I did:
Designed and backtested an EMA(5/15) crossover strategy, taking trades only in favorable regimes and avoiding sideways markets.

5️⃣ Machine Learning Enhancement

What I did:
Applied XGBoost and LSTM models to predict trade profitability and filter out low-quality trades before execution.

6️⃣ Trade & Performance Analysis

What I did:
Analyzed high-profit (outlier) trades using duration, volatility, Greeks, regime, and time-of-day to identify what drives strong performance.

🧠 Key Results

Regime filtering reduces drawdowns

ML models improve trade consistency

LSTM captures time-dependent market patterns

🛠 Tech Stack

Python, Pandas, NumPy
Scikit-learn, XGBoost
TensorFlow / Keras, hmmlearn
Matplotlib, Seaborn

📌 Educational & research project — not financial advice.
