# 📈 Telkomsel School Visit Forecasting using ARIMA

## 📌 Project Overview

This project was developed during an internship at Telkomsel Branch Surabaya. The objective is to forecast school visit activities conducted by Telkomsel using the AutoRegressive Integrated Moving Average (ARIMA) method.

<img width="619" height="224" alt="image" src="https://github.com/user-attachments/assets/efa35e57-72d8-4295-9716-ffc325c50676" />

The dataset contains daily school visit records from **1 January 2024 to 9 October 2024** covering multiple educational institutions, including:

* TK
* SD
* SMP
* SMA
* SMK
* Pesantren
* Universitas
* PKBM
* SKB
* SLB
* Kursus

The target variable used in this study is:

**TOTAL KUNJUNGAN (MINUTE)**

The forecasting horizon is **20 days ahead**.

---

## 🎯 Objectives

* Analyze historical Telkomsel school visit data.
* Identify patterns and trends in time series data.
* Build a forecasting model using ARIMA.
* Evaluate forecasting performance.
* Generate future visit predictions to support planning and decision-making.

---

## 🛠️ Tools & Libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Statsmodels
* Scikit-learn

---

## 📊 Research Workflow

The forecasting process consists of the following stages:

1. Reading and Processing Data
2. Creating Pivot Tables
3. Data Grouping
4. Data Cleaning
5. Trend Visualization
6. Time Series Decomposition
7. Stationarity Testing
8. ACF & PACF Analysis
9. ARIMA Parameter Estimation
10. Residual Diagnostics
11. Forecasting

---

## 📂 Project Structure

```text
telkomsel-school-visit-forecasting-arima/
│
├── Code ARIMA/
│   ├── ARIMA.ipynb
│   └── dataset.csv
│
├── figures/
│   ├── time_series_plot.png
│   ├── acf_pacf.png
│   ├── forecast_result.png
│   └── residual_analysis.png
│
└── README.md
```

---

## 📈 Exploratory Analysis

The time series plot shows significant fluctuations in total visit duration over time. The data exhibits high variability with several peaks and sharp declines. No strong seasonal pattern was observed.

### Stationarity Test

#### Augmented Dickey-Fuller (ADF)

| Metric        | Value   |
| ------------- | ------- |
| ADF Statistic | -3.8129 |
| p-value       | 0.0028  |

**Conclusion:** The data is stationary in mean.

#### KPSS Test

| Metric         | Value  |
| -------------- | ------ |
| KPSS Statistic | 1.6003 |
| p-value        | 0.01   |

**Conclusion:** The data is not stationary in variance.

---

## 🔄 Box-Cox Transformation
<img width="627" height="311" alt="image" src="https://github.com/user-attachments/assets/83defb27-a03d-452a-8136-e0e471f039d3" />

Box-Cox transformation was applied to stabilize variance and improve data distribution.

| Metric             | Before | After  |
| ------------------ | ------ | ------ |
| Standard Deviation | 173.83 | 141.80 |

**Lambda:** 0.9663

The transformed data showed a more stable variance and a distribution closer to normality.

---

## 🤖 ARIMA Modeling

Based on ACF and PACF analysis after differencing, the selected model is:

**ARIMA(6,2,1)**

Where:

* p = 6 (Autoregressive)
* d = 2 (Differencing)
* q = 1 (Moving Average)

---

## ✅ Residual Diagnostics

### Ljung-Box Test

| Metric  | Value |
| ------- | ----- |
| p-value | 0.704 |

Conclusion: No significant autocorrelation detected in residuals.

### Shapiro-Wilk Test

| Metric  | Value |
| ------- | ----- |
| p-value | 0.065 |

Conclusion: Residuals are normally distributed.

---

## 📉 Model Evaluation

Data was split into:

* 80% Training Data
* 20% Testing Data

### Evaluation Metrics

| Model        | MAE     | RMSE    | MAPE    |
| ------------ | ------- | ------- | ------- |
| ARIMA(6,2,1) | 138.603 | 178.875 | 143.60% |

---

## 🔮 Forecasting Results

The ARIMA(6,2,1) model was used to forecast school visits for the next 20 days.

| Date       | Forecast |
| ---------- | -------- |
| 2024-10-10 | 497.57   |
| 2024-10-11 | 539.06   |
| 2024-10-12 | 400.86   |
| ...        | ...      |
| 2024-10-29 | 426.77   |

The forecast indicates a relatively stable trend compared to the historical data, which showed more extreme fluctuations.
<img width="597" height="201" alt="image" src="https://github.com/user-attachments/assets/456d9348-d86a-46e4-a3a9-7df164890b7b" />

---

## 💡 Key Learnings

Through this project, several important insights were gained:

* Understanding ARIMA modeling for time series forecasting.
* Performing stationarity testing using ADF and KPSS.
* Applying Box-Cox transformation to stabilize variance.
* Conducting residual diagnostics.
* Evaluating forecasting performance using MAE, RMSE, and MAPE.
* Using data-driven forecasting to support business planning and decision-making.

---

