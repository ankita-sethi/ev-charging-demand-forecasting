# EV Charging Demand Forecasting (Kaggle Competition)

Forecasting Hourly Demand for EV Charging

---

## Overview
This project focuses on forecasting **hourly electric vehicle (EV) charging demand** using historical charging session data. The goal was to build an accurate time series and machine learning based model that could predict hourly energy demand for a future one month period.

The work was developed as part of a **class wide Kaggle competition**, where teams trained models on eleven months of data and submitted forecasts for a held out test month.

The final solution ranked first on the class Kaggle leaderboard.

---

## Problem Statement
Electric vehicle adoption is growing rapidly, making accurate demand forecasting critical for grid planning, infrastructure optimization, and energy management.

Given historical EV charging session data:
- Train models on **11 months** of data
- Forecast **hourly charging demand** for a **1 month future window**
- Minimize **Mean Squared Error (MSE)** on Kaggle submissions

---

## Dataset
- Source: Kaggle EV Charging Dataset
- Training period: January 2020 to December 2020 (11 months)
- Target variable: Hourly `kWhDelivered`
- Key features:
  - connectionTime
  - disconnectTime
  - doneChargingTime
  - kWhDelivered
  - station, site, and session metadata

#Note on Notebook Rendering

This notebook contains interactive outputs that may not render correctly on GitHub.  
Please clone the repository and run the notebook locally to view all plots and results.

The raw session level data was transformed into an **hourly demand time series**.

---

## Data Preprocessing
Key preprocessing steps included:
- Handling missing values by converting NaNs to zero to avoid data loss
- Identifying and analyzing outliers in charging sessions
- Converting session level data into hourly demand using proportional energy distribution
- Filling missing hourly timestamps with zero demand
- Extracting time based features such as:
  - Hour of day
  - Day of week
  - Day of month
  - Month
  - Quarter
  - Day of year

This ensured a clean and continuous hourly time series suitable for modeling.

---

## Models Explored
Multiple models were evaluated to identify the best approach for forecasting hourly EV demand:

- Linear Regression (baseline)
- LightGBM
- TPOT AutoML
  - Selected RandomForestRegressor as the best pipeline

Each model was evaluated using Mean Squared Error and visual diagnostics comparing actual vs predicted demand.

---

## Final Model Selection
After experimentation and evaluation:
- **TPOT Regressor with RandomForest** was selected as the final model
- Achieved strong generalization on the Kaggle test set
- Final Kaggle score: **MSE ≈ 3.13**

This model balanced accuracy and robustness better than simpler baselines.

---

## Results
- Linear Regression significantly underfit the data
- LightGBM captured non linear patterns with improved accuracy
- TPOT AutoML produced the best performing model
- The final model ranked **1st in the class Kaggle leaderboard**, based on evaluation metrics

This result validated both the preprocessing strategy and model selection approach.

---

## Key Takeaways
- Careful feature engineering is critical for time series forecasting
- Tree based models outperform linear baselines for EV demand prediction
- AutoML can effectively identify strong model pipelines
- Kaggle style validation encourages robust, production oriented modeling

---

## Tech Stack
- Python
- Pandas, NumPy
- Scikit learn
- LightGBM
- TPOT (AutoML)
- Matplotlib

---

## Conclusion
This project demonstrates an end to end workflow for **real world time series forecasting**, from raw data processing to model evaluation and competition submission. The results highlight the importance of thoughtful preprocessing, model experimentation, and evaluation when working with energy demand data.

---

## References
- Kaggle EV Charging Dataset
- TPOT AutoML Documentation
- Scikit learn
