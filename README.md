# 📊 Social Media Impact on Teenagers

An exploratory data analytics and Power BI project analyzing the relationship between **social media usage, lifestyle behaviors, and mental health indicators among teenagers**.

The project uses a dataset of **1,200 teenagers** and combines **Python-based exploratory data analysis, feature engineering, statistical analysis, and Power BI visualization** to identify patterns between social media usage and factors such as sleep, stress, anxiety, addiction, physical activity, and depression.

---

## 📌 Project Overview

Social media has become an important part of teenagers' daily lives. While it provides communication, entertainment, and social interaction, excessive usage may be associated with changes in lifestyle and mental health indicators.

This project explores these relationships using a dataset containing information about teenagers':

* Social media usage
* Preferred social media platform
* Sleep duration
* Screen time before sleep
* Academic performance
* Physical activity
* Social interaction
* Stress level
* Anxiety level
* Addiction level
* Depression classification

The analysis was performed using **Python, Pandas, NumPy, Matplotlib, and Seaborn**, while **Power BI and DAX** were used to create an interactive analytical dashboard.

> **Important:** This project identifies patterns and associations within the dataset. It does not establish that social media usage directly causes depression or other mental health conditions.

---

## 🎯 Project Objectives

The main objectives of this project are to:

* Analyze daily social media usage among teenagers.
* Identify teenagers with low, moderate, and heavy social media usage.
* Compare social media usage between depressed and non-depressed groups.
* Analyze the relationship between social media usage and sleep.
* Examine associations between social media usage and stress.
* Examine associations between social media usage and anxiety.
* Compare addiction levels between different groups.
* Analyze mental health indicators across social media platforms.
* Investigate relationships between lifestyle factors and mental health.
* Engineer additional analytical features.
* Build an interactive Power BI dashboard for data visualization and storytelling.

---

## 🛠️ Technologies & Tools

| Technology           | Purpose                                     |
| -------------------- | ------------------------------------------- |
| **Python**           | Data analysis and feature engineering       |
| **Pandas**           | Data manipulation and analysis              |
| **NumPy**            | Numerical calculations and feature creation |
| **Matplotlib**       | Data visualization                          |
| **Seaborn**          | Statistical visualization                   |
| **Jupyter Notebook** | Exploratory Data Analysis                   |
| **Power BI**         | Interactive dashboard                       |
| **DAX**              | Power BI calculations and measures          |
| **SQLite**           | Database storage                            |
| **CSV**              | Dataset storage                             |

---

## 📂 Project Structure

```text
Social-Media-Impact-on-Teenagers/
│
├── Dashboard/
│   └── Social Media on Teens.pbix
│
├── Data/
│   └── Teen_Mental_Health_Dataset.csv
│
├── Notebook/
│   └── main.ipynb
│
├── datasets/
│   └── teen_mental_health_enriched.csv
│
├── database/
│   └── teen_mental_health.db
│
├── screenshots/
│   ├── executive-summary.png
│   └── behavioral-analysis.png
│
└── README.md
```

> The `screenshots` folder can be added later to display the Power BI dashboard directly on the GitHub project page.

---

# 📊 Dataset

The original dataset contains:

* **1,200 records**
* **13 original features**

### Original Features

| Feature                    | Description                       |
| -------------------------- | --------------------------------- |
| `age`                      | Age of the teenager               |
| `gender`                   | Gender                            |
| `daily_social_media_hours` | Daily hours spent on social media |
| `platform_usage`           | Primary social media platform     |
| `sleep_hours`              | Average sleep duration            |
| `screen_time_before_sleep` | Screen time before sleeping       |
| `academic_performance`     | Academic performance score        |
| `physical_activity`        | Physical activity level           |
| `social_interaction_level` | Level of social interaction       |
| `stress_level`             | Stress level                      |
| `anxiety_level`            | Anxiety level                     |
| `addiction_level`          | Social media addiction level      |
| `depression_label`         | Depression classification         |

---

# 🔍 Exploratory Data Analysis

The Python notebook performs several stages of exploratory analysis.

### Data Inspection

The dataset was examined using:

* Dataset preview
* Column inspection
* Descriptive statistics
* Data type inspection
* Missing-value analysis
* Duplicate detection
* Unique-value analysis
* Categorical value distributions

Example analyses include:

```python
df.describe()
```

```python
df.isnull().sum()
```

```python
df.duplicated().sum()
```

---

# ⚙️ Feature Engineering

Several additional features were created to make the dataset more useful for analysis and visualization.

The enriched dataset contains **19 columns**, including the original 13 features and 6 engineered features.

---

## 1. Usage Category

Teenagers were categorized according to their daily social media usage.

```text
Daily Social Media Hours < 2
        ↓
Low Usage

2 ≤ Daily Social Media Hours < 5
        ↓
Moderate Usage

Daily Social Media Hours ≥ 5
        ↓
Heavy Usage
```

This feature is stored in:

```text
usage_category
```

---

## 2. Mental Health Score

A composite analytical score was created using:

* Stress level
* Anxiety level
* Addiction level

Formula:

```text
Mental Health Score =
Stress Level + Anxiety Level + Addiction Level
```

This feature is stored in:

```text
mental_health_score
```

A higher value represents higher levels of the selected mental-health-related indicators.

> This is a project-specific analytical score and is not a clinical mental health measurement.

---

## 3. Wellness Score

A simple wellness-oriented metric was created using:

* Sleep
* Physical activity
* Social media usage

Formula:

```text
Wellness Score =
Sleep Hours + Physical Activity - Daily Social Media Hours
```

This feature is stored in:

```text
wellness_score
```

> This score is an analytical construct created for this project and should not be interpreted as a medical or clinical wellness measurement.

---

## 4. Risk Category

Teenagers were grouped according to their calculated mental health score.

```text
0–10   → Low
10–20  → Medium
20–30  → High
```

This feature is stored in:

```text
risk_category
```

The category is used for analytical visualization and does not represent a clinical risk assessment.

---

## 5. Sleep Deficit

Sleep deficit was calculated using an 8-hour reference.

Formula:

```text
Sleep Deficit = 8 - Sleep Hours
```

This feature is stored in:

```text
sleep_deficit
```

---

## 6. Social Media Intensity

A ratio was created to compare daily social media usage with sleep duration.

Formula:

```text
Social Media Intensity =
Daily Social Media Hours / Sleep Hours
```

This feature is stored in:

```text
social_media_intensity
```

---

# ❓ Analytical Questions

The project investigates several important questions.

## Question 1 — Do depressed teenagers spend more time on social media?

Average daily social media usage is compared between teenagers classified as depressed and non-depressed.

```python
df.groupby('depression_label')['daily_social_media_hours'].mean()
```

---

## Question 2 — Do depressed teenagers sleep less?

Average sleep duration is compared between depression groups.

```python
df.groupby('depression_label')['sleep_hours'].mean()
```

---

## Question 3 — Do depressed teenagers have higher stress levels?

Stress levels are compared between depressed and non-depressed teenagers.

```python
df.groupby('depression_label')['stress_level'].mean()
```

---

## Question 4 — Do depressed teenagers have higher addiction levels?

Addiction levels are compared between depression groups.

```python
df.groupby('depression_label')['addiction_level'].mean()
```

---

# 📱 Platform Analysis

The project also analyzes differences across social media platforms.

For each platform, the following metrics are examined:

* Average daily social media usage
* Average stress level
* Average anxiety level
* Average addiction level

This helps identify behavioral differences between users of different platforms.

---

# 📈 Correlation Analysis

Correlation analysis was performed on numerical variables to identify relationships between:

* Social media usage
* Sleep
* Stress
* Anxiety
* Addiction
* Physical activity
* Academic performance
* Depression classification
* Other numerical variables

A correlation heatmap was also created using **Seaborn**.

The project also examines the correlation of individual numerical variables with:

```text
depression_label
```

> Correlation indicates an association between variables and does not prove causation.

---

# 🧠 Mental Health & Risk Analysis

The project uses the engineered `mental_health_score` to explore differences between depression groups.

The analysis includes:

* Average mental health score
* Mental health score distribution
* Descriptive statistics
* Risk-category distribution
* Cross-tabulation between risk category and depression classification
* Box plot comparison

This provides an additional analytical perspective beyond the original dataset variables.

---

# 😴 Behavioral Analysis

The project investigates relationships between social media usage and lifestyle factors.

### Social Media Usage vs Sleep

The correlation between:

```text
daily_social_media_hours
```

and:

```text
sleep_hours
```

is analyzed.

### Social Media Usage vs Stress

The relationship between:

```text
daily_social_media_hours
```

and:

```text
stress_level
```

is examined.

### Social Media Usage vs Anxiety

The relationship between:

```text
daily_social_media_hours
```

and:

```text
anxiety_level
```

is also analyzed.

---

# 👥 Demographic & Social Analysis

The project also examines differences across:

### Gender

Metrics analyzed include:

* Daily social media usage
* Sleep
* Stress
* Anxiety
* Mental health score

### Social Interaction Level

The same behavioral and mental health indicators are analyzed across different social interaction levels.

---

# 📊 Power BI Dashboard

The analysis was converted into an interactive Power BI dashboard.

The dashboard is designed to transform the analytical results into an easily understandable visual story.

## Dashboard Page 1 — Executive Summary

The Executive Summary provides high-level KPIs and an overview of the dataset.

The dashboard includes metrics such as:

* Average daily social media usage
* Average sleep duration
* Depression percentage
* Average mental health score
* Average wellness score

This page provides a quick snapshot of the overall dataset.

---

## Dashboard Page 2 — Behavioral Analysis

The Behavioral Analysis page focuses on relationships between social media usage and behavioral or mental health indicators.

The analysis includes:

* Social media usage vs sleep
* Social media usage vs stress
* Social media usage vs anxiety
* Gender-based analysis
* Social interaction analysis
* Mental health score analysis
* Other behavioral comparisons

---

# 🔄 Project Workflow

```text
                 Raw Dataset
                      │
                      ▼
             Data Exploration
                      │
                      ▼
          Data Quality Validation
                      │
                      ▼
             Feature Engineering
                      │
                      ▼
         Exploratory Data Analysis
                      │
                      ▼
             Correlation Analysis
                      │
                      ▼
            Enriched Dataset
                      │
                      ▼
              Power BI Model
                      │
                      ▼
              DAX Calculations
                      │
                      ▼
           Interactive Dashboard
```

---

# 📁 Project Files

### `Teen_Mental_Health_Dataset.csv`

The original dataset containing 1,200 teenager records and 13 features.

### `teen_mental_health_enriched.csv`

The processed dataset containing the original features along with engineered features:

* `usage_category`
* `mental_health_score`
* `wellness_score`
* `risk_category`
* `sleep_deficit`
* `social_media_intensity`

### `main.ipynb`

Jupyter Notebook containing:

* Data exploration
* Data quality checks
* Feature engineering
* Group-based analysis
* Correlation analysis
* Statistical exploration
* Dashboard metric preparation

### `Social Media on Teens.pbix`

Power BI dashboard containing the project's interactive visual analysis.

### `teen_mental_health.db`

SQLite database containing the project data.

---

# 📌 Key Insights

The project focuses on identifying patterns and associations between social media usage and teenage lifestyle and mental health indicators.

The analysis examines whether teenagers with different depression classifications show differences in:

* Social media usage
* Sleep duration
* Stress
* Anxiety
* Addiction
* Mental health score
* Wellness score

It also explores how these indicators vary by:

* Social media platform
* Gender
* Social interaction level
* Social media usage category

The Power BI dashboard makes these relationships easier to explore through interactive visualizations.

---

# ⚠️ Limitations

There are several important limitations to this analysis.

### 1. Correlation does not imply causation

The project identifies relationships within the dataset but cannot establish that social media usage causes depression, anxiety, stress, or other outcomes.

### 2. Analytical scores are not clinical measurements

`mental_health_score`, `wellness_score`, and `risk_category` were created specifically for analytical purposes in this project.

They should not be interpreted as medical diagnoses or clinical assessments.

### 3. Dataset limitations

The dataset contains 1,200 records and may not represent the broader teenage population.

### 4. Observational analysis

The analysis is based on observed data and does not use a controlled experimental design.

### 5. Generalization

The results should not automatically be generalized to all teenagers, populations, countries, or age groups.

---

# 🚀 Future Improvements

The project can be extended in several ways.

### Data & Analysis

* Add a larger and more diverse dataset.
* Perform statistical significance testing.
* Perform regression analysis.
* Investigate additional demographic variables.
* Analyze interactions between multiple behavioral factors.

### Machine Learning

Potential future models could include:

* Logistic Regression
* Decision Tree
* Random Forest
* Gradient Boosting
* Classification models for depression prediction

### Power BI

The dashboard could be extended with:

* Additional report pages
* More advanced DAX measures
* Drill-through analysis
* Interactive filters and slicers
* More detailed platform comparisons
* Advanced tooltips
* Power BI Service deployment

### Data Engineering

The project could also be developed into a larger data pipeline involving:

```text
Data Source
    ↓
Data Ingestion
    ↓
Data Cleaning
    ↓
Data Transformation
    ↓
Data Storage
    ↓
Power BI
```

This would allow the project to evolve from a static analytics project into an automated data analytics pipeline.

---

# 💡 Skills Demonstrated

This project demonstrates practical experience in:

* Exploratory Data Analysis
* Data Cleaning
* Data Quality Checking
* Data Transformation
* Feature Engineering
* Statistical Analysis
* Correlation Analysis
* Data Visualization
* Data Storytelling
* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook
* Power BI
* DAX
* SQLite
* Dashboard Development

---

# 📚 Learning Outcomes

Through this project, the following practical skills were developed:

1. Understanding and exploring a real-world style dataset.
2. Performing data quality checks using Python.
3. Creating analytical features using Pandas and NumPy.
4. Performing group-based and correlation analysis.
5. Translating analytical questions into measurable metrics.
6. Preparing an enriched dataset for visualization.
7. Building an interactive Power BI dashboard.
8. Presenting data-driven insights through visual storytelling.
9. Understanding the difference between correlation and causation.
10. Structuring a data analytics project for portfolio and GitHub presentation.

---

# ⚖️ Disclaimer

This project is intended for **educational and analytical purposes only**.

The scores, categories, and relationships presented in this project are based on the available dataset and the analytical methodology used in the project.

They should not be interpreted as medical, psychological, or clinical conclusions.

The project demonstrates how data analytics and visualization can be used to explore patterns in social media usage and mental health-related indicators.

---

## 👨‍💻 Author

**Rizwan Haq**

GitHub: [RizwanHaq11](https://github.com/RizwanHaq11)

---

⭐ If you found this project interesting, feel free to explore the notebook and Power BI dashboard.
