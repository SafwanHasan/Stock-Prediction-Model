# 📈 Analyzing Risk Sentiment & Predicting Stock Price Trends from 10-K Filings Using LSTM

This project analyzes whether **risk sentiment extracted from Item 1A of 10-K filings** can help explain or predict **S&P 500 stock price movements**.  
Using **FinBERT**, macroeconomic indicators (CPI & EFFR), and an **LSTM forecasting model**, this repository provides a complete pipeline from:

**10-K text → Sentiment → Dataset → LSTM Forecast → Interactive Visualization**

A public **Streamlit web app** is provided for exploring sentiment, stock performance, correlations, and future predictions.

---

## 🚀 Features

- Extracts sentiment from 10-K filings using **FinBERT**
- Builds a merged dataset with:
  - Sentiment scores  
  - S&P 500 price  
  - CPI  
  - Effective Federal Funds Rate (EFFR)
- Trains a **12-month → next-month** LSTM forecasting model
- Generates **rolling forecasts** from Jan 2024 to Apr 2025
- Includes complete dataset, model weights, and training notebooks
- Provides an interactive **Streamlit dashboard**

---

## 📁 Repository Structure

