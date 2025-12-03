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
├── final_dataset.csv # Merged dataset (Sentiment + CPI + EFFR + Stock Price)\
├── model_weights/ # Trained LSTM weights\
├── train.ipynb # Notebook for training the LSTM model\
├── sentiment_processing.ipynb # FinBERT sentiment extraction notebook\
├── README.md # This file

---

## 📊 Project Overview

The **Item 1A (Risk Factors)** section of 10-K filings contains rich qualitative information about risks faced by public companies.  
This project quantifies that risk using FinBERT sentiment analysis and aligns it with historical stock price performance and macroeconomic indicators.

An LSTM model is trained on this multi-source dataset to forecast future S&P 500 prices.

---

## 🧠 Methodology

### 1. Data Sources

- **10-K Sentiment:** Extracted using FinBERT from Item 1A sections  
- **Stock Prices:** S&P 500 historical index (Kaggle)  
- **Macroeconomic Indicators:** CPI and EFFR (FRED API)

### 2. Final Feature Set (4 Inputs)
Sentiment Score
S&P 500 Price
CPI
EFFR

### 3. Input Window

A sliding window of **12 months** is used to predict the next month:
Input shape: (12 months × 4 features)
Output: Next month's stock price


### 4. Model Architecture

- **LSTM layer**: 50 units  
- **Dense layer**: 1 output neuron  
- **Loss function**: Mean Squared Error (MSE)  
- **Optimizer**: Adam (lr = 0.001)  
- **Training Range**: 2014–2022  
- **Testing Range**: 2022–2023  

### 5. Rolling Forecast Strategy

After training, we:

1. Use the last 12 months of 2023  
2. Predict January 2024  
3. Append prediction, slide window  
4. Repeat until April 2025  

---

## 📉 Results

### Model Performance (MAE)

| Model                     | MAE |
|--------------------------|-----|
| Halder MLP               | 218 |
| Halder LSTM              | 180 |
| Halder FinBERT-LSTM     | 174 |
| **Our LSTM (4 features)** | **188** |

Despite using a smaller dataset, our model performs competitively with FinBERT-LSTM baselines.

---

## 🌐 Streamlit Web Application

The Streamlit app allows users to explore:

- Company-level sentiment trends  
- Year-over-year stock changes  
- Sector and industry summaries  
- Correlations (Pearson & Spearman)  
- S&P 500 forecasts (Jan 2024 → Apr 2025)

**🔗 Live Demo:**  
https://sentiment-stock-app.streamlit.app/

---

## ⚠️ Limitations

### 1. Low-frequency sentiment  
Sentiment is annual; quarterly abstraction would improve precision.

### 2. Limited features  
Stock movements depend on many factors not included (VIX, unemployment, earnings, etc.).

### 3. Rolling forecast drift  
Recursive predictions accumulate error.

### 4. Unmodeled external shocks  
Pandemics, rate hikes, and geopolitical events reduce model reliability.

---

## 🧩 Future Work

- Add quarterly / paragraph-level sentiment features  
- Include more macroeconomic indicators  
- Use transformer-based forecasting models (Informer, TFT)  
- Implement SHAP-based explainability

---

## 📚 References

1. Federal Reserve Economic Data (FRED)  
2. S&P 500 Dataset — Kaggle  
3. Halder, S. (2022). FinBERT-LSTM Stock Prediction  
4. Rawte et al. (2018). Risk Factor Change Analysis  
5. Wu et al. (2021). LSTM with Leading Indicators  
6. Babina et al. (2024). AI, Firm Growth, Innovation  

---

## 🙌 Authors

- **Million Solomon**  
- **Safwan Hasan**

Electrical & Computer Engineering  
Toronto Metropolitan University
