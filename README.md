# Windsor, Ontario — Residential House Price Prediction

**Author:** Van Suriyo &nbsp;|&nbsp; **Dataset:** 546 Homes in Windsor, Ontario, Canada &nbsp;|&nbsp; **Source:** [[Kaggle]](https://www.kaggle.com/code/suriyo/windsor-house-prices-prediction)
---

## Overview

This project builds and compares four regression models to predict residential sale prices in Windsor, Ontario using property attributes. The goal is to provide data-driven insight for buyers, sellers, and real estate agents.

**Stakeholders who benefit from this analysis:**
- **Buyers** — understand what features drive price premiums
- **Sellers** — identify which improvements yield the highest return
- **Real estate agents** — set data-backed listing prices with confidence

---

## Project Structure

```
windsor-house-price-prediction/
│
├── windsor-house-prices-prediction.ipynb   # Main notebook
├── HousePrices.csv                         # Datasets
├── requirements.txt                        # Python dependencies
└── README.md
```

---

## Dataset

| Property | Detail |
|---|---|
| Source | Kaggle — House Prices in the City of Windsor, Canada |
| Rows | 546 transactions |
| Features | 12 (lot size, bedrooms, bathrooms, stories, garage, amenities, etc) |
| Target | Sale price (CAD) |
| Price Range | $25,000 — $190,000 |

---

## Workflow

1. **Data Loading & Cleaning** — null handling, binary encoding of yes/no features
2. **Exploratory Data Analysis** — price distributions, correlation heatmap, amenity impact analysis
3. **Feature Engineering** — 5 engineered features including lotsize_log, total_rooms, bath_bed_ratio, stories_x_bedrooms, and garage_x_aircon
4. **Model Building** — four regression models trained on a 70/30 train/test split
5. **Hyperparameter Tuning** — GridSearchCV with Pipeline for Ridge and Random Forest
6. **Evaluation** — R², MAE, and RMSE across all models

---

## Models Used

| Model | Type |
|---|---|
| Linear Regression | Linear |
| Ridge Regression | Linear (regularized) |
| Random Forest | Tree-based (ensemble) |
| Gradient Boosting | Tree-based (boosting) |
| Ridge (GridSearchCV) | Linear + hypertuned |
| Random Forest (GridSearchCV) | Tree-based + hypertuned |

---

## Key Results

> Best Model: **Ridge Regression (GridSearchCV)**

| Metric | Score |
|---|---|
| R² | 0.7132 |
| MAE | $11,432 |
| RMSE | $15,629 |

Linear models outperformed tree-based models, confirming that Windsor house pricing follows a **linear relationship** with its features.

---

## Key Findings

1. **Lot size** is the single strongest predictor of price — by a large margin
2. **Bathrooms matter more than bedrooms** — a higher bath/bed ratio is a proxy for higher-end homes
3. **Garage and Air Conditioning** command a clear price premium in Windsor's climate
4. **Linear models outperform tree-based models**, suggesting the pricing signal is mostly linear
5. The ~29% unexplained variance is likely due to missing features such as property age, interior condition, school district, and neighbourhood effects

---

## Potential Improvements

- Expand dataset size — the small sample (546) likely caps model performance
- Add missing key features: property age, interior/exterior condition, school district, neighbourhood safety scores
- Experiment with additional models (XGBoost, SVR)
- Deploy as an interactive price estimator web app

---

## How to Run

---

1. **Clone the repository**
```bash
git clone https://github.com/suriyo/windsor-house-price-prediction.git
cd windsor-house-price-prediction
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Download the dataset** from [Kaggle](https://www.kaggle.com/datasets/deepikakoche/house-prices-in-the-city-of-windsor-canada) and place the CSV in the project folder

4. **Launch Jupyter and open the notebook**
```bash
jupyter notebook windsor-house-prices-prediction.ipynb
```

---

## Requirements

```
import numpy as np
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Machine Learning Libraries
from sklearn.preprocessing import StandardScaler
from sklearn import preprocessing, metrics
from sklearn.linear_model import LinearRegression, Ridge
from sklearn.ensemble import RandomForestRegressor, GradientBoostingRegressor
from sklearn.model_selection import train_test_split, GridSearchCV
from sklearn.pipeline import Pipeline
```
