# 🧠 Comparative Analysis of Time Series Forecasting Using Classical and Machine Learning Models
---

## 📘 Project Overview

This study investigates the effectiveness of five forecasting methods on a real-world retail dataset. It compares classical statistical techniques such as **SARIMA** and **Triple Exponential Smoothing** with advanced machine learning models like **RNN**, **LSTM**, and **SVM**. The models are evaluated on their accuracy in predicting monthly sales trends using error metrics such as **MSE**, **RMSE**, and **MAPE**.

---

## 🎯 Objectives

- Forecast retail sales from 2010–2018 using various modeling techniques.
- Compare classical and machine learning models for forecasting accuracy.
- Identify the most suitable model for short, seasonal datasets.
- Provide recommendations for real-world forecasting practices.

---

## 🧾 Dataset Overview

- **Source**: Retail company in Bosnia and Herzegovina  
- **Published by**: [4TU Centre for Research Data](https://data.4tu.nl/datasets/8f5339ce-4b89-43e3-92cc-40adcb565a9a/1)  
- **Timeframe**: 2010–2018 (2,611 daily records, resampled to monthly)  
- **Characteristics**: Seasonal trends, non-stationary, clean (no missing values)

---
## 🔍 Exploratory Data Analysis (EDA)

### 📈 Monthly Sales Over Time & Threshold Highlights

<p align="left">
  <img src="https://github.com/user-attachments/assets/64fed17d-2581-4049-8244-d5bbd63e75f5" alt="Monthly Sales" width="48%">
</p>

### 🔄 Decomposition (Trend + Seasonality)

<p align="left">
  <img src="https://github.com/user-attachments/assets/06526244-1086-44c3-b9f4-11c439017be0" alt="Decomposition Plot" width="48%">
</p>

### 📦 Monthly Boxplot

<p align="left">
  <img src="https://github.com/user-attachments/assets/f11af21d-9d37-42fa-9e7e-5d39b09543e2" alt="Monthly Boxplot" width="48%">
</p>

### 📊 Distribution of Sales

<p align="left">
  <img src="https://github.com/user-attachments/assets/775edfcb-c7e3-481c-bcec-1aa0ebf36e2c" alt="Sales Distribution Histogram" width="48%">
</p>

These plots helped identify a strong seasonal pattern and upward sales trend, guiding model selection and feature engineering.

---

## 🛠️ Models Used

### 📉 Classical Models
- **SARIMA**: Seasonal Auto-Regressive Integrated Moving Average, auto-tuned via `auto_arima`.
- **Triple Exponential Smoothing**: Holt-Winters method for modeling trend and seasonality.

### 🤖 Machine Learning Models
- **RNN**: 2-layer sequential model using `SimpleRNN` and dropout layers (Keras).
- **LSTM**: 3-layer deep architecture with memory cells, dropout regularization, and `Adam` optimizer.
- **SVM (SVR)**: RBF kernel with hyperparameter optimization using GridSearchCV.

---

## 📐 Model Performance Summary

| Model                     | MSE             | RMSE     | MAPE   |
|--------------------------|-----------------|----------|--------|
| **SARIMA**               | 47.9B           | 218,916  | **7.06%**  |
| Triple Exponential       | 51.9B           | 227,827  | 7.84%  |
| RNN                      | 53.8B           | 231,986  | 8.23%  |
| LSTM                     | 80.4B           | 283,671  | 8.82%  |
| SVM                      | 81.2B           | 284,986  | 10.52% |

---

## 🔑 Key Findings

### 🥇 1. SARIMA Was the Best Overall Performer
- Achieved the **lowest error metrics** (MSE: 47.9B, RMSE: 218,916, MAPE: 7.06%).
- Effectively captured **seasonal patterns and trends**, especially after ensuring stationarity.
- Required minimal data preprocessing when automated parameter selection (`auto_arima`) was used.
<p align="center">
  <img src="https://github.com/user-attachments/assets/fa87c5a5-c1e1-43a9-a0cf-273ac75f48a7" width="50%" />
</p>
<p align="center"><strong>Figure: SARIME model forecasting </strong></p>

### 🔁 2. Triple Exponential Smoothing Was a Strong Traditional Competitor
- Second-best performance (MAPE: 7.84%).
- Fast and computationally efficient.
- Slightly underperformed during rapid growth periods.
<p align="center">
  <img src="https://github.com/user-attachments/assets/d763c1f0-560d-4ed9-9e3d-119a6e2e7616" width="50%" />
</p>
<p align="center"><strong>Figure: Triple Exponential Smoothing Forecasting </strong></p>
### 🧠 3. RNN and LSTM Faced Challenges with Small Datasets
- **RNN** had a MAPE of 8.23%
- **LSTM** had a MAPE of 8.82%
- Forecasts often **too smooth**, missing seasonal signals.
- High computational cost with **limited gain**.
<div style="display: flex; justify-content: center; align-items: center; gap: 40px;">
  <div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/ddb29c27-2451-41ce-bb05-427b6fcfc9ab" width="300px" />
    <p><strong>Figure: RNN model forecasting</strong></p>
  </div>
  <div style="text-align: center;">
    <img src="https://github.com/user-attachments/assets/b14a09cb-ec42-4755-b826-f6b0e3d2fcbf" width="300px" />
    <p><strong>Figure: LSTM model forecasting</strong></p>
  </div>
</div>

### ⚠️ 4. SVM Was the Least Accurate
- MAPE: **10.52%**.
- Misrepresented both dips and spikes.
- Not suitable for univariate time series without engineered features.
<p align="center">
  <img src="https://github.com/user-attachments/assets/01482c01-545c-4832-9a0d-3fb9e93f1e47" width="50%" />
</p>
<p align="center"><strong>Figure: SVM model forecasting </strong></p>

### 📊 5. Classical Models Outperformed Machine Learning on Small Seasonal Data
- Demonstrated that **complexity ≠ accuracy**.
- In short, seasonal datasets, simpler statistical methods **performed best**.
<p align="center">
  <img src="https://github.com/user-attachments/assets/2f283777-23f0-4416-9b5a-f9dc2a865a81" width="50%" />
</p>
<p align="center"><strong>Figure: Comparison of Forecasting Models (only forecasted period) </strong></p>

---

## 🚧 Challenges Faced

- Parameter tuning (SARIMA, SVR) required careful optimization.
- Neural networks underfit due to limited sequence data.
- Ensuring data stationarity for classical models was critical.

---

## 📈 Visual Summary

### 🔍 Model Accuracy Comparison
<p align="left">
  <img src="https://github.com/user-attachments/assets/29af14ea-7593-48ad-8462-ffe1f78d1557" >
</p>
<p align="center"><strong>Figure: Performance comparison of all models </strong></p>
---

## 🧪 How to Run This Project

```bash
# Clone the repository
git clone https://https://github.com/mizanur-ds/Comparative_Analysis_of_Time_Series_Forecasting_Using_Statistical_Methods_-_Machine_Learning_Models.git
Comparative_Analysis_of_Time_Series_Forecasting_Using_Statistical_Methods_-_Machine_Learning_Models

# Create a virtual environment
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
