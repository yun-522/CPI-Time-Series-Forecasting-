# CPI Time-Series Forecasting  

## Overview  
This project was developed as part of **QBUS2820 (Time Series and Forecasting)** at the University of Sydney.  
The task was to design, implement, and evaluate forecasting models to predict the **quarterly Australian Consumer Price Index (CPI)** for the period **March 2022 – December 2023**, based on historical data from 1997–2021.  

The datasets (`CPI_train.csv` and `CPI_test.csv`) were provided by the unit coordinator.  
Due to licensing restrictions, the full datasets are **not included in this repository**. A small [sample dataset](./sample_CPI_train.csv) with the first 5 rows of training data is provided for illustrative purposes.  

---

## Objectives  
1. **Develop accurate forecasts**  
   - Train models on historical CPI data (1997–2021).  
   - Generate 8-step-ahead forecasts covering March 2022 – December 2023.  

2. **Compare multiple forecasting approaches**  
   - **Naïve model**: baseline assumption that the last observed value continues.  
   - **Seasonal Naïve model**: extends the last value from the same quarter of the previous year.  
   - **Exponential Smoothing (Holt-Winters)**: captures level, trend, and seasonality.  
   - **ARIMA / Auto-ARIMA**: models autoregressive and moving average components, with automatic parameter selection.  

3. **Evaluate accuracy and robustness**  
   - Use **Mean Squared Error (MSE)** on the test set as the primary evaluation metric.  
   - Check residuals to ensure no significant autocorrelation or bias.  
   - Ensure reproducibility with a fixed random seed and documented code pipeline.  

---

## Tech Stack  
- **Language:** Python (Jupyter Notebook)  
- **Libraries:**  
  - Data manipulation: `pandas`, `numpy`  
  - Time series modeling: `statsmodels`, `pmdarima`  
  - Visualization: `matplotlib`  
- **Data Sources:**  
  - `CPI_train.csv` — training data (1997–2021) provided in QBUS2820.  
  - `CPI_test.csv` — withheld dataset (2022–2023) used for evaluation.  

---

## Repository Structure  
cpi-time-series-forecasting/  
│── [implementation.pdf](https://github.com/yun-522/CPI-Time-Series-Forecasting-/blob/468eac5e6500ada7958161fead65b28bc15761de/implementation.pdf) # Code + report (Jupyter Notebook exported to PDF/HTML)  
│── [sample_CPI_train.csv](./sample_CPI_train.csv) # First 5 rows of training data (for illustration)  
│── README.md # Project description  

---

## Key Results  
- **Baseline performance:**  
  - Naïve and Seasonal Naïve models provided simple, interpretable forecasts.  
  - Seasonal Naïve outperformed standard Naïve by accounting for yearly CPI cycles.  

- **Exponential Smoothing (Holt-Winters):**  
  - Accurately modeled both level and seasonality.  
  - Produced smoother forecasts, but performance lagged slightly behind ARIMA.  

- **ARIMA models:**  
  - Stationarity achieved through differencing.  
  - Manual ARIMA fitting gave reasonable accuracy, but required parameter tuning.  

- **Auto-ARIMA:**  
  - Automatically selected optimal (p, d, q) parameters and seasonal components.  
  - Delivered the **lowest test MSE = 1.55**, outperforming all other models.  
  - Residual diagnostics showed minimal autocorrelation, confirming good model fit.  

⚠️ **Note:** The final MSE on the withheld test dataset was not computed within the submitted code.  
The forecasts were generated and submitted, and the official MSE = **1.55** was provided later by the instructor.  

---

## Insights  
- **CPI dynamics:**  
  - The CPI series showed both **trend** and **seasonality**, meaning simple models risk underfitting.  
  - Differencing was necessary to stabilize the mean before applying ARIMA.  

- **Baselines are strong starting points:**  
  - Naïve and Seasonal Naïve provided competitive benchmarks, reminding us that simple models can often perform reasonably well.  

- **Exponential Smoothing is robust but less precise:**  
  - Holt-Winters captured level and seasonal components, but forecast error accumulated across multiple steps ahead.  

- **ARIMA-based methods dominate:**  
  - By incorporating autoregressive terms, moving average components, and differencing, ARIMA captured both short-term shocks and long-term seasonal cycles.  
  - Auto-ARIMA streamlined the modeling process and avoided manual trial-and-error in parameter tuning.  

- **Practical takeaway:**  
  - For CPI and similar economic indicators, **Auto-ARIMA strikes the best balance** between accuracy, interpretability, and reproducibility, making it suitable for policy and business decision-making.  

---
