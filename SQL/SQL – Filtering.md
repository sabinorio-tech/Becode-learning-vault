Links: [[SQL – GROUP BY]], [[SQL – JOIN]]

Tags: #syntax #sql #filtering #database #query

---
## 🌐 1. What is Filtering?

Filtering is:

> Selecting only specific rows based on a condition

Instead of getting all data, you narrow it down.

---

## 🧠 2. Core Idea

Use:

> Use `WHERE` to filter rows BEFORE any grouping or aggregation

---

## ⚙️ 3. Basic Syntax

```sql
SELECT 
	*
FROM 
	table_name
WHERE 
	condition;
```

---
## 🔍 4. Common Conditions

### A) Comparison operators 

```sql 
=      equal  
!=     not equal  
>      greater than  
<      less than  
>=     greater or equal  
<=     less or equal  
```

#### Example 
```sql 
SELECT 
	* 
FROM wines 
WHERE ratings_average > 4.5;
```
👉 Only high-rated wines
### B) AND / OR

```sql
SELECT 
	* 
FROM wines 
WHERE ratings_average > 4.5 AND country = 'France';
```
👉 Both conditions must be true

```sql
SELECT 
	* 
FROM wines 
WHERE country = 'France' OR country = 'Italy';
```
👉 At least one condition must be true

### C) IN 
```sql 
SELECT 
	*
FROM users
WHERE 
	country IN ('France', 'Italy');
```
👉 Shortcut for multiple ORs

### D) BETWEEN (range)
```sql 
SELECT 
	* 
FROM wines
WHERE 
	ratings_average BETWEEN 4.0 AND 4.5;
```
👉 Inclusive range

### E) LIKE (pattern matching)
```sql 
SELECT 
	*
FROM wines
WHERE 
	name LIKE 'Chateau%';
```
👉 Starts with "Chateau"

```sql 
SELECT 
	*
FROM wines
WHERE 
	name LIKE '%Reserve';
```
👉 Ends with "Reserve"

### F) NULL handling 
```sql
SELECT 
	*
FROM wines
WHERE 
	ratings_average IS NULL;
```

```sql 
SELECT 
	*
FROM wines
WHERE 
	ratings_average IS NOT NULL;
```

>[!important]  
You CANNOT use `= NULL`

---
## 🔗 5. Real Example

```sql 
SELECT 
	name, 
	ratings_average, 
	country 
FROM wines 
WHERE ratings_count > 50 AND ratings_average > 4.5;
```
👉 Get **reliable + high-rated wines**

---
## ⚠️ 6. Important Insight

> WHERE filters rows BEFORE GROUP BY

Example:

```sql
SELECT 
    country,
    AVG(ratings_average)
FROM wines
WHERE ratings_count > 50
GROUP BY country;
```
👉 Filter first → then group

---
## ❌ 7. Common Mistakes

- Using `= NULL` ❌
- Forgetting quotes for text ❌
- Mixing AND / OR without parentheses ❌

### ⚠️ Example mistake

```sql
WHERE 
	country = 'France' OR country = 'Italy' AND ratings_average > 4.5
```

👉 Wrong logic

### ✅ Correct

```sql
WHERE 
    (country = 'France' OR country = 'Italy')
    AND ratings_average > 4.5
```

---
## 🧠 8. Mental Model

> WHERE = "filter rows before doing anything else"

- Raw data → filtered → then processed

---
## 🔜 9. Next Step

- Combine:
    - WHERE + JOIN
    - WHERE + GROUP BY
    - WHERE + HAVING

> [!tip]  
> WHERE is used in almost every SQL query