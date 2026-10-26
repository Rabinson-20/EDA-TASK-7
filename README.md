# 📊 Student Performance Exploratory Data Analysis (EDA)

## 📌 Project Overview

This project focuses on performing **Exploratory Data Analysis (EDA)** on a student performance dataset using Python. It analyzes students' mathematics, reading, and writing scores to understand their academic performance and explore patterns in the dataset.

The project also calculates total scores, percentages, average scores, pass/fail status, and identifies potential outliers in mathematics scores.

## 📂 Project Files

| File Name | Description |
|---|---|
| `Task7_EDA.ipynb` | Jupyter Notebook containing Python code for data exploration, statistical analysis, and outlier detection. |
| `StudentsPerformance.csv` | Dataset containing student demographic information and examination scores. |

## 📊 Dataset Information

- **Total Records:** 1,000
- **Total Columns:** 8
- **File Format:** CSV

### Dataset Features

| Feature | Description |
|---|---|
| `gender` | Gender of the student |
| `race/ethnicity` | Student's race/ethnicity group |
| `parental level of education` | Parent's education level |
| `lunch` | Type of lunch received |
| `test preparation course` | Test preparation course completion status |
| `math score` | Mathematics examination score |
| `reading score` | Reading examination score |
| `writing score` | Writing examination score |

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## 🔍 Analysis Performed

### 1. Data Exploration
- Displayed the first and last rows of the dataset.
- Checked the number of rows and columns.
- Inspected column names and data types.
- Generated descriptive statistics.
- Checked for missing values.

### 2. Statistical Analysis
Calculated important statistical measures for mathematics, reading, and writing scores:

- Mean
- Median
- Mode
- Standard deviation
- First quartile (Q1)

### 3. Total Score Calculation

Calculated each student's total score by adding the mathematics, reading, and writing scores.

```python
df["Total Score"] = (
    df["math score"]
    + df["reading score"]
    + df["writing score"]
)
```

### 4. Percentage Calculation

Calculated the student's overall percentage based on a maximum total score of 300.

```python
df["Percentage"] = (
    df["Total Score"] / 300
) * 100
```

### 5. Average Score Calculation

Calculated the average score across the three subjects for each student.

```python
df["Average Score"] = df[
    ["math score", "reading score", "writing score"]
].mean(axis=1)
```

### 6. Pass/Fail Classification

Classified students as Pass or Fail using a minimum score of 40 in each subject.

```python
df["Pass/Fail"] = (
    (df["math score"] >= 40) &
    (df["reading score"] >= 40) &
    (df["writing score"] >= 40)
).map({
    True: "Pass",
    False: "Fail"
})
```

### 7. Outlier Detection

Used the **Interquartile Range (IQR)** method to identify potential outliers in mathematics scores.

The method calculates Q1, Q3, and IQR, then determines the lower and upper boundaries for detecting outliers.

```python
Q1 = df["math score"].quantile(0.25)
Q3 = df["math score"].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

math_outliers = df[
    (df["math score"] < lower) |
    (df["math score"] > upper)
]
```

## 🎯 Project Objectives

- Understand and inspect student performance data.
- Apply descriptive statistics to examination scores.
- Calculate total, average, and percentage scores.
- Classify students based on subject-wise passing criteria.
- Identify potential outliers using the IQR method.
- Develop practical Python data analysis skills.

## 💡 Key Learnings

- Loading and exploring CSV datasets using Pandas.
- Handling and inspecting missing values.
- Calculating descriptive statistics.
- Creating new columns using calculated values.
- Applying conditional logic for classification.
- Detecting potential outliers using statistical techniques.

## 👨‍💻 Author

**Samrabinson P**

BCA Student | Aspiring Data Analyst & Software Developer
