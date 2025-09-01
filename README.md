# CPI Time-Series Forecasting  

## Overview  
This project was developed as part of **QBUS2820 (Time Series and Forecasting)** at the University of Sydney.  
The goal was to build and evaluate models to **forecast quarterly Australian CPI** (Consumer Price Index) for the period **March 2022 – December 2023**, using historical data from 1997–2021.  

The dataset (`CPI_train.csv` and `CPI_test.csv`) was provided by the unit coordinator.  
Due to licensing restrictions, the full dataset is **not included in this repository**.  

---

## Objectives  
1. **Forecast CPI values**  
   - Use training data (1997–2021) to predict test set (2022–2023).  
   - Multi-step ahead forecasting (8 quarters).  

2. **Compare candidate models**  
   - Naïve and Seasonal Naïve benchmarks.  
   - Holt-Winters exponential smoothing.  
   - ARIMA and Auto-ARIMA.  

3. **Evaluate accuracy**  
   - Forecast accuracy measured using **Mean Squared Error (MSE)** on the withheld test dataset.  
   - Reproducibility ensured with fixed random seed.  

---

## Tech Stack  
- **Language:** Python (Jupyter Notebook)  
- **Libraries:** `pandas`, `numpy`, `statsmodels`, `pmdarima`, `matplotlib`  
- **Data Sources:**  
  - `CPI_train.csv` — training data (1997–2021) provided in QBUS2820.  
  - `CPI_test.csv` — withheld dataset (2022–2023) used for evaluation.  

---

## Repository Structure  
cpi-time-series-forecasting/  
│── [implementation.html](https://github.com/yun-522/CPI-Time-Series-Forecasting-/blob/145e0818421f0b48e9fa387444cbd84ff2b45218/implementation.html) # Code + report (Jupyter Notebook exported to HTML)  
│── [sample_CPI_train.csv](./sample_CPI_train.csv) # First 5 rows of training data (for illustration)  
│── README.md # Project description  

---

## Key Results  
- **Final model:** Auto-ARIMA with seasonal components.  
- **Test performance:** MSE = **1.55** on the withheld dataset.  
- Forecasts successfully captured **trend and seasonal patterns** of CPI.  
- Baseline models (Naïve, Seasonal Naïve) were reasonable but consistently outperformed by ARIMA-based models.  
- Holt-Winters was competitive but slightly less accurate than Auto-ARIMA.  

---

## Insights  
- CPI data required **differencing** to achieve stationarity.  
- **Naïve models** provided a strong baseline for short-term forecasts.  
- **Holt-Winters** captured seasonality but struggled with longer horizons.  
- **Auto-ARIMA** provided the best balance of accuracy, interpretability, and robustness.  

---
