Links: [[SQLite (Database Engine)]]

Tags: #concept #sqlite3 #python #backend #database

---
## 🌐 1. What is sqlite3?

sqlite3: 

> A **Python module used to connect to and interact with SQLite databases**

---
## 🧠 2. Core Idea

> sqlite3 allows Python to **send SQL queries to SQLite and receive results**

- It acts as a bridge between Python and SQLite
- It executes SQL queries
- It returns data to Python

---
## 🔗 3. Relationship with SQLite

	Python → sqlite3 → SQLite → Data

- Python → your code
- sqlite3 → sends queries
- SQLite → executes them

---
## ⚙️ 4. How It Works

### Step 1 - Connect to database 
```python
import sqlite3

conn = sqlite3.connect("data.db")
```
👉 Opens (or creates) a database file
### Step 2 — Create a cursor

```python
cursor = conn.cursor()
```
👉 Object used to execute SQL queries and fetch results
### Step 3 — Execute SQL
```python
cursor.execute("SELECT * FROM users")
```
👉 Sends query to SQLite

### Step 4 — Get results
```python
rows = cursor.fetchall()
```
👉 Retrieves data

### Step 5 — Save changes
```python
conn.commit()
```
👉 Required for INSERT / UPDATE / DELETE

### Step 6 — Close connection

```python 
conn.close()
```
👉 Frees resources

---
## 📦 5. What sqlite3 Handles

- connecting to the database
- executing SQL queries
- fetching results
- committing changes

>[!hint] 
>
> sqlite3 is the tool Python uses to talk to SQLite

---
## 6. 🔄 Where sqlite3 fits

```markdown
Python (app)
    ↓
sqlite3 (connector)
    ↓
SQL
    ↓
SQLite (database engine)
```


---
## ⚠️ 6. Important Notes

- You must use SQL queries (`SELECT`, `INSERT`, etc.)
- Always call `commit()` after modifying data
- Always close the connection

---
## 🧠 7. Better Practice (Context Manager)

```python
with sqlite3.connect("data.db") as conn:
    cursor = conn.cursor()
    cursor.execute("SELECT * FROM users")
    rows = cursor.fetchall()
```
👉 Automatically:
- commits changes if no error  
- rolls back if an error occurs  
- closes the connection

---
## Mental Model

Think of sqlite3 as:

> A translator between Python and SQL

- Python speaks → sqlite3 translates  
- SQLite understands → returns data  