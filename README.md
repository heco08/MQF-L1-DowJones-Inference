# 📚 Book 1: The Dow Jones and Statistical Inference
## Master-Quant Framework (MQF) - Foundational Collection

### 1. Executive Summary
This repository is the first module of the **Master-Quant Framework (MQF)**. It focuses on the quantitative analysis of the **Dow Jones Industrial Average ($US30$)**. As an actuarial-based system, it prioritizes the statistical validation of mean-reverting processes (Ornstein-Uhlenbeck) over heuristic trading patterns.

### 2. Theoretical Framework
We analyze the index through the lens of stochastic differential equations:

$$dx_t = \theta (\mu - x_t) dt + \sigma dW_t$$

Our objective is to calculate the **speed of reversion ($\theta$)** and the **Hurst Exponent ($H$)** to verify if the market is in a stationary state ($H < 0.5$).

### 3. Methodology
* **Phase 1:** High-fidelity data extraction via MetaTrader 5 (Pepperstone).
* **Phase 2:** Statistical moments analysis and distribution fitting.
* **Phase 3:** Risk modeling using Value-at-Risk (VaR) and Expected Shortfall.

### 4. Technical Stack
* **Python 3.10+**
* **Infrastucture:** MT5 Bridge (Pepperstone).
* **Core Quants:** Pandas, Numpy, Scipy, Statsmodels.

---
**Lead Actuary / Quant:** HECTOR DAVID ROQUE BARAJAS
**Status:** Chapter 0 - Strategic Foundation Complete.
