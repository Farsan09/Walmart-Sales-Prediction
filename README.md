# Walmart Store Sales Forecasting
📌 Project Overview
This project predicts the weekly sales for 45 Walmart stores across 99 departments. The challenge lies in accounting for significant sales spikes during holiday weeks (Super Bowl, Labor Day, Thanksgiving, and Christmas) and adjusting for external factors like CPI, Fuel Prices, and Unemployment rates.

### Goal: Minimize the Weighted Mean Absolute Error (WMAE), where holiday errors are weighted 5x more heavily than non-holiday errors.
## 📊 The Data
The dataset consists of three primary sources:

Stores: Metadata about the 45 stores (Type and Size).

Features: External data (Temperature, Fuel Price, Markdowns, CPI, Unemployment).

Sales: Historical weekly sales from 2010-02-05 to 2012-11-01.

## 🛠️ Feature Engineering (The "Secret Sauce")
To improve the model from a baseline score of ~6300 down to [Insert Your Best Score Here], the following features were engineered:

52-Week Lag: Captures yearly seasonality by looking at sales from the same week in the previous year.

Days until Christmas: A proximity counter to capture the "ramp-up" period before the holiday peak.

Holiday Flags: Custom binary flags for the weeks leading up to Black Friday and Christmas.

Markdown Imputation: Handled missing values by treating NaN as 0 (indicating no active promotion).

## 🚀 Model Architecture
I utilized XGBoost (Extreme Gradient Boosting) due to its ability to handle non-linear relationships and missing data effectively.

Validation Strategy: Used TimeSeriesSplit (Expanding Window) to prevent data leakage and ensure the model generalizes to future dates.

Loss Function: Optimized for WMAE to prioritize accuracy during high-stakes holiday periods.

## Top Predictive Features:
Sales_Last_Year (52-Week Lag)

Dept (Department ID)

Week of Year

Days_Until_Christmas

## 📂 Repository Structure
├── notebooks/          # Exploratory Data Analysis (EDA) & Model Training
├── submissions/        # Kaggle-ready CSV outputs
└── README.md

The data can be found here: https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/data

## ⚙️ Installation & Usage
  1.  Clone the repo:

      git clone https://github.com/Farsan09/walmart-sales-Prediction.git

  3.  Install dependencies:

      pip install -r requirements.txt


