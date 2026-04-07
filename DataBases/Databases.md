# 🗄️ Databases

Links: [[Relational Databases]]

Tags: #database #backend #data #concept

---
## 🌐 1. What is a Database?

> A **database** is a structured system used to **store, organize, and retrieve data efficiently**

---
## 🧠 2. Core Idea

```text
Application ↔ Database → Data
```

- Your app **reads data** (SELECT)
- Your app **writes data** (INSERT, UPDATE, DELETE)
- The database ensures:
    - structure
    - consistency
    - performance

---
## 📦 3. Why Databases Exist

Without databases:

- Data would be messy (files everywhere)
- No efficient searching
- No relationships between data
- No scalability

With databases:

- Fast queries
- Structured storage
- Data integrity
- Multi-user access

---
## 🧱 4. Basic Concepts

### 📊 Tables

- Data is stored in **tables**
- Like spreadsheets

|id|name|age|
|---|---|---|

### A) 🧬 Rows

- One record (one item) 

### B) 🧾 Columns

- Attributes (features)

### C) 🔑 Primary Key

> Unique identifier for each row

- Example: `id`

### D) 🔗 Relationships

- Tables can be connected

Types:

- 1 → 1
- 1 → many
- many → many

---
## ⚙️ 5. What You Can Do With Databases

- Store user data
- Store application data
- Run analytics
- Power APIs
- Train ML models

---
## 🔄 6. How Databases Fit in Backend

```text
Frontend → API (FastAPI/Flask) → Database
```

Flow:

1. User sends request
2. API processes it
3. Query database
4. Return result

---
## 🧰 7. Types of Databases

## 🟦 7A. Relational Databases

Links: [[Relational Databases]]

> Store data in **tables with relationships**

### 🧠 Core Idea

```text
Structured data + relationships
```

### 📊 Characteristics

- Tables (rows + columns)
- Schema (fixed structure)
- Relationships between tables
- Uses **SQL**

### 🔗 Example

```text
Users Table
id | name

Orders Table
id | user_id
```

👉 `user_id` links to `Users.id`

### ✅ Advantages

- Strong structure
- Data integrity
- Powerful queries (JOIN, GROUP BY)

### ❌ Disadvantages

- Less flexible
- Harder to scale horizontally

### 🧰 Examples

- PostgreSQL
- MySQL
- SQLite

## 🟩 7B. NoSQL Databases

Links: [[NoSQL Databases]]

> Store data in **flexible, non-tabular formats**

### 🧠 Core Idea

```text
Flexible structure (schema-less)
```

### 📦 Types

#### 1. Document (JSON-like)

- MongoDB

#### 2. Key-Value

- Redis

#### 3. Column-based

- Cassandra

#### 4. Graph

- Neo4j

### ✅ Advantages

- Flexible schema
- Easy to scale
- Good for large/unstructured data

### ❌ Disadvantages

- Less strict structure
- Complex queries harder

---

## ⚖️ 8. Relational vs NoSQL

|Feature|Relational|NoSQL|
|---|---|---|
|Structure|Fixed schema|Flexible|
|Query Language|SQL|Varies|
|Relationships|Strong|Weak/implicit|
|Scaling|Vertical|Horizontal|

---
## 🔗 9. Important Related Concepts

### 🟦 SQL

> Language used to query relational databases

- SELECT
- INSERT
- UPDATE
- DELETE

### 🟪 ORM

> Allows you to interact with a database using code instead of SQL

```text
Python → ORM → SQL → Database
```

### 🟫 SQLite

> A lightweight relational database stored in a file

---

## 🧠 10. Mental Model (VERY IMPORTANT)

```text
Database = Storage
SQL = Language
ORM = Translator
API = Messenger
```

---

## 🚀 11. Big Picture

```text
User → Frontend → API → Database → Data
```

---

## 🧩 12. Where This Fits in Your Learning

- Backend development → CORE
    
- Data engineering → CORE
    
- Machine learning → DATA SOURCE
    
- Deployment → REQUIRED
    

---

## 🔥 13. BeCode Insight

You don’t just “learn databases”

You learn:

```text
How data flows through systems
```
