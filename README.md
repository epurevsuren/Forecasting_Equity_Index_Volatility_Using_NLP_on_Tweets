# Forecasting Equity Index Volatility Using NLP on Tweets

This project explores the use of **Natural Language Processing (NLP)** and **time series forecasting** to predict short-term volatility in the **S&P 500 index** using tweets from former U.S. President Donald J. Trump. The hypothesis is that high-impact political communication, especially around fiscal and monetary policy, can significantly move financial markets.

The pipeline combines **rule-based NLP feature engineering**, **financial market data**, and an **LSTM neural network** to generate realistic trading signals.

🔗 **Colab Notebook**: [Open in Google Colab](https://colab.research.google.com/drive/1TwJyS6djZpY8QcP3FX-A_Gfzu5Qcp0YD?usp=sharing)

---

## 📌 Project Overview
- **Problem Statement**: Political tweets, particularly from Trump during his presidency, often had measurable effects on equity indices. This project builds an NLP framework to quantify and forecast those effects.  
- **Objective**: Predict **5-day forward returns** of the S&P 500 using a combination of:
  - Tweet-derived features (policy keywords, named entities, POS-based verb counts)
  - Market context (daily Open prices)  
- **Impact**:
  - Provides interpretable, tweet-driven trading signals  
  - Enhances short-term volatility forecasting  
  - Supports event-driven trading, risk analysis, and policy monitoring  

---

## 🛠️ Methodology
### 1. Tweet Feature Engineering
- **Keyword Flags**: Detects policy-related terms (e.g., stimulus, tariffs, interest rates, COVID-19).  
- **POS & NER Features** (via spaCy):
  - Policy verbs (e.g., “cut”, “ban”, “sign”)  
  - Named entities (dates, money amounts, geopolitical entities)  

### 2. Market Data
- Source: **Yahoo Finance** (S&P 500 OHLC daily prices)  
- Label: **5-day forward return** from each day’s Open price  

### 3. Model
- **LSTM-based sequence model** with 5-day sliding windows  
- Input: Tweet-derived features + Open prices  
- Output: Predicted return (regression)  

### 4. Trade Evaluation Logic
- Converts predicted returns into **Buy/Sell signals**  
- Evaluates predictions against **intraday High/Low prices** to assess if trades were realistically achievable  

---

## 📊 Results
- **Dataset**: Trump tweets (2016–2021) + S&P 500 daily prices (~1,100 days)  
- **Model Performance**:
  - MAE ≈ **1.5%**  
  - RMSE ≈ **1.9%**  
  - R² ≈ **0.41**  
- **Trade Simulation**:
  - Hit Rate: **~63%** (predicted price reached intraday)  
  - Direction Match: **~68%** (predicted vs actual direction)  
- **Interpretability**: Predictions can be linked back to specific tweet content (e.g., stimulus announcements, tariff threats).  

---

## 🚀 How to Run
1. Clone this repo:
   ```bash
   git clone https://github.com/epurevsuren/Forecasting_Equity_Index_Volatility_Using_NLP_on_Tweets.git
   cd Forecasting_Equity_Index_Volatility_Using_NLP_on_Tweets
