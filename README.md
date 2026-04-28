# 🚕 Ride-Hailing Fare Optimization Analytics

A data-driven analytics project focused on understanding ride-hailing demand patterns, improving fare prediction accuracy, and simulating revenue optimization strategies using geospatial and temporal data.

---

## 📌 Project Overview

This project analyzes Uber ride data to uncover patterns in customer demand, pricing behavior, and spatial distribution of trips. It combines **data cleaning, geospatial feature engineering, statistical validation, and regression modeling** to build a foundation for fare prediction and dynamic pricing simulation.

The goal is not only to predict fares but also to explore how pricing strategies can be optimized based on demand behavior across time and location.

---

## 🎯 Objectives

- Clean and validate large-scale ride-hailing data (200,000+ records)
- Engineer meaningful spatial and temporal features
- Identify high-demand geographic zones ("hotspots")
- Build predictive models for fare estimation
- Simulate pricing strategies based on demand patterns
- Analyze revenue optimization opportunities

---

## 🧹 Data Cleaning & Preprocessing

Key steps performed:

- Removed invalid and missing records
- Fixed swapped latitude and longitude values
- Filtered data within New York City boundaries
- Removed outliers:
  - Invalid passenger counts
  - Zero or near-zero trip distances
  - Unrealistic fare values below base threshold

---

## 🗺️ Feature Engineering

To improve model performance, several features were created:

### 🌍 Geospatial Features
- Geodesic distance using `geopy`
- Grid-based clustering (1km and 7.5km zones)
- Pickup location density mapping

### ⏰ Temporal Features
- Hour, day, month, year extraction
- Hour grouping (e.g., rush hours, late night)
- AM/PM segmentation

### 🚖 Trip Segmentation
- Short trips vs long trips classification

---

## 📊 Exploratory Data Analysis

- Identified peak demand periods (18:00 – 00:00)
- Discovered high-density pickup zones in NYC
- Correlation analysis between distance and fare
- Demand variation across weekdays vs weekends

---

## 📈 Modeling Approach

- **Model Used:** Linear Regression (`scikit-learn`)
- **Validation:** Train-test split evaluation
- **Statistical Check:** Variance Inflation Factor (VIF) for multicollinearity detection

### 🎯 Target Variable
- `fare_amount`

### 🔑 Key Predictors
- Trip distance
- Time of day
- Geographic location (grid zones)

---

## 💰 Prescriptive Pricing Strategy

A rule-based pricing simulation was developed to model demand-based fare adjustments.

### Pricing Logic:
- **High-demand periods**
  - Sunday (all day)
  - Monday PM, Tuesday PM
  - Friday AM, Saturday AM
  - → Applied higher fare multipliers

- **Peak surge window**
  - Saturday PM (highest demand period)

- **Standard pricing**
  - Wednesday & Thursday (baseline demand)

👉 This simulates real-world surge pricing behavior used in ride-hailing platforms.

---

## 📦 Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- Statsmodels
- Geopy
- Matplotlib, Seaborn
- Gdown

---

## 📌 Key Insights

- Trip distance is the strongest predictor of fare amount
- Demand is heavily concentrated in specific NYC zones
- Clear temporal patterns exist in ride demand
- Peak hours significantly impact pricing opportunities
- Pricing optimization can increase revenue through demand-aware multipliers

---

## 🚀 Future Improvements

- Deploy ML model as API (Flask / FastAPI)
- Use advanced models (XGBoost / CatBoost)
- Integrate real-time surge pricing simulation
- Add clustering models for dynamic zone detection
