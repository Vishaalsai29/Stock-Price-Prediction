# Stock Price Prediction (Time Series Forecasting)

## 📌 Project Overview  
This project aims to predict Microsoft’s stock price using **Time Series Forecasting and Machine Learning Models**. By analyzing historical stock trends, volatility, and external market influences, we evaluate different modeling techniques to determine the most effective prediction approach.

## 🔍 Key Objectives  
- Perform **Exploratory Data Analysis (EDA)** on Microsoft stock data to identify **trends, volatility, and anomalies**.  
- Implement **multiple forecasting models** including **Random Forest, SARIMA, and LSTM** to predict stock price movements.  
- Compare model performance based on **accuracy, mean absolute error (MAE), and root mean square error (RMSE)**.  

## 🗃 Dataset & Preprocessing  
- **Data Source:** Yahoo Finance via the `yfinance` Python library.  
- **Timeframe:** January 2021 – March 2024 (focused on post-pandemic trends).  
- **Data Features:**  
  - **Numerical Features:** Open, High, Low, Close, Volume.  
  - **Derived Features:** Lag values for trend analysis.  
- **Handling Missing Data:** Removed anomalies and filled gaps using forward fill techniques.  
- **Data Stationarity:** Conducted **Augmented Dickey-Fuller (ADF) Test** to verify stationarity before modeling.  

## 📊 Key Findings  
| **Metric** | **Observation** |  
|------------|----------------|  
| **Trend** | Increasing stock price with major declines in **2020 (COVID-19)** and **2022**. |  
| **Volatility** | High fluctuation in **daily stock returns**, peaking during economic events. |  
| **Seasonality** | No strong cyclical patterns were detected in stock movements. |  

## 🏆 Model Development & Performance  
### **1️⃣ Non-Time Series Model: Random Forest**  
- **Features:** Open, High, Low, Volume, Lag1 (Trend)  
- **Limitations:** Did not perform well due to lack of sequential dependencies.  

### **2️⃣ Time Series Models**  
- **Linear, Quadratic, Cubic, Quartic Trend Models** → Increasing complexity improved RMSE but lacked real-world generalization.  
- **SARIMA (p=1, d=1, q=1, Seasonal Order=(0,0,0,0))** → Improved short-term predictions with better stability.  
- **LSTM (Long Short-Term Memory Network)**  
  - **Sequence Length:** 60 days  
  - **Optimizer:** Adam  
  - **Loss Function:** Mean Squared Error  
  - **Best Performance:** Predicted stock trends closely with **low RMSE (7.98)**.  

## 🎯 Model Comparison  
| **Model** | **MAE** | **RMSE** | **Observations** |  
|------------|--------|---------|----------------|  
| **Random Forest** | 9.76 | 12.33 | Poor for time-series forecasting |  
| **Linear Trend** | 76.67 | 77.04 | Basic trend modeling |  
| **Quadratic Trend** | 41.17 | 41.67 | Better trend fitting |  
| **Cubic Trend** | 21.50 | 22.13 | Improved accuracy |  
| **Quartic Trend** | 5.99 | 6.95 | Strongest polynomial fit |  
| **SARIMA (p=1, q=1)** | 9.17 | 10.98 | Stable short-term forecasting |  
| **LSTM** | **6.50** | **7.98** | Best-performing model |  

## 🚀 Conclusion  
- **LSTM was the most effective model**, demonstrating the lowest RMSE and tracking stock movements closely.  
- **SARIMA performed well for short-term forecasting**, while **polynomial trend models captured overall movement**.  
- **Random Forest struggled with time-series predictions** due to its inability to capture sequential dependencies.  

## 🔮 Future Steps  
- Extend LSTM with **attention mechanisms** for improved sequence understanding.  
- Integrate **external market indicators** (e.g., inflation, interest rates) for enhanced predictive accuracy.  
- Deploy the model using **FastAPI and Streamlit for real-time stock predictions**.

## 🔗 References  
- **Yahoo Finance API**: [https://pypi.org/project/yfinance/](https://pypi.org/project/yfinance/)  
- **Time Series Forecasting Techniques**: [https://otexts.com/fpp3/](https://otexts.com/fpp3/)  
