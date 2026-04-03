
Links: 
- [[ORM]] 
- [[Relational Databases]]
- [[Querying a Database (Python)]] 
- [[Data Extraction]]
- [[SQL - Execution Order]]

Tags: #sql #database #backend #data #language

---
## 🌐 1. What is SQL?

Structured Query Language is: 
	A language used to communicate with databases

It lets you: 
- `store` data
- `retrieve` data
- `update` data
- `delete` data

---
## 🧠 2. Core Idea

SQL works with: 

	Tables → Rows → Columns

### Example: USERS Table

| id  | name | age |
| --- | ---- | --- |
| 1   | Sean | 20  |
| 2   | Alex | 25  |

- **Table** -> `users`
- **Row** -> one entry (Sean)
- **Column** -> attribute (name, age)

---
## ⚙️ 3. Main SQL Operations (CRUD)

>[!important] 💡 CRUD = Create, Read, Update, Delete

### A) 🔍 READ (SELECT)

```sql
SELECT 
	*
FROM users;
```
👉 Get all data

```sql
SELECT
	*
FROM 
	users
WHERE
	age > 21;
```
👉 Filter data

### B) ➕ CREATE (INSERT)

```sql 
INSERT INTO 
	users (name, age)
VALUES ('John', 30); 
```
👉 Add new data

### C) ✏️ UPDATE

```sql 
UPDATE 
	users
SET 
	age = 26
WHERE 
	name = 'Alex'; 
```
👉 Modify existing data

### D) ❌ DELETE

```sql
DELETE FROM 
	users
WHERE 
	name = 'John';
```
👉 Remove data

---
## 4. SQL Execution Order 

> SQL is **written top → bottom**, but **executed in a different order**

```text 
1. FROM
2. JOIN
3. WHERE
4. GROUP BY
5. SELECT
6. ORDER BY
7. LIMIT
```

---
## 🔗 4. How SQL Fits in Real Projects

SQL is used in:
- 📊 Data analysis → querying datasets
- 🧠 Machine learning → loading training data
- 🌐 Web development → storing users, predictions, etc.
- 🏢 Real applications → almost always use databases

> [!example]  
User inputs house data → backend queries database → returns prediction

---
## 🚀 5. Why SQL Matters

- Used in almost every backend system
- Required for most data jobs
- Scales better than CSV files
- Essential for real-world projects

---
## 6.🧭 When to use SQL

Use SQL when:
- data is stored in a database
- you need to filter or analyze structured data
- working with backend systems or APIs
- querying large datasets efficiently

Do NOT use SQL when:
- data is very small → use Python lists / CSV
- working with unstructured data (text, images)

---
## 🧠 7. Mental Model

Think of SQL as:

> “Asking questions to your data”

- `SELECT` → “Show me…”
- `WHERE` → “Only if…”
- `INSERT` → “Add this…”
- `UPDATE` → “Change this…”
- `DELETE` → “Remove this…”

---
## 🔜 8. Next Steps

- Learn [[SQL – Filtering|filtering]] (`WHERE`, `AND`, `OR`)
- Learn [[SQL – Aggregation|aggregation]] (`COUNT`, `AVG`, `SUM`)
- Learn [[SQL – GROUP BY|grouping]](`GROUP BY`)
- Learn [[SQL – JOIN|joins]] (`JOIN`)

> [!tip]  
> This is where SQL becomes powerful 🚀