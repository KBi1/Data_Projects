# UK Temperature Forecasting
This project uses the **GlobalLandTemperaturesByCity** dataset to analyse long-term temperature patterns in the United Kingdom and produce short-term forecasts.

**Dataset source:**
Kaggle – *Global Land Temperatures by City*
https://www.kaggle.com/datasets/aatithi/globallandtemperaturesbycity

## Overview
This project looks at long-term temperature patterns in the United Kingdom. The aim was to clean the data, extract UK-specific records, create clear visualisations, and produce short-term forecasts using Linear Regression and an ARIMA time series model.

---

## Data Cleaning and Preparation

### Removing Missing Values
The dataset contains some rows where the temperature is not recorded. These have to be removed because missing values can distort averages, mislead the model, and reduce the reliability of the trends.

```python
df = df.dropna(subset=['AverageTemperature'])
```

### Filtering for the United Kingdom
Because the dataset includes cities from across the world, it was filtered so only UK records were kept. This ensures all results and charts relate to UK temperatures only.

```python
df_UK = df[df['Country'] == 'United Kingdom']
```

### Creating a Yearly Temperature Feature
The raw data is reported monthly, which makes long-term patterns difficult to see. To fix this, yearly averages were calculated. This smooths out seasonal changes and makes multi-decade trends much clearer.

```python
yearly_avg = df_UK.groupby('Year')['AverageTemperature'].mean().reset_index()
```

### Monthly Temperature Summary
A monthly average was also created so that seasonal behaviour could be visualised.

```python
monthly_avg = df_UK.groupby('Month')['AverageTemperature'].mean()
```
---

## Visual Analysis

### Average Temperature by Year (1743–2013)
This chart shows how UK temperatures have changed over a long period. Although the values fluctuate from year to year, the general pattern shows a gradual warming trend in the more recent decades.
<img width="1389" height="590" alt="image" src="https://github.com/user-attachments/assets/6e2b450a-2ea5-4edb-a756-dbf47c58353e" />

---
### Average Temperature by Month

This chart shows the familiar UK seasonal pattern.
The coldest months are January to March, and the warmest are July and August.

<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/8463bba7-e6e8-4057-b50f-50126eb98ba9" />

---

## Forecasting Models

Two simple methods were used to produce short-term forecasts for 2022 and 2023.

---

## Linear Regression Temperature Forecast

Linear Regression fits a straight line through the data to show the general direction of change. It is a simple way to estimate how temperatures may continue in the near future.

### Code Used

```python
# Prepare data for Linear Regression
recent_data = yearly_avg[yearly_avg['Year'] >= 1950]  # Filter data from 1950
X_linear = recent_data['Year'].values.reshape(-1, 1)  # Feature: Year
y_linear = recent_data['AverageTemperature'].values   # Target: Temperature

# Train Linear Regression model
linear_model = LinearRegression()  # Create model
linear_model.fit(X_linear, y_linear)  # Train model

# Predict temperature for 2022 and 2023
future_years = np.array([2022, 2023]).reshape(-1, 1)  # Years to predict
predicted_linear = linear_model.predict(future_years)  # Make predictions
```

### Linear Regression Results

| Year | Predicted Temperature |
| ---- | --------------------- |
| 2022 | **10.24°C**           |
| 2023 | **10.26°C**           |

---

## ARIMA Time Series Forecast

ARIMA is a time-series model that looks at patterns over time, such as trends and small changes between years. It is useful when the data points depend on previous values.

### Code Used

```python
# Prepare data for ARIMA
train_data = yearly_avg[yearly_avg['Year'] >= 1950]  # Use data from 1950

# Fit ARIMA model
arima_model = ARIMA(train_data['AverageTemperature'], order=(1, 1, 1)).fit()  # Train model

# Forecast next 2 years
arima_forecast = arima_model.forecast(steps=2)  # Predict 2022-2023
future_years_arima = [2022, 2023]  # Target years

```

### ARIMA Results

| Year | Predicted Temperature |
| ---- | --------------------- |
| 2022 | **9.86°C**            |
| 2023 | **9.92°C**            |

---

## Comparison of Forecasts (2022–2023)

| Year | ARIMA  | Linear Regression | Difference |
| ---- | ------ | ----------------- | ---------- |
| 2022 | 9.86°C | 10.24°C           | 0.39°C     |
| 2023 | 9.92°C | 10.26°C           | 0.34°C     |

Both models show a similar outcome: a small increase year on year.
Linear Regression predicts slightly warmer values because it follows a straight upward trend. ARIMA gives a slightly more conservative estimate as it responds more closely to the recent data.

---

## Interpretation
* UK temperatures have gradually warmed over the past several decades.
* Seasonal patterns remain stable, with warm summers and cold winters.
* Both forecasting methods suggest a small rise in temperature for 2022 and 2023.
* The difference between ARIMA and Linear Regression is minor, which supports the overall pattern seen in the historical data.

---

## Future Work

A few simple extensions could be added later:
* Compare UK cities such as London, Birmingham and Manchester.
* Add decade-level summaries to highlight long-term warming rates.
* Include extra visualisations such as rolling averages or smoothing.
* Add static Power BI charts.
