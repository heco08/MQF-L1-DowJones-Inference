# Chapter 0: Philosophical and Mathematical Foundation
**Author:** HECTOR DAVID ROQUE BARAJAS  
**Project:** MQF - Book 1: Dow Jones Statistical Inference  

---

## 1. Thesis and Research Question
The core objective of this research is to move away from technical heuristics and towards **Probabilistic Modeling**. We treat the **Dow Jones Industrial Average ($US30$)** as a continuous-time stochastic process. 

**The Question:** Can we statistically distinguish between a "Random Walk" and a "Mean-Reverting" regime in intraday timeframes for the $US30$?

## 2. Mathematical Foundation: The Ornstein-Uhlenbeck Process
To model mean reversion, we utilize the **Ornstein-Uhlenbeck (OU) SDE**:

$$dx_t = \theta (\mu - x_t) dt + \sigma dW_t$$

### 2.1 Variable Definition from an Actuarial Perspective
* **$\theta$ (Speed of Reversion):** This is our "Risk Multiplier." A higher $\theta$ implies a shorter exposure time, reducing the probability of a black swan event affecting our position.
* **$\mu$ (Long-term Mean):** The "Equilibrium Price." Unlike retail "Support/Resistance," this is a statistically calculated center of gravity.
* **$\sigma$ (Volatility):** The standard deviation of the noise ($dW_t$). This defines our **Value-at-Risk (VaR)** boundaries.



## 3. Statistical Testing Framework
We will validate our thesis using three primary metrics:

1. **Augmented Dickey-Fuller (ADF) Test:** To identify if the series is stationary ($I(0)$).
2. **Hurst Exponent ($H$):**
    * $H < 0.5$: Mean Reverting (Our Target).
    * $H = 0.5$: Random Walk (No Edge).
    * $H > 0.5$: Trending (Momentum).
3. **Half-Life of Reversion:** Calculated as $\tau = \frac{\ln(2)}{\theta}$. This tells us how long, on average, a trade will stay open.

## 4. Why Pepperstone and MT5?
The choice of infrastructure is a matter of **Data Integrity**.
* **Liquidity:** Pepperstone provides ECN-like spreads, which is vital for mean reversion where the edge is often thin.
* **Granularity:** MT5 allows us to pull tick-level data, essential for calculating high-frequency volatility clusters.

## 5. Conclusion of Chapter 0
We conclude that the $US30$ is not a single process, but a series of shifting regimes. Our goal in the following chapters is to build the code that detects when the "Mean Reversion" regime is active.

---
*Proceed to [Chapter 1: Connectivity Architecture](./chapter_1_data.md)*