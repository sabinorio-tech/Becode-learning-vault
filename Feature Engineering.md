Links: 
- [[EDA (Exploratory Data Analysis)]]  
- [[Data Cleaning]]  
- [[Model]]  
- [[Model Evaluation and Validation Concepts]]

Tags: #concept #feature-engineering #ml #data

---
## 🌐 1. What is Feature Engineering?

Feature Engineering is:

> The process of transforming raw data into useful features for machine learning models

You take existing data and:

- improve it
- transform it
- create new variables

---
## 🧠 2. Core Idea

> Better features → better model performance

Models don’t learn from raw data  
👉 They learn from **features you create**

---
## 🔄 3. Where it Fits

```text
						     Database / Data
								   ↓
							EDA (understand data)
								   ↓
							Feature Engineering 🔥
								   ↓
							  Model (ML)
								   ↓
							   Evaluation
```

---
## ⚙️ 4. Types of Feature Engineering

### 🔧 A) Creating New Features

Combine existing columns:

```python
df["price_per_m2"] = df["price"] / df["living_area"]
```
👉 More informative than raw price

### 🧮 B) Transformations

Change how data is represented:

```python
df["log_price"] = np.log(df["price"])
```
👉 Helps with skewed data

### 🔢 C) Encoding Categorical Data

Convert text → numbers:

```python
df = pd.get_dummies(df, columns=["property_type"])
```
👉 Required for ML models

### ⚠️ D) Handling Missing Values

```python
df["garden_area"].fillna(0, inplace=True)
```
👉 Avoids model errors

### 📏 E) Scaling / Normalization

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df[["living_area"]] = scaler.fit_transform(df[["living_area"]])
```

👉 Makes features comparable

---
## 5. Real Example (Your Projects)

### 🏠 Immo Project

```python
df["outdoor_area"] = df["garden_area"] + df["terrace_area"]
```
👉 Combines useful information

```python
df["distance_brussels"] = ...
```
👉 Location-based feature

### 🍷 Wine Project

```sql
SELECT
    ROUND( SUM(ratings_average * ratings_count) / SUM(ratings_count), 2) 
    AS weighted_avg_rating,
FROM wines  
WHERE ratings_count > 50  
GROUP BY country;
```
👉 Accounts for review reliability
👉 Feature Engineering can also be done directly in SQL (before loading data into Python)

---
## 🔗 6. Link with EDA

EDA tells you WHAT to do:

- “This feature is important”
- “This data is skewed”
- “There are missing values”

👉 Feature Engineering APPLY those insights

---
## ⚠️ 7. Common Mistakes

- Using raw data without transformation ❌
- Creating features using target variable (data leakage) ❌
- Ignoring missing values ❌
- Over-engineering too many features ❌

---
## 🧠 8. Mental Model

> Feature Engineering = “make data easier for the model to understand”

- raw data → transformed → useful signals

---
## 🚀 9. Why It Matters

- Improves model performance
- Makes patterns clearer
- Often more important than the model itself

---
## 🔜 10. Next Step

- [[Model]]
- [[Model Evaluation and Validation Concepts]]

> [!tip]  
> Better features > more complex models