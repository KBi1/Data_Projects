# Adult Income Dataset – Analysis and Visualisation

## Overview

This project examines the Adult Income dataset to understand how different factors relate to income levels. The work includes cleaning the raw data, grouping similar categories and creating visualisations that highlight trends across age, gender, education, marital status and workclass.

The aim is to show how structured preparation and clear visual analysis can produce meaningful insights from a large dataset.

---

## Data Cleaning and Preparation

### Handling Missing Values

The dataset includes entries marked as `"?"`, which were replaced with `NaN` so they could be dealt with properly during cleaning.

```python
df.replace('?', np.nan, inplace=True)
```

### Grouping Marital Status

Several marital status categories describe similar situations, so they were grouped to make comparisons clearer:

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

Education levels were consolidated into broader groups. This reduced the number of small categories and made the income patterns easier to interpret:

* **School** (Grades 1–8)
* **Higher School** (Grades 9–12)
* **College** (Associate level)
* **Degree / Masters**
* **Doctorate**

### Renaming Columns

Some columns were renamed to make them more readable and consistent across the analysis.

```python
df.rename(columns={
    'Hoursperweek': 'Working_Hours',
    'Nativecountry': 'Country',
    'Maritalstatus': 'Marital-Status',
    'Income': 'Salary',
}, inplace=True)

AdultDataset = df
```

This helped create cleaner visualisations, especially when comparing salary, marital status and working hours.

---

## Visual Analysis

### Salary Distribution (Pie Chart)

The first pie chart shows the overall income split:

* **75.2%** earn **≤50K**
* **24.8%** earn **>50K**

The dataset is therefore weighted towards lower-income individuals.

### Gender and Salary Comparison

The second chart compares male and female earnings. Two things stand out:

* More men earn **≤50K** than women.
* More men also earn **>50K** than women.

This pattern reflects the fact that there are simply more men in the dataset. It does not by itself prove income inequality, but it does show that male counts dominate both income groups.

### Age Distribution

This chart shows how ages spread across the dataset.

<img width="1040" height="562" alt="image" src="https://github.com/user-attachments/assets/5f5c096b-395c-4fa7-9c69-90f11f3ab28c" />

### Marital Status and Income

This visual compares the grouped marital status categories with salary brackets.

<img width="1035" height="716" alt="image" src="https://github.com/user-attachments/assets/fafaea47-535f-4f79-a9da-9316f9508feb" />

---

## Interpretation

1. **Education is the strongest predictor of income.**
   Higher qualifications are linked with a greater share of >50K earners.

2. **Age plays a clear role.**
   Earnings tend to increase from early adulthood and peak between the mid-30s and mid-50s.

3. **Marital status shows a financial pattern.**
   Married individuals are more likely to fall into the >50K group.

4. **Gender differences are visible.**
   More men appear in both income groups, which reflects their higher representation in the dataset.

5. **Workclass influences earnings, though not as strongly as education.**
   Private sector workers dominate the dataset and show varied income levels.

---

## Conclusion

Cleaning and grouping the dataset allowed the main income patterns to stand out clearly.
Education shows the strongest link to higher earnings, supported by trends in age, marital status and gender. The visualisations provide a clear picture of how these factors interact across the dataset.

---

## Future Work

* Build predictive salary models using machine learning.
* Examine feature importance to confirm key drivers of income.
* Add correlation matrices and other extended visualisations.
* Explore combined factors such as education plus gender.
* Carry out hypothesis testing on significant differences.
* Use logistic regression, random forests or boosting models.
* Create static dashboard images (Python or Power BI) for deeper comparisons.
