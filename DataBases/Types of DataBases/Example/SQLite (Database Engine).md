Links: [[SQLite3]]

Tags: #concept #database #sqlite #backend

---
## 🌐 1. What is SQLite?

SQLite is: 

> A **lightweight relational database engine** that stores data in a single file 

---
## 🧠 2. Core Idea

> SQLite is the system that **stores data and executes SQL queries**

- It understands SQL
- It manages tables
- It returns results

---
## 📦 3. How Data is Stored

SQLite stores everything in a file: 

`data.db`

Inside that file:
- tables
- rows
- columns

---
## ⚙️ 4. What SQLite Does

SQLite is responsible for: 
- creating tables
- storing data
- executing SQL queries
- returning results

### Example
```sql
CREATE TABLE users (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER
);
```
👉 SQLite creates and manages this table

---
## 🔗 5. Relationship with SQL

> SQL is the language, SQLite is the engine 

`SQL` → instructions
`SQLite` → executes them

---
## 🛠 6. How to Use SQLite

SQLite is usually accessed through: 

### A) Python (`sqlite3`)
```python
import sqlite3

conn = sqlite3.connect("data.db")
cursor = conn.cursor()
```

### B) ORM (e.g. SQLAlchemy)

```python
engine = create_engine("sqlite:///data.db")
```

### C) GUI Tools 
- DB Browser for SQLite
👉 used to inspect and explore the database visually

---
## 🚀 7. Why SQLite is Useful

- No server required
- Easy to set up
- Perfect for learning
- Good for small to medium projects
- Used in many real applications

---
## 8. 🔄 Where SQLite fits
```text
						   Python / App
								↓
						  sqlite3 / ORM
								↓
							   SQL
								↓
						SQLite (database engine)
								↓
						Data stored in file
```

---
## ⚠️ 9. Limitations

- Not ideal for high-traffic applications (many concurrent users)  
- Limited scalability compared to PostgreSQL / MySQL  
- No advanced features like distributed systems or clustering

