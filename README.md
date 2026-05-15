# LEGO Star Wars Analysis 🚀🧱

## Project Overview

This project explores one of the most important turning points in LEGO’s history — the introduction of licensed themes, with a major focus on the **Star Wars partnership**.

Using Python and Pandas, the analysis investigates:

* The dominance of Star Wars among licensed LEGO sets
* Release trends over the years
* The year with the highest number of Star Wars set launches

The goal was to provide actionable insights for LEGO’s partnerships team by analyzing historical LEGO set data.

---

# Dataset Information

## `lego_sets.csv`

Contains information about individual LEGO sets.

| Column         | Description                         |
| -------------- | ----------------------------------- |
| `set_num`      | Unique identifier for each LEGO set |
| `name`         | Name of the LEGO set                |
| `year`         | Release year                        |
| `num_parts`    | Number of pieces in the set         |
| `theme_name`   | Sub-theme name                      |
| `parent_theme` | Parent theme category               |

---

## `parent_themes.csv`

Contains information about LEGO parent themes.

| Column        | Description                             |
| ------------- | --------------------------------------- |
| `id`          | Unique theme identifier                 |
| `name`        | Parent theme name                       |
| `is_licensed` | Indicates whether the theme is licensed |

---

# Objectives

The partnerships team requested answers to the following business questions:

### 1️⃣ What percentage of all licensed LEGO sets were Star Wars themed?

### 2️⃣ Which year recorded the highest number of Star Wars set releases?

---

# Technologies Used

* 🐍 Python
* 📊 Pandas
* 🔍 Exploratory Data Analysis (EDA)

---

# Data Cleaning & Preparation

The following preprocessing steps were carried out:

* Loaded datasets using Pandas
* Merged datasets using the `parent_theme` and `name` columns
* Filtered licensed themes
* Isolated Star Wars themed sets
* Aggregated yearly releases using pivot tables

---

# Python Code

```python
import pandas as pd

# Load datasets
parent_themes = pd.read_csv('data/parent_themes.csv')
lego_sets = pd.read_csv('data/lego_sets.csv')

# Merge datasets
merged_sets = pd.merge(
    parent_themes,
    lego_sets,
    left_on='name',
    right_on='parent_theme'
)

# Filter licensed sets
licensed_sets = merged_sets[merged_sets['is_licensed'] == True]

# Filter Star Wars sets
star_wars_sets = licensed_sets[
    licensed_sets['parent_theme'] == 'Star Wars'
]

# Calculate percentage
the_force = int(
    (len(star_wars_sets) / len(licensed_sets)) * 100
)

# Count yearly releases
year_counts = star_wars_sets.pivot_table(
    index='year',
    values='set_num',
    aggfunc='count'
)

# Find peak release year
new_era = year_counts['set_num'].idxmax()

print(the_force)
print(new_era)
```

---

# Key Insights 📈

## ⭐ Star Wars Dominates Licensed LEGO Themes

> **45%** of all licensed LEGO sets ever released were Star Wars themed.

This highlights how impactful the LEGO–Star Wars collaboration has been in shaping LEGO’s modern product strategy.

---

## 🚀 Peak Star Wars Release Year

> The highest number of Star Wars sets were released in **2016**.

This suggests a major expansion period for the franchise, potentially influenced by:

* New movie releases
* Increased fan engagement
* Strong commercial demand

---

# Business Impact

The findings demonstrate that:

* Licensed collaborations can significantly influence product success
* Star Wars remains one of LEGO’s strongest commercial partnerships
* Strategic entertainment partnerships drive sustained customer engagement

---

# Project Structure

```bash
├── README.md
└── lego_sets.csv
└── parent_themes.csv
```

---

# Future Improvements

Possible extensions for this project include:

* Time-series visualization of LEGO releases
* Comparing Star Wars against other franchises
* Analyzing set complexity using `num_parts`
* Predicting future successful themes using machine learning

---

# Conclusion

This analysis reveals how transformational the Star Wars licensing deal was for LEGO. Nearly half of all licensed LEGO sets belong to the Star Wars universe, proving the enormous value of entertainment partnerships in product growth and brand expansion.

---

# Author

### Jeremiah Kehinde

Aspiring Data Analyst passionate about transforming data into actionable insights.

* Python
* SQL
* Power BI
* Data Visualization
* Exploratory Data Analysis

⭐ If you found this project interesting, feel free to star the repository!
