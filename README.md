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
<img width="793" height="1316" alt="image" src="https://github.com/user-attachments/assets/0b1b54f3-11fb-44f0-becc-d5f5f8555010" />

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
├── requirements.txt
│
└── README.md
```
## Exploratory Data Analysis

### Hourly Taxi Demand

<img width="549" height="411" alt="image" src="https://github.com/user-attachments/assets/f6e6f3e2-0c0b-4ad0-8e2f-ef3cf1aa74ac" />

The demand shows a clear bimodal commuting pattern with morning and evening peaks.

<img width="566" height="436" alt="image" src="https://github.com/user-attachments/assets/0316185d-7599-4ea6-b981-336bff07a2b1" />
<img width="473" height="345" alt="image" src="https://github.com/user-attachments/assets/4cce0e97-34a1-48b1-8b84-6c736dc98b0f" />
<img width="450" height="317" alt="image" src="https://github.com/user-attachments/assets/2582cec8-6a45-4bd2-ab42-2deb5e6b6b3a" />
<img width="523" height="377" alt="image" src="https://github.com/user-attachments/assets/401f7912-be0c-4237-be3a-dfe3a72afa79" />

---

### Spatial Demand Distribution

<img width="706" height="485" alt="image" src="https://github.com/user-attachments/assets/5a2b2ca2-c5de-465d-9b3c-eb8581e9c37f" />

Trips are concentrated within Manhattan, while airport zones exhibit significantly longer journeys.

## Machine Learning

### Feature Importance

<img width="564" height="407" alt="image" src="https://github.com/user-attachments/assets/ee0612eb-65f6-45a3-9be8-29273197a585" />

Average fare was identified as the strongest predictor of zone-level demand.

### Predicted vs Actual Demand
<img width="837" height="596" alt="image" src="https://github.com/user-attachments/assets/2aed54fd-f9b5-40cc-9b8d-5acf8d852d81" />

## Fare Scenario Simulation

<img width="832" height="584" alt="image" src="https://github.com/user-attachments/assets/d8032a8a-8403-4650-94b1-0e54f17053ae" />

<img width="817" height="579" alt="image" src="https://github.com/user-attachments/assets/5c016214-378f-4808-9811-3fbce859781e" />

## Regional Pricing Strategy

<img width="761" height="550" alt="image" src="https://github.com/user-attachments/assets/bc6d95fb-c76e-40a2-8980-535ac26fd4ad" />


## Revenue vs CO₂

<img width="956" height="401" alt="image" src="https://github.com/user-attachments/assets/4c459c3c-6d89-4b0d-b3b7-d4eb81d2802f" />

The targeted pricing strategy achieved nearly the same emissions reduction as a blanket fare increase while affecting far fewer taxi zones.

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

