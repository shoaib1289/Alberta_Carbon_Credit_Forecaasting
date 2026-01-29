

# Carbon Credit Market Analysis & Forecasting (Alberta TIER)

## Overview
This project analyzes Alberta carbon offset registry data and historical TIER carbon
credit prices to understand supply-side dynamics and forecast market prices.
The objective is to demonstrate an end-to-end analytics workflow combining
SQL-based data preparation, exploratory analysis, and time-series forecasting.

The project emphasizes correct data granularity, reproducible pipelines,
and explainable modeling decisions rather than complex black-box approaches.

---

## Problem Statement
Carbon credit markets are influenced by long-term regulatory policy, project-level
supply dynamics, and market adoption. The goals of this project are:

- Clean and prepare large-scale registry data with inconsistent formats
- Engineer meaningful supply-side features at an appropriate temporal level
- Explore relationships between registry metrics and market prices
- Forecast carbon credit prices using interpretable time-series models

---

## Data Sources
- **Carbon Offset Registry Data**
  - Project-level offset records (1M+ rows)
  - Includes quantities, project dates, status, ownership, and expiry information

- **Carbon Credit Price Data**
  - Historical Alberta TIER carbon credit prices
  - Daily observations aggregated to monthly averages for modeling

---


## SQL: Data Cleaning & Preparation
The SQL script performs:
- Schema standardization and type casting
- Date normalization and validation
- Data quality checks (invalid quantities, expiry logic)
- Creation of analysis-ready tables

This step ensures consistent, reliable inputs before Python-based analysis.

---

## Exploratory Analysis (Python)
The analysis notebook focuses on:
- Missing data diagnostics and data quality assessment
- Feature engineering (offset age, time to expiry, quantity metrics)
- Monthly aggregation of registry data to match market price granularity
- Exploratory relationships between supply-side metrics and prices

Registry data is aggregated before merging with prices to avoid artificial
inflation of observations and misleading correlations.

---

## Forecasting Approach
Price forecasting treats carbon credit prices as a pure time series.

Key steps:
- Monthly aggregation of price data
- Trend and seasonality assessment using STL decomposition
- Stationarity testing (ADF)
- ARIMA modeling with train/test validation
- Forecast evaluation using RMSE and residual diagnostics

STL results indicate a strong trend component and weak seasonality, motivating
a non-seasonal ARIMA model for interpretability and robustness.

---

## Key Findings
- Carbon credit prices are primarily trend-driven with limited seasonal effects
- Registry supply metrics provide context but do not fully explain price movements
- Simple, interpretable models perform well given limited historical data

---

## Limitations
- Monthly sample size is relatively small
- Policy and regulatory changes introduce structural breaks
- Demand-side transaction data is not directly observed

---

## Tools & Technologies
- SQL (data cleaning and validation)
- Python (Pandas, NumPy, Statsmodels, Matplotlib, Seaborn)
- Time-series analysis (STL, ARIMA)

---

## Next Steps
- Incorporate additional policy or compliance signals
- Explore scenario-based forecasting
- Productionize the pipeline with scheduled updates
