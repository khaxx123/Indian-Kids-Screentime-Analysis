
# Indian Kids Screentime Analysis

This project analyzes digital screen time behavior and its potential health implications among Indian students. Using both Python for data wrangling and visualization, and Power BI for dashboarding, the analysis reveals trends across age, gender, device usage, and screen time risk levels.

---

## Project Overview

**Objective:**
To understand and visualize how Indian children use screens and identify usage patterns that may impact their well-being.

**Tools Used:**

* Python (Pandas, Matplotlib, Seaborn)
* Power BI

**Dataset:**
Simulated data of \~9,700 students including:

* Age, Gender
* Average Daily Screen Time
* Primary Device Used
* Educational-to-Recreational Ratio
* Reported Health Impacts
* Urban/Rural Region

---

## Key Features

### Python – Jupyter Notebook

**Data Cleaning & Preprocessing**
Example: Dropping null values and formatting columns

```python
df.dropna(inplace=True)
df['Gender'] = df['Gender'].str.title()
```

**Feature Engineering**

Creating a usage category:

```python
def categorize_usage(row):
    if row['Edu:Rec Ratio'] >= 0.7:
        return 'Educational'
    elif row['Edu:Rec Ratio'] <= 0.3:
        return 'Recreational'
    else:
        return 'Balanced'

df['usage_category'] = df.apply(categorize_usage, axis=1)
```

Classifying screen time risk based on age:

```python
def classify_screen_time_risk(row):
    if row['Age'] <= 10:
        return 'High' if row['Avg Screen Time (hrs)'] > 2 else 'Low'
    elif row['Age'] <= 15:
        return 'High' if row['Avg Screen Time (hrs)'] > 3 else 'Low'
    else:
        return 'High' if row['Avg Screen Time (hrs)'] > 4 else 'Low'

df['screen_time_risk'] = df.apply(classify_screen_time_risk, axis=1)
```

Assigning health impact level:

```python
def assign_health_impact(row):
    if row['Reported Issues'] in ['Poor Sleep', 'Eye Strain', 'Anxiety']:
        return 'Moderate to High'
    return 'Low'

df['health_impact_level'] = df.apply(assign_health_impact, axis=1)
```

**Exploratory Data Analysis**
Example: Plotting average screen time by age group and gender

```python
plt.figure(figsize=(10, 6))
sns.barplot(data=df, x='Age Group', y='Avg Screen Time (hrs)', hue='Gender')
plt.title('Average Screen Time by Age and Gender')
plt.xlabel('Age Group')
plt.ylabel('Hours per Day')
plt.tight_layout()
plt.show()
```
<img width="1668" height="676" alt="image" src="https://github.com/user-attachments/assets/444367cf-9336-4f74-92e4-873c3179611e" />

---

### Power BI – Interactive Dashboard

**Visual Highlights:**

* Total student count
* Average screen time trends by age group
* Primary device usage (pie chart)
* Health impact vs. screen time risk (stacked chart)
* Filters for gender, age, and screen time risk level

  ![powerbidashboard](https://github.com/user-attachments/assets/dd04a5a7-41db-4574-8701-359bd2bcb245)
  ![dashboard2](https://github.com/user-attachments/assets/8ec90095-8a78-44f7-9fa1-bc73a49a5507)



---

## Repository Contents

| Folder    | Description                              |
| --------- | ---------------------------------------- |
| Python/   | Jupyter notebook and cleaned CSV dataset |
| PowerBI/  | Power BI dashboard file (.pbix)          |
| README.md | Project documentation and walkthrough    |

---

## Sample Insights

* Over 81% of students exceed recommended screen time limits.
* Smartphones are the most commonly used device (approximately 47%).
* The 11–15 age group has the highest average daily screen time.
* Predominantly recreational usage correlates with higher reported health risks (e.g., poor sleep, eye strain).

---

## How to Use This Project

### Run the Jupyter Notebook

1. Open: `Python/Indian_kids_screentime_analysis.ipynb`
2. Run all cells to view the full data processing and EDA workflow.

### Explore the Power BI Dashboard

1. Open: `PowerBI/Indian_Kids_Screen_Time_Dashboard.pbix`
2. Use slicers to filter by:

   * Age group
   * Gender
   * Region
3. Hover over charts for dynamic insights.

---

## License

This project is licensed under the MIT License.
Feel free to use or modify it with credit.

---

## About the Author

**KHAHINI BI**
Aspiring Data Analyst | Python | Power BI

LinkedIn: [https://www.linkedin.com/in/khahiniboopathi6/](https://www.linkedin.com/in/khahiniboopathi6/)
Email: [khahini.off.216@gmail.com](mailto:khahini.off.216@gmail.com)

---

If you found this project useful, insightful, or inspiring, feel free to connect with me or give the repository a star!




