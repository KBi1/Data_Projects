# Billionaire Data Analysis Project

## Project Overview

This project explores a dataset of global billionaires, focusing on cleaning, pre-processing, and creating visualisations to uncover patterns in wealth, gender, business categories, self-made status, and age. The cleaned dataset is exported for further analysis in tools like Tableau.

---

## 1. Introduction

The aim is to understand trends such as:

* Gender distribution of billionaires
* Wealth concentration across countries and business categories
* Age patterns
* Self-made versus inherited wealth
---

## 3. Dataset Description
This dataset contains detailed information about global billionaires. Each column is described below:

* **Rank**: The billionaire's wealth ranking in the dataset.
* **Category**: The primary business area or industry the billionaire operates in.
* **PersonName**: Full name of the billionaire.
* **Country**: Country of residence.
* **City**: City of residence.
* **Source**: How the billionaire generated their wealth.
* **Industries**: Types of businesses involved.
* **Self Made**: Indicates whether the billionaire made their fortune independently (`Yes`) or inherited it (`No`).
* **Gender**: Gender of the billionaire.
* **LastName**: Last name.
* **FirstName**: First name.
* **FinalWorth**: Net worth in U.S. dollars (converted to billions in the cleaned dataset).
* **BirthYear**: Birth year.
* **BirthMonth**: Birth month.
* **BirthDay**: Birth day.
* **cpi_country**: Consumer Price Index in the billionaire's country.
* **gdp_country**: GDP of the billionaire's country.
* **life_expectancy_country**: Average lifespan in the country.
* **tax_revenue_country**: Tax revenue in the country.
* **total_tax_rate_country**: Overall tax rate in the country.
* **population_country**: Population of the country.


## Data Cleaning

* Removed duplicates.
* Converted `FinalWorth` to billions for easier interpretation.
* Exported cleaned dataset for Tableau or further analysis:

```python
data.to_csv('/content/clean_billionaires_dataset.csv', index=False)
```

## Visualisations

### Gender Distribution

Pie chart showing male vs female billionaires.

### Top Countries by Wealth

Top 5 countries by total billionaire wealth.

### Top Business Categories

Bar chart of top 5 business categories by net worth.

### Self-Made vs Inherited

Pie chart comparing self-made vs inherited billionaires.

### Additional Visualisations

* Age distribution histogram.
* Scatter plot of age vs net worth.
* Country-wise gender distribution.
* Number of billionaires by business category.

## Summary & Insights












