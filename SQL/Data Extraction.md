
Links: 
- [[EDA (Exploratory Data Analysis)]]
- [[Data Sources]]
- [[Notes/Web Scraping|Web Scraping]]
- [[Request Handling]]
- [[Concurrency]]
- [[Data Cleaning]]
- [[Data Validation (Cleaning Stage)]]


Tags: #data #analysis #cleaning #concept 

---
## 🌐 1. What is Data Extraction?

Data extraction is: 

> The process of **retrieving data from a source** so it can be used for analysis or applications

---
## 🧠 2. Core Idea

> Data lives somewhere -> you extract it -> then you use it 

> Like: 
> Database / API / File → Extraction → Usable Data

---
## 📦 3. Common Data Sources

### A) 🟦 Databases
- SQLite
- PostgreSQL

👉 Extract using:
- SQL queries
- ORM

### B) 🟩 Files

- CSV
- JSON

```python 
import pandas as pd

df = pd.read_csv("data.csv")
```

### C) 🌐 APIs

- Web services
- External data providers

```python 
import requests

response = requests.get("https://api.example.com/data")
data = response.json()
```

### D)🌍 Web Scraping

- HTML pages

```python
from bs4 import BeautifulSoup
```

---
## ⚙️ 4. Extraction from Databases

### A) Using SQL 

```sql
SELECT *
FROM users
WHERE age > 18;
```

### B) Using Python(sqlite3)

```python
cursor.execute("
		SELECT 
			*
		FROM 
			users
")


rows = cursor.fetchall()
```

### C) Using ORM 

```python
session.query(user).all()
```

>[!tip] All of these do the same thing: 
>
>Retrieve data from the database 

---
## 🔄 5. Where It Fits in the Workflow

Data Source → Data Extraction → Data Exploration → Cleaning → Analysis / ML

---
## 🧠 6. Mental Model

> "Get the data before you understand it"

- Extraction = getting access
- Exploration = understanding

---
## ⚠️ 7. Common Mistakes

- Extracting too much data (inefficient queries)
- Not filtering (`WHERE`)
- Ignoring performance
- Mixing extraction with cleaning