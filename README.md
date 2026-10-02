# 🚕 Taxis Dataset Analysis

## 📌 Project Overview

This project performs **data cleaning, exploratory data analysis (EDA), and data visualization** on the Seaborn `taxis` dataset.

The analysis focuses on understanding taxi trip patterns, fares, distances, tips, payment methods, and pickup locations using **Python, Pandas, Matplotlib, and Seaborn**.

---

## 🎯 Objectives

* Load and explore the Taxis dataset.
* Identify and handle missing values.
* Apply appropriate imputation techniques for categorical data.
* Analyze taxi fares, trip distances, tips, and payment methods.
* Compare taxi activity across pickup boroughs and zones.
* Examine relationships between numerical variables.
* Create meaningful visualizations using Matplotlib, Pandas Plot, and Seaborn.

---

## 🛠️ Tools & Technologies

* Python
* Pandas
* Matplotlib
* Seaborn
* Google Colab / Jupyter Notebook

---

## 📂 Dataset

The project uses the built-in **Seaborn `taxis` dataset**.

```python
import seaborn as sns

df = sns.load_dataset("taxis")
```

The dataset contains information about taxi trips, including:

* Pickup and drop-off timestamps
* Number of passengers
* Trip distance
* Fare
* Tip
* Tolls
* Total amount
* Payment method
* Pickup and drop-off zones
* Pickup and drop-off boroughs

---

## 🧹 Data Cleaning

Missing values were identified using:

```python
df.isnull().sum()
```

Missing data was found in:

* `payment`
* `pickup_zone`
* `dropoff_zone`
* `pickup_borough`
* `dropoff_borough`

The `payment` column contained **44 missing values**. Since it is categorical, the missing values were imputed using the **mode**.

```python
df['payment'] = df['payment'].fillna(df['payment'].mode()[0])
```

`credit card` was the most frequently occurring payment method.

Rows containing missing pickup or drop-off location information were removed because these values could not be reliably imputed without introducing inaccurate geographical information.

```python
df = df.dropna(
    subset=[
        'pickup_zone',
        'dropoff_zone',
        'pickup_borough',
        'dropoff_borough'
    ]
).copy()
```

---

## 📊 Matplotlib / Pandas Visualizations

### 1. Fare Over Time — Line Chart

Analyzed changes in individual taxi fares based on pickup timestamps.

### 2. Total Fare by Pickup Borough — Bar Chart

Compared the total fare generated from different pickup boroughs.

### 3. Trips by Payment Method — Pie Chart

Displayed the proportion of trips made using different payment methods.

### 4. Trip Distance Distribution — Histogram

Analyzed the frequency distribution of taxi trip distances.

### 5. Tips by Pickup Borough — Box Plot

Compared tip distributions across boroughs and helped identify potential outliers.

---

## 📈 Seaborn Visualizations

### 1. Trips by Pickup Borough — Count Plot

Compared the number of taxi trips originating from each borough.

### 2. Distance vs Fare — Scatter Plot

Examined the relationship between trip distance and fare, differentiated by pickup borough.

### 3. Correlation Heatmap

Analyzed correlations among:

* Distance
* Fare
* Tip
* Tolls
* Total

### 4. Pair Plot

Explored pairwise relationships between:

* Distance
* Fare
* Tip
* Total

The **five most frequent pickup zones** were selected for the pair plot because using all pickup zones made the visualization computationally intensive and difficult to interpret.

### 5. Fare by Payment Method — Violin Plot

Compared the distribution and density of taxi fares across different payment methods.

---

## 🔍 Key Findings

* Credit card was the most frequently used payment method.
* Most taxi trips were concentrated within shorter-distance ranges, while long-distance trips occurred less frequently.
* Taxi trip volume varied across pickup boroughs.
* Total fare generation also differed across pickup boroughs.
* Trip distance and fare showed an overall positive relationship, with longer trips generally associated with higher fares.
* Tip amounts varied across pickup boroughs, with some potential high-value outliers.
* Correlation analysis helped identify relationships among distance, fare, tip, tolls, and total trip amount.
* The top pickup zones showed different patterns across distance, fare, tip, and total values.

---

## 💡 Skills Demonstrated

* Data Loading
* Data Inspection
* Missing Value Analysis
* Mode Imputation
* Data Cleaning
* Data Filtering
* Datetime Conversion
* Data Aggregation
* Exploratory Data Analysis (EDA)
* Correlation Analysis
* Data Visualization
* Interpretation of Analytical Results

---

## ✅ Conclusion

This project demonstrates an end-to-end exploratory analysis of taxi trip data using Python. The dataset was cleaned by appropriately handling missing categorical and location information before performing the analysis.

Using **Pandas, Matplotlib, and Seaborn**, multiple visualization techniques were applied to understand trip activity, payment preferences, fare and distance distributions, tipping patterns, geographical differences, and relationships among numerical variables.

The project highlights how data cleaning and visualization can transform raw transportation data into meaningful and interpretable insights.

---

