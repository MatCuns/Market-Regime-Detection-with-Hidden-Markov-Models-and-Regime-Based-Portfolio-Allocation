# Market Regime Detection with Hidden Markov Models and Regime-Based Portfolio Allocation

## Project Overview

Financial markets move through different phases characterized by changes in returns and volatility.  
This project uses a **Hidden Markov Model (HMM)** to detect hidden market regimes and explores how these regimes can be used to adjust portfolio exposure.
These regimes are **not defined manually**.  
The model identifies statistical states, and the regimes are interpreted afterward by analyzing their average returns and volatility.

| Regime | Description | Characteristics |
|------|------|------|
| Low Volatility Regime | Stable market conditions | Positive or moderate returns and low volatility |
| High Volatility Regime | Uncertain market environment | Unstable returns and elevated volatility |
| Extreme Volatility Regime | Market stress periods | Large negative returns and volatility spikes |

For example:

- a regime with **positive returns and low volatility** can be interpreted as a stable market environment  
- a regime with **higher volatility and unstable returns** represents uncertain market conditions  
- a regime with **large negative returns and volatility spikes** usually corresponds to crisis periods
  
The goal is to identify different market environments and test whether a **regime-based allocation strategy** can improve risk management compared to a passive benchmark.

---

# Methodology

The project follows four main steps.

### 1. Data Collection

The historical daily price csvdata of ACWI for proxy ov a global equity index is downloaded from.

From the price series, the following variables are computed:

- daily returns
- rolling volatility

I also include US 3 months T-bill bonds as cashlike defensive sleeves
---

### 2. Feature Construction

The regime model is estimated using a feature matrix that includes:

- daily returns
- rolling volatility

These variables capture changes in market behavior over time.

---

### 3. Regime Detection

Market regimes are estimated using a **Gaussian Hidden Markov Model** with three hidden states.

The model assumes that financial markets switch between different hidden regimes, each characterized by different statistical properties of returns and volatility.

The HMM estimates:

- the most likely regime at each point in time
- the transition probabilities between regimes

---

### 4. Portfolio Strategy

Portfolio exposure is adjusted depending on the detected regime.

Example allocation logic:

- **Low volatility regime:** higher exposure to equities  
- **High volatility regime:** reduced equity exposure  
- **Extreme volatility regime:** defensive positioning
  
---

# Backtest and Benchamark

A regime-based allocation strategy is evaluated using historical backtesting.

The strategy is compared to a **Buy & Hold benchmark of ACWI** and to just holding cash.

Performance metrics include:

- CAGR
- volatility
- maximum drawdown
- Sharpe ratio

---

# Limitations

Some limitations should be considered:

- regimes are statistical and may not perfectly match economic cycles
- regime detection may react slowly to sudden market changes
- results depend on model assumptions and parameters

---

# Tools and libraries

The project is implemented using:

- Python
- pandas
- numpy
- hmmlearn
- matplotlib

---

