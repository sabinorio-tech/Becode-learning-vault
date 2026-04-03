
Links: [[Relational Databases]]

Tags: #database #backend #architecture #theory

---
## 🧠 1. The Big Picture

```text 
			User → Frontend → Backend (Python)
									 ↓
						  Query Layer (ORM / sqlite3)
									 ↓
									SQL
									 ↓
			   	      Database Engine (SQLite/PostgreSQL)
									 ↓
							   Tables (data)
```

---
## 🧩 2. Two Ways to Talk to a Database

### A) Raw SQL (sqlite3)

> You write SQL manually and send it through Python

```python 
cursor.execute("SELECT * FROM users")
```

✔️ Direct  
✔️ Full control  
❌ More verbose

### B) ORM (SQLAlchemy)

>You write Python objects → ORM translates it into SQL

```python
session.query(User).all()
```

✔️ Cleaner  
✔️ More scalable  
❌ Abstract (can hide SQL logic)

---
## 🔗 3. What Actually Happens Under the Hood

Even with ORM:

	Python code → ORM → SQL → Database → Result

👉 SQL is ALWAYS there

---
## ⚙️ 4. Role of Each Component

| Component | Role                   |
| --------- | ---------------------- |
| Database  | Stores data            |
| SQL       | Language to query data |
| sqlite3   | Python connector       |
| ORM       | Abstraction over SQL   |

---
## 🧠 5. Mental Model

> With sqlite3 → “I write SQL in Python”  
> With ORM → “I write Python that becomes SQL”

---
## 🌍 6. Why Applications Use Databases

> Applications need to **store, retrieve, and reuse data efficiently**

Without databases, you would:

- lose data when the app stops
- store everything in memory or CSVs
- struggle with large datasets

>[!tip] 💡 Key idea:
> The database is the **memory of the application**

---
## 🔄 6.1 Where This Fits in Backend

```
Client request
↓
API (Flask / FastAPI)
↓
Business logic
↓
Query layer (ORM / SQL)
↓
Database
↓
Return data → Response
```

👉 Database interaction happens inside backend logic

---
## ⚙️ 7. CRUD Operations

All database interactions are based on CRUD:

- Create → INSERT
- Read → SELECT
- Update → UPDATE
- Delete → DELETE

👉 Every application uses these operations

---
## 🧪 8. Example (User Login)

```text
								User logs in
									↓
						 Backend receives request
									↓
							Query database:
					SELECT * FROM users WHERE email = ...
									↓
							   Check password
									↓
							  Return response
```

