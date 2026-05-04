# 🏠 Windsor, Ontario — Residential House Price Prediction

**Author:** Van Suriyo &nbsp;|&nbsp; **Dataset:** 546 Homes in Windsor, Ontario, Canada &nbsp;|&nbsp; **Source:** [Kaggle](https://www.kaggle.com/datasets/zahrayazdani/house-prices-in-the-city-of-windsor-canada)

---

## 📋 Overview

This project builds and compares four regression models to predict residential sale prices in Windsor, Ontario using property attributes. The goal is to provide data-driven insight for buyers, sellers, and real estate agents operating in mid-sized Canadian housing markets.

**Stakeholders who benefit from this analysis:**
- 🏡 **Buyers** — understand what features drive price premiums
- 💰 **Sellers** — identify which improvements yield the highest return
- 📊 **Real estate agents** — set data-backed listing prices with confidence

---

## 📁 Project Structure

```
windsor-house-price-prediction/
│
├── windsor-house-prices-prediction.ipynb   # Main notebook
├── requirements.txt                        # Python dependencies
└── README.md
```

---

## 📦 Dataset

| Property | Detail |
|---|---|
| Source | Kaggle — House Prices in the City of Windsor, Canada |
| Rows | 546 transactions |
| Features | 12 (lot size, bedrooms, bathrooms, stories, garage, amenities) |
| Target | Sale price (USD) |
| Price Range | $25,000 — $190,000 |

---

## 🔍 Workflow

1. **Data Loading & Cleaning** — null handling, binary encoding of yes/no features
2. **Exploratory Data Analysis** — price distributions, correlation heatmap, amenity impact analysis
3. **Feature Engineering** — 5 engineered features including `lotsize_log`, `total_rooms`, `bath_bed_ratio`, `stories_x_bedrooms`, and `garage_x_aircon`
4. **Model Building** — four regression models trained on a 70/30 train/test split
5. **Hyperparameter Tuning** — GridSearchCV with Pipeline for Ridge and Random Forest
6. **Evaluation** — R², MAE, and RMSE across all models

---

## 🤖 Models Used

| Model | Type |
|---|---|
| Linear Regression | Linear |
| Ridge Regression | Linear (regularized) |
| Random Forest | Tree-based (ensemble) |
| Gradient Boosting | Tree-based (boosting) |
| Ridge (GridSearchCV) | Linear + hypertuned |
| Random Forest (GridSearchCV) | Tree-based + hypertuned |

---

## 📈 Key Results

> Best Model: **Ridge Regression (GridSearchCV)**

| Metric | Score |
|---|---|
| R² | ~0.71 |
| MAE | ~$10,000s |
| RMSE | Lower is better |

Linear models outperformed tree-based models, confirming that Windsor house pricing follows a largely **linear relationship** with its features.

---

## 💡 Key Findings

1. **Lot size** is the single strongest predictor of price — by a large margin
2. **Bathrooms matter more than bedrooms** — a higher bath/bed ratio is a proxy for higher-end homes
3. **Garage and Air Conditioning** command a clear price premium in Windsor's climate
4. **Linear models outperform tree-based models**, suggesting the pricing signal is mostly linear
5. The ~29% unexplained variance is likely due to missing features such as property age, interior condition, school district, and neighbourhood effects

---

## ⚙️ How to Run

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/windsor-house-price-prediction.git
cd windsor-house-price-prediction
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Download the dataset** from [Kaggle](https://www.kaggle.com/datasets/zahrayazdani/house-prices-in-the-city-of-windsor-canada) and place the CSV in the project folder

4. **Launch Jupyter and open the notebook**
```bash
jupyter notebook windsor-house-prices-prediction.ipynb
```

---

## 🛠️ Requirements

```
numpy
pandas
seaborn
matplotlib
scikit-learn
```

---

## 🚀 Potential Improvements

- Expand dataset size — the small sample (546) likely caps model performance
- Add missing key features: property age, interior/exterior condition, school district, neighbourhood safety scores
- Experiment with additional models (XGBoost, SVR)
- Deploy as an interactive price estimator web app
