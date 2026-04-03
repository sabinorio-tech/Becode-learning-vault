Links:

Tags: #syntax #sql #join #database #query

---
## 🌐 1. What is a JOIN?

A JOIN is:

> Combining data from multiple tables using a related column

---
## 🧠 2. Core Idea

> Tables are connected using keys (usually Primary Key ↔ Foreign Key)

You JOIN them to:

- get complete information  
- avoid duplicate data  
- work across multiple tables  

---
## ⚙️ 3. Basic Syntax

```sql
SELECT columns
FROM 
	table1
	JOIN table2 ON table1.column = table2.column;
	
```

---
## 🔍 4. Example Tables

### Users

|user_id|name|
|---|---|
|1|Sean|
|2|Alex|
|3|John|
### Orders

|order_id|user_id|product|
|---|---|---|
|101|1|Laptop|
|102|2|Phone|
|103|1|Mouse|

### 🔗 A) INNER JOIN (most common)

→ intersection of both tables
```sql
SELECT 
    users.name,
    orders.product
FROM 
	users
	INNER JOIN orders ON users.user_id = orders.user_id;
```
👉 Only matching rows

| name | product |
| ---- | ------- |
| Sean | Laptop  |
| Alex | Phone   |
| Sean | Mouse   |

### ⬅️ B) LEFT JOIN

→ everything on the left + matches
```sql
SELECT 
    users.name,
    orders.product
FROM 
	users
	LEFT JOIN orders ON users.user_id = orders.user_id;
```
👉 All users, even if no orders

| name | product |
| ---- | ------- |
| Sean | Laptop  |
| Sean | Mouse   |
| Alex | Phone   |
| John | NULL    |
### ➡️ C) RIGHT JOIN

→ everything on the right + matches
```sql
SELECT 
    users.name,
    orders.product
FROM 
	users
	RIGHT JOIN orders ON users.user_id = orders.user_id;
```
👉 All orders, even if no user

### 🔄 D) FULL JOIN

→ everything from both sides
```sql
SELECT 
    users.name,
    orders.product
FROM 
	users
	FULL JOIN orders ON users.user_id = orders.user_id;
```
👉 All data from both tables

>[!caution] Note (SQLite)  
>
>- SQLite supports:  
>	- INNER JOIN 
>	- LEFT JOIN  
>
>- SQLite does NOT support: 
>	- RIGHT JOIN 
>	- FULL JOIN  
  
👉 You must simulate them manually

---
## 🧭 When to Use Each JOIN
  
- INNER JOIN  
	→ when you only want matching data  
  
- LEFT JOIN  
	→ when you want all main records + optional matches  
  
- RIGHT JOIN  
	→ rarely used (can swap table order instead)  
  
- FULL JOIN  
	→ when you want everything from both tables

---
## 5. 🔗 Real Example

Get wine name + country:
```sql 
SELECT  
	w.name,  
	c.name AS country  
FROM 
	wines w  
	JOIN regions r ON w.region_id = r.id  
	JOIN countries c ON r.country_code = c.code;
```

>[!important]
>- Always use `ON` to define the relationship
>- Column names can be the same → use table prefixes
>- JOIN combines data  
>- WHERE filters rows
> 	BUT:  
> 	JOIN type (INNER, LEFT) also affects which rows appear


---
## ❌ 6. Common Mistakes

- Forgetting ON ❌
- Joining on wrong column ❌
- Not understanding LEFT vs INNER ❌

---
## 🔜 7. Next Step

- Combine everything:
    - JOIN + GROUP BY + WHERE

> [!tip]  
> JOIN is what makes relational databases powerful