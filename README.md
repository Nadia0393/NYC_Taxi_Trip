# 🚖 NYC Taxi Trip Duration Prediction using PySpark ML

## 📌 Project Overview

Accurately estimating taxi trip duration is valuable for both customers and taxi service providers. In this project, I built an end-to-end machine learning pipeline using PySpark to predict NYC taxi trip duration based on trip details such as pickup/dropoff locations, passenger count, pickup time, and engineered features.

The project demonstrates data cleaning, feature engineering, model training, evaluation, and interpretation using Apache Spark ML.

---

## 🎯 Business Problem

Given information about a taxi trip at the time of pickup, predict the total trip duration.

This helps:

- Improve ETA predictions
- Enhance customer experience
- Optimize fleet management
- Support ride pricing and planning

---

## 📂 Dataset

NYC Taxi Trip Duration Dataset

Target Variable:

- **trip_duration (seconds)**

Features:

- Vendor ID
- Pickup & Dropoff Coordinates
- Pickup Datetime
- Passenger Count

Dataset Size:

- **1,458,644 records**

---

## 🛠 Technologies Used

- Python
- PySpark
- Spark ML
- Databricks Community Edition
- Git
- GitHub

---

## 🔍 Exploratory Data Analysis

Performed:

- Schema inspection
- Missing value analysis
- Summary statistics
- Outlier detection
- Trip duration analysis

---

## ⚙️ Feature Engineering

Created the following features:

### Pickup Hour

Extracted hour from pickup datetime.

Purpose:

Traffic patterns vary throughout the day.

---

### Weekend Indicator

Identifies whether the trip occurred on Saturday or Sunday.

---

### Rush Hour Indicator

Morning:
8 AM – 10 AM

Evening:
4 PM – 6 PM

---

### Trip Distance (Haversine Formula)

Engineered a new feature by calculating the great-circle distance between pickup and dropoff coordinates.

This became the most important feature in the model.

---

## 🧹 Data Cleaning

During EDA, I identified unrealistic trips.

Examples included:

- Trips exceeding 1000 km
- Trips lasting several days

Since these represented only **0.15%** of the dataset, they were removed.

Cleaning Rules:

- Trip Distance ≤ 50 km
- Trip Duration ≤ 7200 seconds

---

## 🤖 Machine Learning Pipeline

Raw Data
↓

Feature Engineering
↓

Data Cleaning
↓

StringIndexer

↓

OneHotEncoder

↓

VectorAssembler

↓

Random Forest Regressor

↓

Prediction

↓

Evaluation

---

## 📊 Model Performance

| Metric | Value |
|---------|--------|
| RMSE | 417.62 sec |
| MAE | 305.56 sec |
| R² Score | 0.589 |

---
## Impact

- Processed 1.45 million NYC taxi trips using PySpark.
- Engineered a Haversine distance feature that became the most influential predictor (62.5% importance).
- Improved prediction performance by removing only 0.15% of unrealistic records.
- Built an end-to-end Spark ML pipeline from data ingestion through model evaluation

---
## ⭐ Feature Importance

| Feature | Importance |
|---------|-----------|
| Trip Distance | 62.48% |
| Pickup Longitude | 10.31% |
| Pickup Latitude | 5.48% |
| Dropoff Longitude | 6.46% |
| Dropoff Latitude | 6.32% |
| Pickup Hour | 6.69% |
| Weekend | 1.42% |
| Rush Hour | 0.79% |
| Passenger Count | <0.1% |
| Vendor | <0.1% |

---

## 📈 Key Findings

- Trip distance was the strongest predictor of trip duration.
- Removing unrealistic GPS records significantly improved model quality.
- Pickup and dropoff coordinates remained useful even after adding distance.
- Time-based features contributed modestly to prediction accuracy.

---

## 🚀 Future Improvements

- Hyperparameter tuning using CrossValidator
- Gradient Boosted Trees
- Weather integration
- Holiday information
- Traffic congestion data
- XGBoost implementation

---

## 👨‍💻 Author

**Nadhiya Ganesan**

Data Engineer | PySpark | SQL | Azure | Machine Learning
