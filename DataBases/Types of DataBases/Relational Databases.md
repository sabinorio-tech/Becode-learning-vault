Links: [[SQL]], [[ORM]], [[SQLite (Database Engine)]]

Tags: #concept #database #relational

---
## 🌐 1. What is a Relational Database?

A relational database is:

> A database system that organizes data into related tables using keys and relationships

Data is organized in a structured way using:

- tables  
- rows  
- columns  

---

## 🧠 2. Core Idea

> Data is split into multiple tables and connected using relationships

Instead of one big table, you separate data:

### Example

#### Users Table

| user_id | name |
|--------|------|
| 1      | Sean |
| 2      | Alex |

#### Orders Table

| order_id | user_id | product |
|----------|--------|--------|
| 101      | 1      | Laptop |
| 102      | 2      | Phone  |

👉 The `user_id` connects both tables

---

## 🔗 3. Relationships

### A) One-to-Many (1 → N)

> One user can have multiple orders

- One → User  
- Many → Orders  
### B) One-to-One (1 → 1)

> One user has one profile
### C) Many-to-Many (N ↔ N)

> Many students ↔ many courses

👉 Requires a **junction table**
### Example: Many-to-Many

#### Students
| id | name |
|----|------|
| 1  | Sean |

#### Courses
| id | course |
|----|--------|
| 10 | Math |

#### Student_Course (junction table)
| student_id | course_id |
|------------|----------|
| 1          | 10       |


---
## 🧱 4. Keys (VERY IMPORTANT)

### 🔑 Primary Key (PK)

> Uniquely identifies each row in a table

Example:
- `user_id`
### 🔗 Foreign Key (FK)

> A reference to a primary key in another table

Example:
- `user_id` in Orders → links to Users

---
## 🧩 5. Why Use Relational Databases?

- Avoid duplicate data  
- Keep data organized  
- Make relationships clear  
- Efficient querying with SQL  

---
## 🧠 6. Mental Model

Think of it like:

> Multiple Excel sheets that are connected together

Instead of repeating data:
- you **reference it**

---
## 7.❗ Why Relational Databases Exist

Without relationships:

- data is duplicated  
- harder to update  
- inconsistent data  

Example:

If user name changes → must update everywhere ❌  

With relationships:

- data stored once  
- referenced everywhere  
- consistent and efficient ✅  

---
## 🔗 8. Connection with SQL

> SQL is the language used to interact with relational databases

- Database → structure  
- SQL → communication  

👉 You use SQL to:
- query tables  
- join tables  
- manipulate data  

---

## 🔜 9. Next Steps

- Learn [[SQL]]
- Learn how to connect tables using  `JOIN`

> [!tip]  
Understanding this makes SQL MUCH easier
