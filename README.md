# Retail Demand Forecasting

## Project Overview

This project analyzes historical retail sales and builds machine-learning models to forecast daily demand. It explores weekly and monthly sales patterns, creates time-based features, and compares a seasonal-naive baseline with Decision Tree and Random Forest models.

## Business Objective

Accurate demand forecasts can help retailers plan inventory, reduce stockouts, and make better replenishment decisions.

## Dataset

- **Source:** [Kaggle Store Item Demand Forecasting Challenge](https://www.kaggle.com/competitions/demand-forecasting-kernels-only/data)
- **Period:** 2013–2017
- **Records:** 913,000
- **Stores:** 10
- **Items:** 50

The raw dataset is not included in this repository. Download `train.csv` from Kaggle and place it in `data/`.

## Data Quality

- No missing values in the original dataset.
- No duplicate rows.
- 500 store-item combinations.
- 1,826 daily records per combination.

## Exploratory Findings

- Average total daily sales differ substantially by weekday.
- Sunday has the highest historical average daily sales; Monday has the lowest.
- Monthly sales show a recurring seasonal pattern, with July having the highest average daily sales in the observed data.

## Modeling

The initial experiment aggregates sales across all stores and items into a daily time series.

Models evaluated:
1. Seven-day seasonal-naive baseline.
2. Decision Tree using the seven-day lag.
3. Random Forest using calendar, lag, and rolling-average features.

A chronological train-test split was used, with the later dates reserved for testing.

## Preliminary Results

| Model | MAE | RMSE | WAPE |
|---|---:|---:|---:|
| Seven-day seasonal naive | 899.81 | 1,876.62 | 3.05% |
| Decision Tree (lag 7 only) | 1,156.49 | 1,971.39 | 3.91% |
| Random Forest | 639.78 | 1,093.93 | 2.17% |

These results are preliminary and reflect a rolling one-day-ahead setup using observed historical sales for lag features. They should be revalidated before being treated as final performance claims.

## Tools and Technologies

- Python
- Pandas and NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Git and GitHub

## Project Structure

- `data/` — local dataset, excluded from version control
- `notebooks/` — exploratory analysis and modeling
- `reports/` — model comparison and feature importance
- `models/` — locally saved model artifacts, excluded from version control

## Future Improvements

- Validate performance using rolling-origin backtesting.
- Compare against seasonal-naive and other time-series forecasting approaches.
- Evaluate forecasts across individual stores and items.
- Investigate forecast errors by season and weekday.
- Document reproducible training and prediction workflows.