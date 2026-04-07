Links: - [[SQL - Execution Order]]

Tags: #sql #database #python #backend #eda #query 

---
## 🧠 1. The Big Picture

```text
Python
  ↓
[ JupySQL ]   → for notebooks / learning
[ sqlite3 ]   → for backend / apps
[ pandas ]    → for data analysis (EDA)
  ↓
 SQL
  ↓
SQLite (database)
```

---
## ⚙️ 2. Method 1 — JupySQL (Notebook SQL)

> Run SQL directly inside Jupyter 

### Setup 
```python
%load_ext sql
%sql sqlite:///data.db
```

### Query 
```sql 
%%sql
SELECT * FROM users;
```
### ✅ Use case

- learning SQL
- quick queries
- exercises
- exploring data
### ❌ Limitations

- not used in real applications
- no control over logic
- only works in notebooks

---
## 🐍 3. Method 2 — sqlite3 (Python Backend)

> Direct communication between Python and SQLite

### Example 
```python
import sqlite3

connexion = sqlite3.connect("data.db")
cursor = connexion.cursor()

cursor.execute("SELECT * FROM users")
rows = cursor.fetchall()

connexion.close()
```
### ✅ Use case

- backend development (Flask, FastAPI)
- APIs
- automation scripts

>[!tip] ⚠️ Key idea
>
> You must use `cursor.execute()` to run SQL

---
## 📊 4. Method 3 — pandas + SQL (Data Analysis)

> Combine SQL with DataFrames 

```python
import pandas as pd 

df = pd.read_sql_query("SELECT * FROM users", connexion)
```

### ✅ Use case

- data analysis
- cleaning datasets
- visualization (Plotly, matplotlib)

### 🔥 Why it's powerful

- SQL → filtering, grouping
- pandas → analysis, transformation
---
## 🔁 5. Same Query – 3 Ways

### 🟢 JupySQL
```sql
%%sql  
SELECT * FROM users;
```

### 🔵 sqlite3
```python
cursor.execute("SELECT * FROM users")

row = cursor.fetchall()
```

### 🟣 pandas
```python
df = pd.read_sql_query("SELECT * FROM users", connexion)
```

| Method  | Syntax           | Use case       |
| ------- | ---------------- | -------------- |
| JupySQL | `%%sql`          | learning / EDA |
| SQLite3 | `cursor.execute` | backend / apps |
| pandas  | `read_sql_query` | data analysis  |
|         |                  |                |

---
## 🧩 6. Where ORM fits

Without ORM:  

	Python → sqlite3 → SQL → SQLite  
  
With ORM:  

	Python → ORM → SQL → SQLite


>[!tip] 🧠 Idea
>
> ORM still uses SQL behind the scenes  
> You just don’t write it manually

---
## 🧠 7. When to Use Each

- **JupySQL**  
    → learning SQL, exercises
- **pandas + SQL**  
    → EDA, data analysis, ML projects
- **sqlite3**  
    → backend, APIs, automation
- **ORM**  
    → larger applications, cleaner code

---
## ⚠️ When NOT to use each

- JupySQL  
  → not for production apps

- sqlite3  
  → not ideal for large-scale systems (use PostgreSQL)

- pandas + SQL  
  → not for backend APIs

- ORM  
  → not for complex/optimized queries

---

>[!important] ## 🧠 Core Insight
> No matter the method, **you are always writing SQL**
> - JupySQL → raw SQL
> - sqlite3 → SQL inside Python
> - pandas → SQL inside function
> - ORM → SQL generated for you
>
> -> Tools don't replace SQL 
> -> They only change how you write it

---


- Learn [[SQL – Filtering|filtering]] (`WHERE`, `AND`, `OR`)
- Learn [[SQL – Aggregation|aggregation]] (`COUNT`, `AVG`, `SUM`)
- Learn [[SQL – GROUP BY|grouping]] (`GROUP BY`)
- Learn [[SQL – JOIN|joins]] (`JOIN`)