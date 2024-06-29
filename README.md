# Gold Price Analysis and Forecasting

## Introduction 🌟

This project focuses on the analysis and forecasting of gold prices from 1950 onwards. The dataset comprises monthly gold prices, and we aim to build various time series models to predict future prices. We also incorporate exogenous variables such as Nasdaq stock prices and Google Trends search data for "gold price" to enhance the forecasting accuracy.

## Problem Statement 📝

The objective of this project is to analyze and forecast monthly gold prices from 1950 onwards using various time series models. The challenge includes evaluating the effectiveness of different models, incorporating exogenous variables such as Nasdaq stock prices and Google Trends data, and determining the most accurate approach for predicting future gold prices. This analysis aims to identify the model that provides the best balance between accuracy and computational efficiency for practical forecasting applications.

## Data Information 📊

The dataset consists of monthly gold prices from 1950. Key details of the data include:

- **Date Range:** 1950-01 to the latest available date.
- **Frequency:** Monthly.
- **Variables:** Date, Gold Price.

## Data Preprocessing and Analysis 🧹

Data preprocessing steps include:

1. **Handling Missing Values:** 
   - Imputation or removal of missing values as needed.
   - Methods used: Linear interpolation and forward fill.

2. **Log Transformation:**
   - Applied log transformation to stabilize the variance and make the series more stationary.

3. **Exogenous Variables:**
   - Added Nasdaq stock prices and Google Trends search data for "gold price" as exogenous variables.
   - Lagged versions of these variables were also created to account for delayed effects.

4. **Seasonal Decomposition:**
   - Decomposed the time series into trend, seasonality, and residual components to understand underlying patterns.

**Dataset Structure**: The dataset comprises 847 entries, each containing the date of observation and the corresponding gold price.

- **Statistical Summary**: 
  - Mean gold price: $416.56
  - Standard deviation: $453.67
  - Minimum price: $34.49
  - Maximum price: $1840.81
    
- **Trends and Patterns**:
  - Gold prices were relatively stable until the 1970s, after which they began to increase, with significant rises in the early 1980s and post-2005.
  - Periods of economic instability, such as the financial crisis of 2008-09, correlate with sharp increases in gold prices.
  - Box plots and coefficient of variation analyses highlight the presence of outliers and the variability in gold prices over different periods.

## Limiting Data for Specific Time Periods
- **Analysis**: Limiting the dataset to the period from 1975 to 2020 provided more relevant insights, as earlier data was relatively stagnant and less informative.
- **Stationarity Check**:
  - The Dickey-Fuller Test indicated that the original data was non-stationary.
  - After differencing once, the data became stationary, ready for further modeling.
    
## Log Transformation and Forecasting
- **Purpose**: Log transformation was applied to stabilize variance, linearize exponential growth, and reduce skewness.
- **Impact**:
  - Original data exhibited significant volatility, which was smoothed by the log transformation.
  - Differencing once (d = 1) helped remove the trending pattern, making the data more suitable for modeling.

## Model Building 🛠️

We built various time series models, both with and without log transformation. The models include:

1. **Naive Model**
2. **Simple Moving Average (SMA)**
3. **Linear Regression (LR)**
4. **Autoregressive (AR)**
5. **Autoregressive Integrated Moving Average (ARIMA)**
6. **Seasonal ARIMA (SARIMA)**
7. **Seasonal ARIMA with Exogenous Variables (SARIMAX)**
8. **Simple Exponential Smoothing (SES)**
9. **Double Exponential Smoothing (DES)**
10. **Triple Exponential Smoothing (TES)**

### Model Explanations

#### 1. Naive Model
The Naive Model forecasts future values based on the last observed value. It assumes that the next value will be the same as the most recent one.

#### 2. Simple Moving Average (SMA)
SMA calculates the average of a specified number of past data points to forecast future values. It gives equal weight to all observations within the chosen window.

#### 3. Linear Regression (LR)
Linear Regression uses historical data to establish a linear relationship between the dependent variable (gold price) and one or more independent variables (e.g., time). It predicts future values based on this linear relationship.

#### 4. Autoregressive (AR)
AR models predict future values based on a linear combination of past values of the series. It assumes that the value at any given time depends linearly on its previous values (lags).

#### 5. Autoregressive Integrated Moving Average (ARIMA)
ARIMA combines autoregression (AR), differencing (I), and moving average (MA). It's effective for non-stationary data by differencing the series to make it stationary before applying AR and MA components.

#### 6. Seasonal ARIMA (SARIMA)
SARIMA extends ARIMA by incorporating seasonal components to account for seasonal patterns in the data. It includes additional parameters for seasonal AR, MA, and differencing.

#### 7. Seasonal ARIMA with Exogenous Variables (SARIMAX)
SARIMAX incorporates external factors (exogenous variables) alongside the time series data to improve forecasting accuracy. It includes additional terms in the model equation for these variables.

#### 8. Simple Exponential Smoothing (SES)
SES forecasts future values by giving exponentially decreasing weights to past observations. It places more weight on recent data points and is suitable for data with no clear trend or seasonality.

#### 9. Double Exponential Smoothing (DES)
DES extends SES by incorporating a trend component in addition to the level component. It forecasts future values by capturing both the level and trend of the time series.

#### 10. Triple Exponential Smoothing (TES)
TES, also known as Holt-Winters method, extends DES by adding a seasonal component. It forecasts future values by considering the level, trend, and seasonality of the time series data.

### Evaluation Metrics 📈

We used the following evaluation metrics to assess the model performance:

- **Mean Absolute Error (MAE)**
- **Mean Squared Error (MSE)**
- **Root Mean Squared Error (RMSE)**
- **Mean Absolute Percentage Error (MAPE)**

### Performance Summary

#### Models without Log Transformation from 1950

| Name of Model                                          | MAE        | MSE          | RMSE        | MAPE  |
|--------------------------------------------------------|------------|--------------|-------------|-------|
| LR model without log P from 1950                       | 30.29      | 1508.97      | 38.85       | 2.33  |
| Linear Reg model without log P from 1950               | 30.29      | 1508.97      | 38.85       | 2.33  |
| Naive model without log P from 1950                    | 32.72      | 1667.13      | 40.83       | 2.51  |
| SMA model without log P w5 from 1950                   | 41.04      | 2575.24      | 50.75       | 3.10  |
| SARIMA model without log P from 1950                   | 81.12      | 16133.15     | 127.02      | 5.86  |
| AR model without log P lag 8 from 1950                 | 84.69      | 16469.51     | 128.33      | 6.17  |
| ARIMA model without log P from 1950                    | 110.32     | 28804.38     | 169.72      | 7.73  |
| SARIMAX without log P from 1950 w Stock Price          | 143.57     | 29011.40     | 170.33      | 8.39  |
| DES model without log P from 1950 trend mul            | 117.31     | 22099.93     | 148.66      | 8.97  |
| SARIMAX log P from 1950 w Stock Price exo              | 155.50     | 33165.38     | 182.11      | 9.11  |
| SES model without log P from 1950 without detrend      | 120.48     | 22741.75     | 150.80      | 9.23  |
| SARIMAX without log P from 1950 w Search exo           | 179.49     | 51228.15     | 226.34      | 11.15 |
| SARIMAX without log P from 1950 w Search exo lag 1     | 195.98     | 62303.30     | 249.61      | 12.15 |
| TES model without log P from 1950 trend mul seasonal   | 868.34     | 926162.08    | 962.37      | 65.49 |
| TES model without log P from 1950 trend mul seasonal 2 | 995.00     | 1202127.00   | 1096.42     | 75.26 |

#### Models with Log Transformation from 1950

| Name of Model                                          | MAE        | MSE          | RMSE        | MAPE  |
|--------------------------------------------------------|------------|--------------|-------------|-------|
| LR model with log P from 1950                          | 30.29      | 1472.13      | 38.37       | 2.34  |
| Linear Reg model with log P from 1950                  | 30.29      | 1472.13      | 38.37       | 2.34  |
| Naive model with log P from 1950                       | 32.72      | 1667.13      | 40.83       | 2.51  |
| SMA model with log P w5 from 1950                      | 41.24      | 2611.93      | 51.11       | 3.12  |
| DES model with log P from 1950 trend mul               | 99.74      | 25051.95     | 158.28      | 7.02  |
| SARIMAX with log P from 1950 w Stock Price exo         | 126.71     | 23434.18     | 153.08      | 7.39  |
| SARIMAX log P from 1950 w Stock Price exo              | 132.84     | 25275.16     | 158.98      | 7.77  |
| ARIMA model with log P from 1950                       | 108.06     | 16800.06     | 129.62      | 8.48  |
| SES model with log P from 1950 without detrend         | 120.32     | 22718.63     | 150.73      | 9.21  |
| SARIMAX with log P from 1950 w Search exo lag 1        | 160.71     | 41081.91     | 202.69      | 10.01 |
| SARIMAX with log P from 1950 w Search exo              | 162.14     | 41396.83     | 203.46      | 10.10 |
| SARIMA model with log P from 1950                      | 172.81     | 41375.99     | 203.41      | 13.64 |
| AR model with log P lag 8 from 1950                    | 206.25     | 55391.19     | 235.35      | 16.39 |
| TES model with log P from 1950 trend mul seasonal      | 828.71     | 845512.08    | 919.52      | 62.45 |
| TES model with log P from 1950 trend mul seasonal 2    | 915.29     | 979035.82    | 989.46      | 69.40 |

#### Models with Log Transformation from 1975

| Name of Model                                          | MAE        | MSE          | RMSE        | MAPE  |
|--------------------------------------------------------|------------|--------------|-------------|-------|
| LR model with log P from 1975                          | 32.85      | 1746.07      | 41.79       | 2.43  |
| Linear Reg model with log P from 1975                  | 32.85      | 1746.07      | 41.79       | 2.43  |
| Naive model with log P from 1975                       | 33.06      | 1815.20      | 42.61       | 2.45  |
| SMA model with log P w5 from 1975                      | 44.21      | 2998.52      | 54.76       | 3.19  |
| SARIMAX with log P from 1975 w Stock Price exo         | 126.71     | 23434.18     | 153.08      | 7.39  |
| SARIMAX log P from 1975 w Stock Price exo              | 132.84     | 25275.16     | 158.98      | 7.77  |
| SARIMAX with log P from 1975 w Search exo lag 1        | 160.71     | 41081.91     | 202.69      | 10.01 |
| SARIMAX with log P from 1975 w Search exo              | 162.14     | 41396.83     | 203.46      | 10.10 |
| SARIMA model with log P from 1975                      | 193.73     | 50666.45     | 225.09      | 13.83 |
| SES model with log P from 1975 without detrend         | 269.89     | 96823.27     | 311.16      | 19.19 |
| DES model with log P from 1975 trend mul               | 325.74     | 132501.38    | 364.01      | 23.34 |
| AR model with log P lag 8 from 1975                    | 359.20     | 163677.46    | 404.57      | 25.70 |
| ARIMA model with log P from 1975                       | 409.09     | 206835.77    | 454.79      | 29.38 |
| TES model with log P from 1975 trend mul seasonal      | 540.89     | 368747.59    | 607.25      | 38.85 |
| TES model with log P from 1975 trend mul seasonal 2    | 878.07     | 888675.57    | 942.70      | 63.94 |

## Graphs and Visualizations 📊

Here are some key visualizations that help understand the data and model performance:

### 1. Average Gold Price Yearly Since 1950
![Average Gold Price Yearly Since 1950](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/Average%20Gold%20Price%20Yearly%20Since%201950%20onwards.png)

### 2. Comparison of Original Price and Log Transformed Price
![Comparison of Original Price and Log Transformed Price](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/Comparison%20of%20Original%20Price%20and%20Log%20Transformed%20Price.png)

### 3. Gold Price Monthly Since 1950
![Gold Price Monthly Since 1950](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/Gold%20Price%20Monthly%20Since%201950%20onwards.png)

### 4. Gold Price vs Nasdaq Stock (Lag 1) Close with Correlation Value
![Gold Price vs Nasdaq Stock (Lag 1) Close with Correlation Value](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/Gold%20Price%20vs%20Nasdaq%20Stock%20(%20lag%201%20)%20Close%20with%20correlation%20value.png)

### 5. Gold Price vs. Gold Price Search (Lag 1) with Correlation
![Gold Price vs. Gold Price Search (Lag 1) with Correlation](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/Gold%20Price%20vs.%20Gold%20Price%20Search%20(%20lag%201%20)%20with%20correlation.png)

### 6. Gold Prices Monthly Since 1950 and Onwards
![Gold Prices Monthly Since 1950 and Onwards](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/Gold%20Prices%20Monthly%20Since%201950%20and%20onwards.png)

### 7. Seasonal Decompose Graph (Trend, Seasonality, and Residual)
![Seasonal Decompose Graph (Trend, Seasonality, and Residual)](https://github.com/ashay-thamankar/gold_price_analysis_and_forecasting/blob/main/graphs/seasonal%20decompose%20graph%20trend%2C%20seasonality%20and%20residual.png)

## Usage

1. **Clone the repository to your local machine:**

```bash
git clone https://github.com/ashay-thamankar/gold-price-forecasting-model.git
```

2. **Navigate to the project directory:**

```bash
cd gold_price_analysis_and_forecasting
```

3. **Activate the conda environment:**

```bash
conda activate gold
```

## Conclusion 📌

The analysis and forecasting of gold prices using time series models reveal that simpler models like Linear Regression and Naive models perform relatively well compared to more complex models like SARIMAX and TES. Incorporating exogenous variables such as Nasdaq stock prices and Google Trends data did not significantly improve the forecasting accuracy.

- **Trend Analysis**: Gold prices show long-term upward trends with periodic volatility influenced by economic and geopolitical factors.
- **Seasonality**: Identified yearly seasonality patterns, with an additive nature for seasonality and multiplicative for trends.
- **Correlations**:
  - Positive correlations were found between gold prices and both Nasdaq stock prices and Google search trends for "gold price".
  - These factors can be considered as exogenous variables in advanced models.

Key takeaways:
- **Linear Regression** models, both with and without log transformation, show the best performance with the lowest MAE and RMSE.
- **Exponential Smoothing** models, especially Triple Exponential Smoothing, performed poorly, indicating a need for more refined parameter tuning or alternative approaches.
- **SARIMA and SARIMAX** models, while more sophisticated, did provide substantial improvements in accuracy.

Future work could involve exploring more advanced machine learning models or further tuning the existing time series models to enhance forecasting accuracy. 

Thank you for exploring this analysis! 📈✨
