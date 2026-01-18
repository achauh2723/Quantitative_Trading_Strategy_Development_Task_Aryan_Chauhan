# Quantitative_Trading_Strategy_Development_Task_Aryan_Chauhan

# PROJECT OVERVIEW
This project builds an end-to-end quantitative trading pipeline using NIFTY 50 5-minute data (~1 year).
It includes data cleaning, feature engineering, regime detection, strategy backtesting, and ML enhancement (XGBoost + LSTM) to improve trade filtering.

Pipeline:
Data Fetching → Cleaning → Feature Engineering → Regime Detection → EMA Strategy → Backtesting → ML Filter → Outlier Analysis

Note: Futures historical data could not be fetched due to account/data access restriction, so strategy was mainly validated on Spot + derived datasets.


_______________________________________________________________________________________________________________________________



# INSTALLATION INSTRUCTIONS

1) Clone the Repository:
git clone <your-github-repo-link>
cd <your-project-folder>

2) Create Virtual Environment:
python -m venv venv

Activate it:
venv\Scripts\activate

3) Install Required Libraries
pip install -r requirements.txt

4) Extra Dependencies (Important for this project)

If any package is missing, install manually:

pip install pandas numpy matplotlib scikit-learn
pip install xgboost
pip install tensorflow
pip install hmmlearn
pip install joblib

5) Jupyter Notebook Setup
pip install notebook
jupyter notebook



_______________________________________________________________________________________________________________________________



# HOW TO RUN:

Run notebooks in order:

01_data_fetching.ipynb → Fetch/Load data

02_data_cleaning.ipynb → Clean & align 5-min data

03_feature_engineering.ipynb → Features + IV calculation

04_strategy_backtest.ipynb → EMA 5/15 + Regime strategy + metrics

05_ml_models_xgb_lstm.ipynb → Train XGBoost + LSTM + ML-filtered backtest

06_outlier_analysis.ipynb → Trade outlier detection & cleaned equity analysis




_______________________________________________________________________________________________________________________________


# PROJECT STRUCTURE EXPLANATION

📦 Quantitative_Trading_Strategy_Development_Task
│
├── 📂 data
│   ├── instruments.csv
│   ├── nifty_futures_5min.csv
│   ├── nifty_options_5min.csv
│   └── nifty_spot_5min.csv
│
├── 📂 data_clean
│   ├── nifty_futures_5min_clean.csv
│   ├── nifty_options_5min_clean.csv
│   ├── nifty_spot_5min_clean.csv
│   └── nifty_merged_5min.csv
│
├── 📂 data_features
│   └── nifty_features_5min.csv
│
├── 📂 data_regime
│   ├── nifty_with_regime_5min.csv
│   └── nifty_with_regime_fixed_5min.csv
│
├── 📂 models
│   └── xgboost_model.pkl
│
├── 📂 plots
│   └── equity_comparison.png
│
├── 📂 results
│   ├── backtest_metrics.csv
│   ├── data_cleaning_report.txt
│   ├── test_trades.csv
│   └── train_trades.csv
│
├── 📂 results_clean
│   ├── equity_clean_curve.csv
│   └── trades_clean.csv
│
└── 📂 results_ml
    ├── equity_curve_comparison.png
    └── equity_curves_comparison.csv



_______________________________________________________________________________________________________________________________



# KEY RESULTS SUMMARY 

Strategy Used:
EMA 5/15 crossover strategy
Regime Filter applied
Long only in regime +1
Short only in regime -1
No trades in regime 0

ML Enhancement:
Model A: XGBoost (Time-series CV)
Model B: LSTM (10 candle sequence input)
ML Filter rule: take trade only when prediction confidence > 0.5

Final Comparison:
Baseline strategy performance was compared with:
Baseline
XGBoost filtered strategy
LSTM filtered strategy
Equity curve plots and performance metrics are included in results.