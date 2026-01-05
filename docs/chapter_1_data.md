# Chapter 1: Data Acquisition & Connectivity Architecture

## 1. Data Source and Integrity
Our primary liquidity provider is **Pepperstone**, utilizing the **MetaTrader 5 (MT5)** gateway. The data integrity is paramount for statistical inference; therefore, we implement a **Singleton Connector Pattern** to manage sessions and prevent data corruption.

## 2. Hybrid Connectivity Logic (Linux/Windows)
Given the OS-specific constraints of the `MetaTrader5` library, we utilize a **Decoupled Architecture**:

* **Production Layer (Live/Windows):** Connects directly to Pepperstone via `mt5.initialize()`.
* **Development Layer (Local/Linux):** Utilizes a `LocalDataManager` that fetches historical data from cached Parquet/CSV files located in the `data/` directory.



## 3. Data Pipeline Specifications
The $US30$ time series is processed using the following ETL (Extract, Transform, Load) pipeline:

### 3.1 Extraction Parameters
* **Symbol:** `US30`
* **Timeframe:** `H1` (Selected to minimize microstructure noise while maintaining enough samples for ADF tests).
* **Depth:** 2,000+ bars (Approx. 1-2 years of historical data).

### 3.2 Cleaning & Pre-processing
Actuarial models are sensitive to outliers and gaps. Our pipeline handles:
1.  **Weekend Gaps:** Removal of non-trading hours to prevent artificial volatility spikes.
2.  **Missing Ticks:** Linear interpolation for minor missing data points.
3.  **Log-Returns Transformation:** Conversion of raw prices to log-returns to ensure stationarity in variance where applicable.

## 4. Environment Security
We implement a `.env` strategy to decouple credentials from the source code. Under no circumstances are the `MT5_LOGIN` or `MT5_PASSWORD` committed to the version control system.

---
*Next Step: [Chapter 2: Exploratory Data Analysis (EDA)](./chapter_2_eda.md)*