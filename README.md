# Sunspot Forecasting with Facebook Prophet

## Overview
This project leverages Facebook Prophet to forecast sunspot activity using three datasets: **daily**, **monthly**, and **yearly**. The goal is to analyze sunspot trends and improve prediction accuracy by applying custom seasonalities and tuning the model's hyperparameters.

## Dataset
The datasets used in this project provide sunspot data at different time resolutions:

- **Daily Data**: Contains fine-grained sunspot counts per day with additional statistical columns.
  - Columns:
    - `Year`, `Month`, `Day`: Gregorian calendar date.
    - `Date in fraction of year`: Fraction of the year.
    - `Sunspot count`: Daily total sunspot number (missing values are represented as `-1`).
    - `Std Dev`: Standard deviation of sunspot numbers from individual stations.
    - `Number of observations`: Count of observations used for daily computation.
    - `Definitive/provisional indicator`: Indicates if the data is provisional (`*` symbol).
  
- **Monthly Data**: Aggregated data showing sunspot activity trends at a monthly level.
  - Columns:
    - `Year`, `Month`: Gregorian calendar date.
    - `Date in fraction of year`: Middle of the month in fractional year.
    - `Monthly mean sunspot number`: Average sunspot number for the month.
    - `Std Dev`: Monthly mean standard deviation from stations.
    - `Number of observations`: Count of observations used for monthly mean.
    - `Definitive/provisional indicator`: Indicates provisional values (`*` symbol).

- **Yearly Data**: High-level trends showing sunspot activity on a yearly basis.
  - Columns:
    - `Year`: Gregorian calendar year (mid-year date).
    - `Yearly mean sunspot number`: Average sunspot number for the year.
    - `Std Dev`: Yearly mean standard deviation.
    - `Number of observations`: Count of observations used for yearly mean.
    - `Definitive/provisional indicator`: Indicates provisional yearly values.

Note: The `ds` column (date) and `y` column (sunspot count) were used for model training, while other columns provided additional context for dataset interpretation.

## Approach
- Used **Facebook Prophet** for forecasting with both **linear** and **logistic** growth modes, depending on the dataset.
- Applied custom seasonalities for each dataset (daily, monthly, yearly) to capture unique patterns.
- Hyperparameters such as `changepoint_prior_scale`, `seasonality_prior_scale`, and Fourier orders were optimized.
- Performance evaluation was done using the following metrics:
  - **MAE**: Mean Absolute Error
  - **RMSE**: Root Mean Squared Error
  - **MAPE**: Mean Absolute Percentage Error
  - **R²**: R-squared value for model goodness

## Results

### Daily Data
- **MAE**: 56.73
- **MSE**: 5226.04
- **RMSE**: 72.29

### Monthly Data
- **RMSE**: 62.71
- **MAE**: 51.78
- **R²**: 0.181

### Yearly Data
- **MAE**: 44.70
- **RMSE**: 54.85
- **MAPE**: 66.22%
- **R²**: 0.495

## Key Features
- **Custom Seasonalities**: Seasonal components tailored to daily, monthly, and yearly data.
- **Hyperparameter Tuning**: Optimized Prophet parameters to enhance prediction accuracy.
- **Visualization**: Data trends and components visualized for better understanding of sunspot activity.

## Conclusion
This project demonstrated how Facebook Prophet can effectively model sunspot activity across multiple time resolutions. While the yearly data showed the best fit with higher R² values, the daily and monthly datasets exhibited more noise, requiring further parameter adjustments for better prediction accuracy.

## Future Improvements
- **External Regressors**: Incorporating solar cycle data or other external factors to improve forecasting.
- **Hyperparameter Optimization**: Using automated methods like grid or Bayesian search for finer model tuning.
- **Alternative Models**: Comparing Prophet with other models, such as LSTM or ARIMA, to check for improvements in accuracy.

