# Project: Algorithmic Trading Strategy

**Course:** Machine Learning for Trading (CS7646)

## **The Challenge**
The objective was to create an automated trading strategy for the stock **JPM (JPMorgan Chase)** during the volatile periods surrounding the 2008 financial crisis. The goal was to outperform a standard "Buy and Hold" benchmark by identifying optimal entry and exit points for long and short positions.

## **The Approach**
I compared two distinct methodologies:

### 1. Manual Strategy
I developed a rule-based system relying on three technical indicators:
* **Bollinger Band Percent (BBP)**: Identifying price deviations from the moving average.
* **Relative Strength Index (RSI)**: Detecting overbought/oversold conditions.
* **Percentage Price Indicator (PPI)**: Measuring momentum.

*Logic*: The system triggered trades when indicators crossed specific thresholds (e.g., RSI < 30 indicating oversold).

### 2. Strategy Learner (Random Forest)
I framed the trading problem as a **classification problem** rather than a regression problem.
* **Input Features**: Windowed time-series data of the technical indicators (BBP, RSI, PPI).
* **Target**: Classifying price movement as `UP`, `DOWN`, or `FLAT`.
* **Model**: A **Random Forest Learner** (Bagging + Random Trees) was trained to recognize non-linear patterns in the market data that strict thresholds might miss.

## **The Results**
* **Manual Strategy**: While effective in the *in-sample* (training) period, it struggled to generalize to the *out-of-sample* (testing) period due to the rigidity of the hard-coded thresholds.
* **Strategy Learner**: The Random Forest learner significantly outperformed the Manual Strategy. It successfully adapted to market noise and achieved a higher cumulative return than the benchmark, demonstrating that ML-based approaches offer superior flexibility in volatile markets compared to static technical analysis.