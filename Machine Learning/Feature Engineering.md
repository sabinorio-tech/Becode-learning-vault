Links: [[Model]]

Tags: #ml #feature-engineering #data #core #model 

---
## 🌐 1. What is Feature Engineering?

Feature Engineering is:

> The process of transforming raw data into meaningful inputs (features) for machine learning models

You take existing data and:

- clean it
- transform it
- create new variables

> [!important]  
Feature engineering depends heavily on clean data.  
Poor data quality leads to misleading or useless features.


---
## 🧠 2. Core Idea

> Better features → better model performance

Models do NOT learn from raw data  
👉 They learn from **features you provide**

---
## 🔄 3. Where it Fits

```text
						        Raw Data
								   ↓
						 EDA (understand patterns)
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

Combine or derive new information:

```python
df["price_per_m2"] = df["price"] / df["living_area"]
```
👉 More informative than raw features

### 🧮 B) Transformations

Change how data is represented:

```python
df["log_price"] = np.log(df["price"])
```
👉 Helps with skewed data

### 🔢 C) Encoding Categorical Data

Convert categories → numerical form:

```python
df = pd.get_dummies(df, columns=["property_type"])
```
👉 Required for most ML models

### ⚠️ D) Handling Missing Values

```python
df["garden_area"].fillna(0, inplace=True)
```
👉 Prevents errors and bias

### 📏 E) Scaling / Normalization

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df[["living_area"]] = scaler.fit_transform(df[["living_area"]])
```
👉 Makes features comparable

---
## 🧱 5. Real Examples

### 🏠 Immo Project

```python
df["outdoor_area"] = df["garden_area"] + df["terrace_area"]
```
👉 Combines useful signals

```python
df["distance_brussels"] = ...
```
👉 Adds location intelligence

### 🍷 Wine Project (SQL)

```sql
SELECT
    ROUND(SUM(ratings_average * ratings_count) / SUM(ratings_count), 2) 
    AS weighted_avg_rating
FROM wines  
WHERE ratings_count > 50  
GROUP BY country;
```
👉 Feature engineering can happen **before Python (in SQL)**

---
## 🔗 6. Relationship with EDA

EDA tells you:

- what matters
- what is broken
- what needs transformation

👉 Feature Engineering applies those insights

---
## ⚠️ 7. Common Mistakes

- Using raw data without transformation ❌
- Creating features using target variable (data leakage) ❌
- Ignoring missing values ❌
- Creating too many useless features ❌

---
## 💡 8. Core Insight

Feature Engineering is:

> Making data easier for the model to learn from

---
## 🧠 9. Mental Model

```text
Raw data → Transform → Signal → Model
```

---
## 🚀 10. Why It Matters

- Often more important than the model itself
- Improves accuracy and generalization
- Reveals hidden patterns

---
## 🔗 11. Key Idea

> Better features > more complex models



