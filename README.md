# 🌾 Crop Yield Prediction and Agricultural Analytics Using Machine Learning

## Overview
This project focuses on analyzing and predicting crop yields across Indian districts using multi-year agricultural and climatic data from the **ICRISAT District-Level Dataset (1990–2015)**.  
By combining **machine learning (ML)**, **deep learning (LSTM)**, and **interactive visualization (Streamlit)**, this study identifies key yield drivers, classifies regional productivity, detects anomalies, and recommends suitable crops for specific regions.

---

## Objectives
- Preprocess and clean multi-year agricultural and climatic data.  
- Explore relationships between crop yield and environmental factors.  
- Predict crop yields using regression and deep learning models.  
- Classify districts by productivity tiers and crop dominance.  
- Detect anomalies and cluster similar agricultural regions.  
- Build a **Streamlit dashboard** for interactive visualization and prediction.

---

## Dataset
**Source:** ICRISAT District-Level Data (India, 1990–2015)  
**Records:** ~3,800  
**Features:** 30+ including  
- Crop Yields: Rice, Chickpea, Groundnut, Sugarcane, Pearl Millet  
- Inputs: Fertilizer consumption, Irrigation ratio  
- Climate: Rainfall, Temperature  
- Identifiers: State, District, Year  

---

## Methodology

### Data Preprocessing
- Handled missing values using state-wise mean and mode imputation.  
- Renamed and standardized column names.  
- Removed irrelevant or duplicate entries.  
- Feature Engineering:  
  - `irrigation_ratio`  
  - `yield_per_fertilizer`  
  - `temperature_c`  
  - `rainfall_mm`  

### Exploratory Data Analysis (EDA)
- Generated heatmaps, regression plots, and pairplots.  
- Identified strong positive correlations between **irrigation**, **fertilizer use**, and **yield**.  
- Top rice-producing states: *West Bengal, Andhra Pradesh, Punjab, Uttar Pradesh*.  
- Found that extreme temperature and rainfall fluctuations reduce yield.

### Model Development
| Model | Type | Purpose | Result |
|:------|:------|:---------|:--------|
| **Linear Regression (OLS)** | Regression | Baseline model for rice yield | R² = 0.15 |
| **Random Forest Regression** | Ensemble | Multi-crop yield prediction | R² = 0.48 |
| **XGBoost Regression** | Ensemble Boosting | Improved yield accuracy | R² = 0.55 |
| **Logistic Regression** | Classification | High vs. Low yield classification | 70% Accuracy |
| **Random Forest Classifier** | Multi-class | District crop dominance classification | 87.8% Accuracy |
| **k-NN / PCA + k-NN** | Classification | Productivity tiers | 67.8% / 60.8% Accuracy |
| **LSTM (Keras)** | Deep Learning | Year-wise yield prediction | Captured temporal trends |

### Clustering & Anomaly Detection
- **K-Means Clustering:** Grouped districts by yield and climate profiles.  
- **Isolation Forest:** Detected outliers caused by abnormal climate or data errors.  

### 📉 Dimensionality Reduction (PCA)
- Reduced multicollinearity between features.  
- Visualized productivity tiers in 2D space.  
- Explained variance ≈ 45% (PC1, PC2).

---

## Results Summary

| Model | Metric | Performance | Key Findings |
|:--|:--|:--|:--|
| Linear Regression | R² = 0.15 | Basic trend captured | Yield ↑ with irrigation & fertilizer |
| Random Forest | R² = 0.48 | Better accuracy | Handles nonlinearity well |
| XGBoost | R² = 0.55 | Best regression model | Most stable and precise predictions |
| Logistic Regression | 70% Accuracy | Binary yield classification | Works well for simple separation |
| Random Forest Classifier | 87.8% Accuracy | Dominant crop detection | Rainfall & irrigation most influential |
| LSTM | High R², Low RMSE | Temporal yield forecasting | Closely follows real trends |

---

## Insights
- **Irrigation ratio** and **fertilizer use** are the strongest predictors of yield.  
- **High temperature** and **rainfall extremes** negatively impact productivity.  
- **Eastern and southern states** outperform in rice yield due to better irrigation.  
- **Ensemble models (RF, XGBoost)** outperform linear methods.  
- **LSTM** effectively captures temporal dependencies for future yield forecasting.

---

## Streamlit Dashboard
An **interactive Streamlit dashboard** was developed for:
- Visualizing yield, rainfall, and irrigation data.
- Comparing model predictions for selected crops and states.
- Displaying **Actual vs Predicted** graphs and **Feature Importance** plots.
- Enabling crop recommendations based on climatic inputs.
