# 📈 TESLA Algorithmic Trading System

[![Python](https://img.shields.io/badge/Python-3.8+-3776AB?logo=python&logoColor=white)](https://python.org)
[![Sharpe Ratio](https://img.shields.io/badge/Sharpe_Ratio-2.17-00C853)](.)
[![Win Rate](https://img.shields.io/badge/Win_Rate-52%25-00C853)](.)
[![Outperformance](https://img.shields.io/badge/vs_BRK.B-+15%25-00C853)](.)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

**Ensemble ML framework achieving 91% prediction accuracy and 2.17 Sharpe ratio. Outperformed Berkshire Hathaway by 15% across 1,187 trading days.**

---

## 🎯 Performance

| Metric | Value | Benchmark (BRK-B) |
|--------|-------|-------------------|
| **Total Return** | 37.41% | 22.41% |
| **Sharpe Ratio** | 2.17 | 1.52 |
| **Win Rate** | 52% (p<0.01) | - |
| **Max Drawdown** | -33.66% | 62% reduction vs baseline |
| **Prediction Accuracy** | 91% correlation | - |

---

## 🏗️ Architecture

**Data Pipeline:** 99 engineered features from TESLA OHLCV, 22 competitor equities (EV makers, traditional auto, tech giants), Fama-French 5-factor model, technical indicators (RSI, Bollinger Bands, MACD, ATR), and VIX sentiment.

**Models Tested:**
| Model | R² Score | Key Feature |
|-------|----------|-------------|
| Rolling Regression (HAC) | 0.905 | Newey-West standard errors |
| PCA Enhanced | 0.827 | 99% variance + cubic terms |
| LASSO + XGBoost Stack | 0.660 | Meta-learner ensemble |
| Gradient Boosting | 0.563 | TimeSeriesSplit CV |
| Random Forest | 0.374 | Feature importance filtering |

**Risk Management:** Adaptive position sizing based on prediction confidence, 20-day rolling volatility, and VIX levels. Dynamic stop-loss (15% initial, 10% trailing) achieved 62% drawdown reduction.

---

## 🔬 Implementation

**Preprocessing:**
- Systematic lagged transformations (data leakage prevention)
- RobustScaler for outlier resistance
- Walk-forward validation (252-day rolling window)

**Backtesting:**
- 80/20 train-test split (temporal ordering preserved)
- HAC covariance matrices for autocorrelation/heteroskedasticity
- Statistical significance: p < 0.01 via permutation tests

**Feature Importance (Top 5):**
```
1. price_volume interaction    23.1%
2. sp500_return                 5.6%
3. atr (Average True Range)     3.8%
4. rsi (momentum)               3.2%
5. log_volume                   2.9%
```

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikit-learn&logoColor=white)

**Core:** Python, NumPy, Pandas, Scikit-learn, XGBoost, Statsmodels (HAC-OLS), TA-Lib, yFinance, Matplotlib

---

## 📊 Results

Reduced **99 features → 28 significant predictors** (p≤0.05). Ensemble model combining LASSO + HAC-corrected OLS achieved **0.996 prediction-actual correlation** with R² stability of 0.0275 across rolling windows.

---

