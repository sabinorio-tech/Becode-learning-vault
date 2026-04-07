Links: 
- [[Data Sources]]

Tags: #data #extraction #concept

---
## 🌐 1. What is Data Extraction?

> The process of **retrieving raw data from a source** so it can be processed and used for analysis, storage, or applications

---
## 🧠 2. Core Idea

> Data lives somewhere → you extract it → then you use it

```text
Database / API / File → Extraction → Usable Data
```


---
## 📦 3. Data Sources

👉 See: [[Data Sources]]

Common sources include:

- Databases
- APIs
- Files
- Web pages (scraping)

---
## ⚙️ 4. Methods of Extraction

Different sources require different methods:
### 🟦 A) Databases

- SQL queries
- ORM

```sql
SELECT * FROM users;
```
  
### 🟩 B) Files

- File readers (pandas, built-in Python)

```python 
import pandas as pd

df = pd.read_csv("data.csv")
```

### 🌐 C) APIs

- HTTP requests

```python 
import requests

response = requests.get("https://api.example.com/data")
data = response.json()
```

### 🌍 D) Web Scraping

- HTML parsing

```python
from bs4 import BeautifulSoup
```

---
## ⚙️ 5. Extraction from Databases

### A) Using SQL 

```sql
SELECT *
FROM users
WHERE age > 18;
```

### B) Using Python(sqlite3)

```python
cursor.execute("""
		SELECT 
			*
		FROM 
			users
""")


rows = cursor.fetchall()
```

### C) Using ORM 

```python
session.query(user).all()
```

>[!tip] 
>All of these do the same thing -> Retrieve data from the database 

---
## 🔄 6. Types of Data Extraction (IMPORTANT)

### 🟦 Batch Extraction

- Extract data in chunks
- Example: daily export of database

### 🟩 Real-Time Extraction

- Continuous data flow
- Example: live API, streaming data
### 🟨 Incremental Extraction

- Only extract new/updated data
- Example: `WHERE updated_at > last_run`

👉 Used in production systems to **avoid reprocessing everything**

---
## 🚀 7. Where It Fits in the Workflow

```text 
								Data Source 
								    ↓
							 Data Extraction 
								    ↓
						Data Processing / Cleaning
								    ↓
							EDA (Exploration)
								    ↓
						    Feature Engineering
								    ↓
								  Model
```

---
## 🧠 8. Mental Model

> "Get the data before you understand it"

- Extraction = getting access
- EDA = understanding
- Cleaning = fixing

---
## ⚠️ 9. Common Mistakes

- Extracting too much data (inefficient queries)
- Not filtering (`WHERE`)
- Ignoring performance
- Mixing extraction with cleaning
- Not handling API limits or errors


