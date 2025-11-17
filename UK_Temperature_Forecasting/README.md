# UK Temperature Forecasting – Linear Regression and ARIMA
Using the *GlobalLandTemperaturesByCity* Dataset

Dataset URL: https://www.kaggle.com/datasets/aatithi/globallandtemperaturesbycity

## Overview

This project explores long-term temperature patterns in the United Kingdom using the GlobalLandTemperaturesByCity dataset. The aim is to clean the data, prepare a UK-specific subset, and create clear visualisations that highlight yearly and seasonal behaviour. Additional forecasting work is included using Linear Regression and an ARIMA time series model.

---

## Data Cleaning and Preparation

### Removing Missing Values

The dataset contains gaps where temperature readings were not recorded. These records were removed to ensure that the analysis reflects only valid observations.

```python
df = df.dropna(subset=['AverageTemperature'])
```

### Selecting United Kingdom Records

The full dataset covers thousands of cities around the world, so it was first filtered to include only UK entries. This ensures that all calculations and plots relate strictly to the United Kingdom.

```python
df_UK = df[df['Country'] == 'United Kingdom']
```

### Creating a Yearly Temperature Feature

Annual averages were calculated to make long-term patterns easier to interpret. Since the dataset provides temperature measurements at the monthly level, the data can be noisy when viewed directly. Grouping by year and taking the mean smooths out the regular seasonal cycle, making multi-decade trends more visible.

```python
yearly_avg = df_UK.groupby('Year')['AverageTemperature'].mean().reset_index()
```

### Creating a Monthly Temperature Summary

To understand seasonal behaviour, the average temperature for each month was also calculated.

```python
monthly_avg = df_UK.groupby('Month')['AverageTemperature'].mean()
```

---

## Visual Analysis

### Yearly Temperature Trend (1743–2013)

This line chart shows the average yearly temperature over a long historical span. It highlights natural fluctuations and a gradual warming trend in modern decades.

<img width="1389" height="590" alt="image" src="https://github.com/user-attachments/assets/440155bf-1c7b-4da8-a42c-0efd118495a1" />

---

### Monthly Temperature Pattern

This bar chart shows the average temperature for each month across the dataset. It follows the familiar UK seasonal structure:

* Coldest months: January to March
* Warmest months: July and August
* Cooling period towards winter from September

<img width="989" height="490" alt="image" src="https://github.com/user-attachments/assets/57b8587d-43dc-409b-9fe8-8bcfa345fd0a" />

---

## Forecasting Models

Two simple forecasting methods were explored using the yearly average data from 1950 onwards.

---

## Linear Regression Temperature Forecast

A linear trend line was fitted to the post-1950 data to estimate temperatures for the next two years.

**Linear Regression Predictions:**

* 2022: 10.24°C
* 2023: 10.26°C

---

## ARIMA Time Series Forecast

A time series model (ARIMA (1,1,1)) was fitted to the same post-1950 UK data. This approach models temporal patterns directly and produces a short-term two-year forecast.
---

### ARIMA Forecast Results

**ARIMA Predictions:**

* 2022: 9.86°C
* 2023: 9.92°C

---

## Temperature Predictions Comparison (2022–2023)


### ARIMA Model Predictions:
- 2022: 9.86°C
- 2023: 9.92°C

### Linear Regression Predictions:
- 2022: 10.24°C
- 2023: 10.26°C

### Differences Between Models:
- 2022 Difference: 0.39°C
- 2023 Difference: 0.34°C


The two models produce similar results overall, with Linear Regression giving slightly warmer estimates.

---

## Interpretation

1. UK temperatures show a gradual upward trend over the modern period.
2. Seasonal patterns are stable, with warm summers and cool winters.
3. The Linear Regression model captures a simple upward trend.
4. The ARIMA model reacts more closely to the recent data, producing slightly lower short-term forecasts.
5. Differences between the two methods are small, which suggests that the underlying pattern is consistent.

---

## Future Work

You may extend this project with:

* A comparison between UK cities such as London, Birmingham and Manchester.
* More advanced forecasting models such as random forests or gradient boosting.
* Broader climate indicators such as variance, extremes or decade-based summaries.
* Additional static dashboard images created in Power BI.
* A wider global comparison with other major countries or climate zones.
