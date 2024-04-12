# Cryptocurrency Trading Analysis and Prediction

## Overview
This repository contains analysis, implementation, and prediction models applied to cryptocurrency market data. It includes exploratory data analysis (EDA), a turtle trading strategy implementation, and a random forest regressor model

## Dataset
The dataset (data.csv) comprises 935 entries with 20 columns. Here's a brief description of the columns:
- datetime: Date and time of the observation.
- open, high, low, close: Cryptocurrency price metrics.
- volume: Trading volume.
- reserve: Reserve data.
- funding_rates: Funding rates.
- mvrv, nrpl, nupl: Cryptocurrency market indicators.
- stock_to_flow_reversion, sth_sopr, RSI: Additional market indicators.
- signal: Trading signal (buy/none).
- 9_ema, 21_ema, 50_ema, 200_ema: Exponential moving averages.
- Fear_and_Greed_Index: Market sentiment indicator.

## Exploratory Data Analysis (EDA)
- The EDA notebook (EDA.ipynb) explores the cryptocurrency market data using Python libraries such as pandas, matplotlib, seaborn, and statsmodels. The following key steps are performed:
### Data Type and Missing Values
- All columns have appropriate data types.
- There are no missing values in the dataset.
### Descriptive Statistics
- The descriptive statistics provide insights into the distribution of numerical features.
- Cryptocurrency prices have a wide range with significant standard deviations.
- Other features like volume, reserve, and market indicators also show variability.
### Data Visualization
- A Line plot of cryptocurrency closing prices over time.
- Seasonal decomposition suggests potential seasonal patterns.
### Stationarity Check
- Augmented Dickey-Fuller (ADF) test is used to check for stationarity of the closing prices.
- It was observerd that the First and second differences of closing prices are stationary, indicating a potential for time-series modeling.
### Correlation Analysis
- Relationships between features.
- Cryptocurrency prices exhibit strong correlations with market indicators like MVRV, stock-to-flow reversion, and others.
### Conclusion
- Valuable insights into cryptocurrency market dynamics.
- Foundation for further analysis and model development.

---

## Cryptocurrency Turtle Trading Strategy

### Overview
This turtle trading notebook(Turtletrading.ipynb) contains the implementation of a turtle trading strategy applied to cryptocurrency market data. The turtle trading strategy is a trend-following strategy that aims to capture significant price movements in the market. The strategy is based on rules derived from the famous Turtle Trading experiment conducted by Richard Dennis and William Eckhardt in the 1980s.

### Strategy Implementation
- Calculating Donchian Channels: Donchian channels are used to identify potential breakout points in the market. Upper and lower channels are calculated based on the highest high and lowest low prices over a specified period.
- Calculating True Range: True range is calculated to measure the volatility of the market. It considers the maximum of the current high minus low, absolute high minus previous close, and absolute low minus previous close.
- Calculating Average True Range (ATR): Average true range is calculated as an exponential moving average of the true range over a specified period.
- Calculating Position Size: Position size is calculated based on the account funds and average true range to manage risk.
- Generating Trading Signals: Trading signals are generated based on the rules of the turtle trading strategy. Buy signals are triggered when the closing price breaks above the upper Donchian channel, and sell signals are triggered when the closing price breaks below the lower Donchian channel. Additional position may be added if the price moves favorably after a buy signal.
- Exit Conditions: Exit conditions are defined based on Donchian channels and unfavorable price trends to exit positions

### Evaluation Metrics
- Accuracy: 72.41%
- Confusion Matrix: [[  4  67   7]
-                    [ 75 673  23]
-                    [  5  81   0]]
- Classification Report:
-            precision    recall  f1-score   support

-      buy       0.05      0.05      0.05        78
-      none       0.82      0.87      0.85       771
-      sell       0.00      0.00      0.00        86
-  accuracy                           0.72       935
- macro avg       0.29      0.31      0.30       935

### Conclusion
- While the turtle trading strategy demonstrates a moderate level of accuracy, it's important to note that the model's performance may be impacted by the skewness in the dataset. Additionally, the strategy does not allow for assigning class weights, limiting its ability to handle imbalanced data effectively. To address these challenges, an alternative approach was explored by implementing the Random Forest Regressor model. 

---
## Random Forest Regressor Model

### Overview
- The Random Forest Regressor notebook (`RandomForestRegressor.ipynb`) presents a machine learning approach to predict cryptocurrency prices. Below are the key steps involved in the process:

### Feature Engineering
- In this step, additional features like Relative Strength Index,Average True Range,Moving Average Convergence Divergence are engineered based on existing data to enhance the predictive capability of the model. Feature engineering aims to capture relevant information that might not be directly encoded in the original dataset.

### Data Preprocessing
- Data preprocessing involves preparing the dataset for model training. This includes handling missing values, scaling numerical features, encoding categorical variables, and splitting the data into training and testing sets.
- Missing values are typically handled using imputation techniques to ensure that the model can effectively learn from the available data.

### Model Training
- The Random Forest Regressor model is trained on the preprocessed dataset.
- During the training process, class weights are assigned to address the class imbalance issue present in the data.
- Class imbalance occurs when the distribution of target classes is uneven, leading to biased model predictions.
- By assigning higher weights to minority classes, the model is encouraged to pay more attention to these classes during training, thereby improving its ability to generalize to all classes.

### Model Evaluation Metrics
- Accuracy: 80%
- Confusion Matrix: [[  1  0  19]
-                    [  0  2  17]
-                    [  0  1  147]]  
- Classification Report:
-            precision    recall  f1-score   support
-      buy        1.00      0.05      0.10        20
-      none       0.67      0.11      0.18        19
-      sell       0.80      0.99      0.89       148
-  accuracy                           0.80       187
- macro avg       0.82      0.38      0.39       187
- weighted avg    0.81      0.80      0.73       187

The Random Forest Regressor approach offers a data-driven method to predict cryptocurrency prices, leveraging machine learning techniques to capture complex relationships between various market features and price movements.






