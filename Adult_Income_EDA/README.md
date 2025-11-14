# Adult Income Dataset – Analysis and Visualisation

## Overview

This project explores the Adult Income dataset to understand how different factors relate to income levels. The work includes cleaning and grouping the data, preparing consistent categories, and building several visualisations to highlight trends in income across age, gender, education, marital status, and workclass.

---

## Data Cleaning and Preparation

### Handling Missing Values

The dataset includes entries marked as `"?"`, which were replaced with `NaN`:

```python
df.replace('?', np.nan, inplace=True)
```

### Grouping Marital Status

To simplify analysis, similar categories were grouped:

* **Married**
* **Single**
* **Separated**

```python
df["Maritalstatus"] = df["Maritalstatus"].replace({
    "Married-civ-spouse": "Married",
    "Married-AF-spouse": "Married",
    "Married-spouse-absent": "Married",
    "Never-married": "Single",
    "Divorced": "Separated",
    "Separated": "Separated",
    "Widowed": "Separated"
})
```

### Grouping Education

Education levels were grouped as:

* **School**: Grades 1–8
* **Higher School**: Grades 9–12
* **College**: Associate-level
* **Degree / Masters**
* **Doctorate**

This reduced noise from having many small categories.

### Renaming Columns

Some columns were renamed to make the dataset clearer and easier to read. This helped standardise naming across the analysis.

```python
# Renaming columns in a single call
df.rename(columns={
    'Hoursperweek': 'Working_Hours',
    'Nativecountry': 'Country',
    'Maritalstatus': 'Marital-Status',
    'Income': 'Salary',
}, inplace=True)

# Assigning the renamed dataframe to a new variable
AdultDataset = df

# Display the renamed DataFrame
AdultDataset
```

This step ensured that later visualisations and grouping operations were easier to follow, especially when comparing salary, marital status, and working hours.

---

## Visual Analysis

### Salary Distribution (Pie Chart)

The first pie chart shows the overall split between people earning **≤50K** and **>50K**.
The distribution is clear:

* **75.2%** of individuals earn **≤50K**
* **24.8%** earn **>50K**

This shows that the majority of the population in the dataset falls within the lower income bracket.

### Gender and Salary Comparison

The second chart compares income levels between males and females. A few points stand out:

* More males earn **≤50K** compared with females.
* More males also earn **>50K** compared with females.
* This suggests that there are simply more men represented in the dataset, which affects the counts in both salary groups.

The chart does not necessarily mean men are paid more because of gender. Instead, it likely reflects that more men are participating in the workforce in this dataset, so both the lower and higher income bands show higher numbers for males.

### Age Distribution

This plot shows how ages are distributed in the dataset.

<img width="1040" height="562" alt="image" src="https://github.com/user-attachments/assets/5f5c096b-395c-4fa7-9c69-90f11f3ab28c" />



### Marital Status and Income

This graph compares marital status against income brackets.

<img width="1035" height="716" alt="image" src="https://github.com/user-attachments/assets/fafaea47-535f-4f79-a9da-9316f9508feb" />


---

## Interpretation

1. **Education strongly influences income.**
   People with degrees, masters, or doctorates are far more likely to earn above 50K.

2. **Age contributes, particularly mid-career.**
   Higher income is more common between ages 35 and 55.

3. **Marital status shows a link with higher earnings.**
   Married individuals have a larger share of >50K incomes.

4. **Gender shows income differences.**
   A higher proportion of men earn above 50K compared with women.

5. **Workclass affects earnings, but not as strongly as education.**
   Private workers form the largest group overall, and income varies widely.

---

## Conclusion

After cleaning and grouping the dataset, several consistent patterns appear. Education is the clearest predictor of income, with higher-level qualifications tied to better pay. Marital status, age, and gender also show clear trends. The visualisations highlight these relationships and support the value of structuring the data before analysis.

---

## Future Work

* Build predictive models for salary using machine learning.
* Run feature importance analysis to confirm key variables.
* Add heatmaps, pair-plots, or correlation matrices.
* Explore combined factors such as gender plus education.
* Include hypothesis testing to measure significance.
* Use logistic regression, random forests, or boosting models.
* Create an interactive dashboard using Plotly, Streamlit, or Power BI.

---

*This README is written in UK English and follows professional documentation standards.*
