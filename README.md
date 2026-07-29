# 🧹 Customer Data Cleaning & Statistical Quality Assessment

## 📌 Project Overview

A professional **data cleaning and statistical quality assessment pipeline using Python**.

This project applies statistical methods to identify:

* 🔍 Missing values
* 🔁 Duplicate records
* ⚠️ Invalid observations
* 📊 Statistical outliers
* 🧾 Transaction inconsistencies
* ✅ Business-rule violations

Suspicious records are **flagged instead of deleted** to preserve information quality.


# 🎯 Objectives

✅ Improve data quality
✅ Detect abnormal observations
✅ Apply statistical validation methods
✅ Create quality-control indicators
✅ Export cleaned datasets (CSV / Excel)


```bash
pip install pandas numpy scipy scikit-learn openpyxl
```


# 📊 Statistical Data Cleaning Methods

## 1️⃣ Missing Value Analysis

Missing values were evaluated by:

```python
df.isnull().sum()

df.isnull().mean()*100
```

📌 Missing percentage helps decide whether to:

* Impute
* Investigate
* Remove


## 2️⃣ Median Imputation

Missing numerical values were replaced using:

```python
df["age"] = df["age"].fillna(
    df["age"].median()
)
```

Why median?

[
Median = Q_2
]

The median is robust against:

* Skewed distributions
* Extreme values



## 3️⃣ Duplicate Detection

```python
df.duplicated().sum()

df.drop_duplicates(
    subset="customer_id"
)
```

📌 Prevents double counting and statistical bias.



## 4️⃣ Data Validation & Type Correction

Date conversion:

```python
df["signup_date"] = pd.to_datetime(
    df["signup_date"],
    errors="coerce"
)
```

Categorical variables:

```python
df["category"].astype("category")
```

---

## 5️⃣ Invalid Value Detection

Example: Age validation

```python
invalid_age = df[
(df.age < 18) |
(df.age > 100)
]
```

📌 Domain rules prevent unrealistic values.


# 📈 Outlier Detection

## IQR Method

[
IQR = Q_3-Q_1
]

[
Lower=Q_1-1.5(IQR)
]

[
Upper=Q_3+1.5(IQR)
]

```python
Q1=df["age"].quantile(0.25)

Q3=df["age"].quantile(0.75)

IQR=Q3-Q1
```

📌 Suitable for skewed data and extreme observations.


## Z-Score Method

[
Z=\frac{x-\mu}{\sigma}
]

```python
from scipy.stats import zscore

df["z_age"]=zscore(df["age"])
```

Outlier criterion:

[
|Z|>3
]

📌 Appropriate for approximately normal distributions.


# 🧾 Transaction Consistency Check

Expected spending:

[
Expected\ Total =
Purchase\ Count \times Average\ Order\ Value
]

```python
df["expected_total"] = (
df.purchase_count *
df.avg_order_value
)

df["difference"] = abs(
df.expected_total -
df.total_spending
)
```

📌 Detects inconsistent transactions without losing data.


# ✅ Business Rule Validation

Checked rules:

✔ purchase_count ≥ 0
✔ avg_order_value ≥ 0
✔ total_spending ≥ 0
✔ 1 ≤ satisfaction_score ≤ 5
✔ returned_items ≤ purchase_count
✔ signup_date ≤ current date


# 🚩 Data Quality Flags

Generated indicators:

* `total_spending_flag`
* `return_flag`
* `future_signup_flag`
* `overall_data_status`

Status:

| Status          | Meaning                |
| --------------- | ---------------------- |
| ✅ Valid         | Passed validation      |
| ⚠️ Needs Review | Quality issue detected |


# ▶️ Run Project

```bash
python customer_project.py
```

or

```bash
py customer_project.py
```


# 📌 Statistical Approach

> Statistical methods were used to detect anomalies, not automatically remove them.
> Missing values were estimated using robust median imputation.
> Outliers were identified using IQR and Z-score methods.
> Suspicious records were preserved with quality flags for further analysis.


## 👩‍💻 Author

**Mahdiyeh Mirzaei**
