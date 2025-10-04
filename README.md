# Bitcoin Price Prediction
This project focuses on forecasting Bitcoin closing prices using historical market data. It combines time series analysis with machine learning techniques, culminating in a finely tuned Gradient Boosting Regressor model that delivers high predictive accuracy.

# Project Workflow
1. Data Preparation: Handle missing values, converted ‘Date’ column to datetime and set as index, and resampled data to weekly and monthly frequencies for trend analysis.
2. Exploratory Data Analysis (EDA): Identify patterns and relationships in the dataset.
3. Feature Engineering: Created 7-day and 30-day moving averages of 'Close' price, calculated daily percentage changes and 7-day rolling standard deviation, and dropped rows with missing values from rolling calculations.
4. Data Splitting: Chronologically spliting data into 80% training and 20% testing sets, defining 'Close' price as the target variable.
5. Model Training: Trained five models (i.e., ARIMA, SARIMA, Decision Tree Regressor, Random Forest Regressor, and Gradient Boosting Regressor).
6. Model Evaluation: Compare model performance metrics.
7. Model Selection: Select the model with the highest accuracy.
8. Hyperparameter Tuning: Bayesian Optimization used to optimize Gradient boosting Regressor

# Dataset Description
The dataset includes daily Bitcoin market data:
1. Open: Price of Bitcoin at the start of the trading day.
2. High: Highest price Bitcoin reached during the trading day.
3. Low: Lowest price Bitcoin dropped to during the trading day.
4. Close: Final price of Bitcoin at the end of the trading day.
5. Adj Close: Closing price adjusted for splits and dividends.
6. Volume: Total number of Bitcoin units traded during the day.
7. Moving Averages: Smmothed averages of the closing price over 7 or 30 days to capture trends.
8. Percentage Changes: Daily percent change in closing to reflect volatility.
9. 7-Day Rolling Standard Deviation: Weekly measure of price fluctuation to quantify volatility.

# Exploratory Data Analysis (EDA)
The EDA phase involves:
1. Visualized price and volume trends over time.
2. Applied seasonal decomposition to detect patterns.
3. Identified and capped outliers using the IQR method.
4. Correlation heatmap revealed strong relationships among price features.

# Model Selection and Evaluation
Evaluated multiple models using RMSE:
1. ARIMA (1,1,1): RMSE = 20,745.25
2. SARIMA (0,1,1)x(0,1,1,7): RMSE = 17,943.01
3. Decision Tree Regressor: RMSE = 476.67
4. Random Forest Regressor: RMSE = 611.81
5. Gradient Boosting Regressor: RMSE = 420.85

Gradient Boosting Regressor was selected due to its superior RMSE performance. Bayesian Optimization further enhanced its accuracy. A separate script, model_selection.ipynb, automates model comparison and selection.

# Model Performance Dashboard
Key Metrics:
1. RMSE: 349.8
2. MAE: 176.5
3. Cross-validation RMSE: 11,708.97

Visual Insights:
1. Overlay plot of actual vs predicted prices (2021-2024) showed strong alignment.
2. Scatter plot revealed tight clusteringalong diagonal with few outliers.
3. Residuals are balanced and centered near zero.
4. Error distribution is normal-like with few extreme deviations.
