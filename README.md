# Sustainable Taxi Pricing using Machine Learning and Big Data
### An ML-driven framework for identifying environmentally sustainable taxi pricing strategies using NYC Taxi & Limousine Commission trip data

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Gradient%20Boosting-success)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

## Overview

This project investigates how machine learning and spatio-temporal analytics can be used to design taxi pricing strategies that improve revenue while simultaneously reducing vehicle miles travelled (VMT) and carbon emissions.

Using the **NYC Taxi & Limousine Commission (TLC) 2025 Yellow Taxi dataset**, this research develops an end-to-end analytical pipeline combining:

- Exploratory Data Analysis (EDA)
- Feature Engineering
- Machine Learning Demand Prediction
- Fare Scenario Simulation
- Carbon Emission Estimation
- Spatial Optimisation

The project forms the basis of my MSc dissertation in Data Science.

---

## Research Question

> **How can spatio-temporal taxi trip data be analysed using machine learning and big data techniques to identify pricing strategies that maintain revenue while supporting sustainable urban mobility and reducing carbon emissions?**

---

# Objectives

- Explore spatial and temporal demand patterns across NYC
- Build machine learning models for taxi demand prediction
- Evaluate fare elasticity under different pricing scenarios
- Estimate changes in revenue, Vehicle Miles Travelled (VMT), and CO₂ emissions
- Develop a geographically targeted pricing strategy

---

# Dataset

**Source**

NYC Taxi & Limousine Commission (TLC)

The dataset contains approximately **22,700 Yellow Taxi trips** including:

- Pickup & drop-off timestamps
- Pickup & drop-off locations
- Fare amount
- Trip distance
- Total payment
- Passenger count

After cleaning:

- **22,535 trips**
- **261 taxi zones**

---

# Project Workflow

```
Raw TLC Data
      │
      ▼
Data Cleaning
      │
      ▼
Feature Engineering
      │
      ▼
Exploratory Data Analysis
      │
      ▼
Zone-Hour Aggregation
      │
      ▼
Machine Learning Models
      │
      ▼
Best Model Selection (GBM)
      │
      ▼
Fare Scenario Simulation
      │
      ▼
Spatial Optimisation
      │
      ▼
Policy Recommendations
```

---

# Feature Engineering

The following features were created:

- Hour of day
- Day of week
- Month
- Peak hour indicator
- Weekend indicator
- Trip duration
- Fare per mile
- Vehicle Miles Travelled (VMT)
- Estimated CO₂ emissions

CO₂ emissions were estimated using the **US EPA emission factor**

> **404 g CO₂ per vehicle mile**

---

# Machine Learning Models

Three supervised learning models were evaluated.

| Model | Purpose |
|--------|----------|
| Linear Regression | Baseline |
| Random Forest | Ensemble |
| Gradient Boosting | Final model |

Evaluation metrics:

- R²
- RMSE

### Best Performing Model

**Gradient Boosting Regressor**

Performance:

- **R² = 0.38**

Although modest, this is consistent with published taxi demand forecasting literature using comparable features.

---

# Fare Simulation

Rather than predicting future fares, this project simulates fare changes using an elasticity-based demand model.

Nine pricing scenarios were evaluated:

| Fare Change |
|-------------|
| -20% |
| -15% |
| -10% |
| -5% |
| Current |
| +5% |
| +10% |
| +15% |
| +20% |

Demand responses were calculated using a literature-supported elasticity:

> **Price Elasticity = -0.4**

For every scenario the project estimates:

- Revenue
- Demand
- Vehicle Miles Travelled
- CO₂ emissions

---

# Regional Optimisation

Taxi zones were classified according to VMT intensity.

Instead of increasing fares city-wide, the project evaluates:

- blanket fare increases
- targeted fare increases in high-VMT zones

Airport zones (JFK and LaGuardia) were identified as the most efficient locations for targeted pricing.

---

# Key Findings

## 1. Fare increases can improve both revenue and sustainability

A moderate fare increase produced:

- higher revenue
- lower VMT
- lower CO₂ emissions

This demonstrates a **"double dividend"** where commercial and environmental objectives align.

---

## 2. Airport trips are the largest emission contributors

JFK and LaGuardia generated:

- the highest VMT
- relatively low fare per mile
- the greatest opportunity for targeted pricing

---

## 3. Targeted pricing performs almost as well as blanket pricing

Applying a **10% fare increase only in high-VMT zones** achieved:

- **+3.1% revenue**
- **−3.4% CO₂ emissions**

while affecting only a small proportion of taxi zones.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

---

# Repository Structure

```
├── data/
│   ├── raw/
│   ├── cleaned/
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_ml_models.ipynb
│   ├── 05_fare_simulation.ipynb
│
├── figures/
│
├── outputs/
│
├── dissertation/
│
├── requirements.txt
│
└── README.md
```

---

# Results

| Strategy | Revenue Change | CO₂ Change |
|------------|---------------|-------------|
| +5% Blanket | +1.9% | -2.0% |
| +10% Blanket | +3.7% | -4.0% |
| +10% Targeted | +3.1% | -3.4% |

---

# Academic Contributions

This project contributes by:

- Integrating machine learning with pricing policy simulation
- Introducing VMT intensity as a pricing criterion
- Linking fare strategy directly to environmental outcomes
- Demonstrating practical policy recommendations using real-world administrative data

---

# Future Improvements

Potential extensions include:

- Zone-specific elasticity estimation
- Weather and event integration
- Ride-hailing (Uber/Lyft) comparison
- Multi-year trend analysis
- GPS-based deadheading estimation
- SHAP explainability for model interpretation

---

# References

- NYC Taxi & Limousine Commission
- US Environmental Protection Agency (EPA)
- Scikit-learn Documentation
- Relevant academic literature cited throughout the dissertation

