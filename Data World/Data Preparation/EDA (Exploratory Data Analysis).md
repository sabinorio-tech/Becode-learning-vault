
Links: 
- [[Data Processing]]

Tags: #concept #eda #data #analysis #python 

---
## 🌐 1. What is EDA?

EDA (Exploratory Data Analysis) is: 

> The process of exploring and understanding data before building models

You analyze data to: 
- Understand patterns 
- detect issues
- generate insights

---
## 🧠 2. Core Idea

> Ask questions → explore data → find insights

EDA helps you answer:

- What does the data look like?
- Are there patterns or trends?
- Are there outliers or errors?
- What features are important?

---
## 🔄 3. Where EDA Fits

```text
						  Database (SQLite)  
								↓  
						   SQL (extract)  
								↓  
						EDA (understand 🔍)  
								↓  
						Data Cleaning (fix 🧹)  
								↓  
					Feature Engineering (improve ⚙️)  
								↓  
							Model (ML)
```

---
## ⚙️ 4. Tools Used

- **SQL** → extract relevant data
- **pandas** → manipulate and analyze
- **[[Plotly]] / matplotlib** → visualize

---
## 🔍 5. Common EDA Tasks

### 📊 A) Summary Statistics

```python
df.describe()
```

👉 Mean, min, max, etc.

### 🔎 B) Group Analysis

```python
df.groupby("country")["ratings_average"].mean()
```

👉 Average rating per country

### ⚠️ C) Missing Values

```python
df.isna().sum()
```

👉 Check missing data

### 📈 D) Distributions

```python
df["ratings_average"].hist()
```

👉 Understand how values are spread

### 🔗 E) Relationships

```python
df.plot.scatter(x="ratings_count", y="ratings_average")
```

👉 Do more reviews = better rating?

---
## 🍷 6. Real Example 

### Step 1 — Extract data (SQL)

```sql
df = pd.read_sql_query("""
SELECT 
    country,
    ratings_average,
    ratings_count
FROM wines
WHERE ratings_count > 50;
""", conn)
```

### Step 2 — Analyze

```python
df.groupby("country")["ratings_average"].mean()
```

👉 Which countries have the best wines?

### Step 3 — Visualize

```python
import matplotlib.pyplot as plt

df["ratings_average"].hist()
plt.show()
```
👉 Distribution of ratings

---
## ⚠️ 7. Common Mistakes

- Skipping EDA before modeling ❌
- Ignoring missing values ❌
- Not checking outliers ❌
- Jumping straight into ML ❌

---
## 🧠 8. Mental Model

> EDA = “Understand your data before using it”

- Raw data → explored → insights

---
## 🚀 9. Why EDA Matters

- Improves model performance
- Prevents bad assumptions
- Helps discover patterns
- Essential in real-world data work

---
## 🔜 10. Next Step

- Feature Engineering
- Data Cleaning
- Machine Learning

> [!tip]  
> Good EDA = better models and better insights

