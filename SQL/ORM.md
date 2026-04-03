Links: [[SQLite (Database Engine)]]  

Tags: #backend #database #orm #concept 

---
## 🌐 1. What is an ORM?
👉 This is a **bridge concept** (VERY important for backend jobs)

ORM (Object Relational Mapping) is:
  
> A tool that lets you interact with relational databases using Python objects instead of writing raw SQL

---
## 🧠 2. Core Idea

> Tables → Python classes  
> Rows → Python objects  

---

## ⚙️ 3. Example (SQL vs ORM)

### 🟢 SQL

```sql
SELECT 
	* 
FROM users 
WHERE age > 21;
```

### 🟣 ORM (Python)
```python  
from sqlalchemy.orm import sessionmaker  
  
Session = sessionmaker(bind=engine)  
session = Session()
```

```python 
users = session.query(User).filter(User.age > 21).all()
```

👉 Same result  
👉 Different way of writing it

---
## 🧩 4. Mapping Concept

### Table -> Class 

```python
class User(Base):
    __tablename__ = "users"
```
### Columns -> Attributes 

```python

	id = Column(Integer, primary_key=True)
	name = Column(String)
	age = Column(Integer)
```

### Row → Object

```python
user = User(name="Sean", age=20)
```

---
### ⚙️ 5. CRUD with ORM

### Create
```python
new_user = User(name="Sean", age=20)
session.add(new_user)
session.commit()
```

### Read
```python
users = session.query(User).all()
```

### Update 
```python
user.age = 25  
session.commit()
```

### Delete
```python
session.delete(user)
session.commit()
```

---
## ⚖️ 6. ORM vs Raw SQL

|Feature|ORM 🟣|SQL 🟢|
|---|---|---|
|Ease of use|Easy|Harder|
|Control|Less|Full control|
|Readability|High|Medium|
|Performance|Slightly lower|Optimal|

---
## 🎯 7. When to Use ORM

- building APIs (Flask, FastAPI)
- working with models (User, Property, etc.)
- larger applications
- when code readability matters

---
## ⚠️ 8. When NOT to Use ORM

- very complex queries
- performance-critical queries
- heavy analytics (better with SQL + pandas)

---
## 🚀 9. Key Takeaway

Without ORM:  
Python → sqlite3 → SQL → Database  
  
With ORM:  
Python → ORM → SQL → Database

> ORM makes database interaction feel like working with Python objects  
> but SQL is always happening underneath

