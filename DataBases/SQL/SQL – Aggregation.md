Links: [[SQL – GROUP BY]], [[SQL – Filtering]]

Tags: #syntax #sql #aggregation #database #query

---
## 🌐 1. What is Aggregation?

Aggregation is:

> Summarizing data into a single value

Instead of returning rows, you return **computed results**

---
## 🧠 2. Core Idea

Use functions like:

- `COUNT()` → number of rows  
- `SUM()` → total  
- `AVG()` → average  
- `MIN()` → smallest value  
- `MAX()` → largest value  

---
## ⚙️ 3. Basic Syntax

```sql
SELECT 
	AGG_FUNCTION(column)
FROM table_name;
```

---
## 🔍 4. Example: retail_sales

| id  | name   | ratings_average | ratings_count | country |
| --- | ------ | --------------- | ------------- | ------- |
| 1   | Wine A | 4.5             | 120           | France  |
| 2   | Wine B | 4.2             | 80            | France  |
| 3   | Wine C | 4.7             | 200           | Italy   |
| 4   | Wine D | 4.1             | 60            | Italy   |

### A) COUNT 

```sql 
SELECT 
	COUNT(*) AS total_wines
FROM wines;
```
👉 Total number of wines

Output -> 4
## B) SUM 

```sql 
SELECT 
	SUM(ratings_count) AS total_reviews
FROM wines;
```
👉 Total number of reviews

Output -> 460

### C) AVG

```sql 
SELECT 
	AVG(ratings_average) AS avg_rating
FROM wines;
```
👉 Average rating across all wines

Output -> 4,38

### D) MIN / MAX 
```sql 
SELECT 
	MIN(ratings_average) AS lowest_rating, 
	MAX(ratings_average) AS highest_rating
FROM wines;
```
👉 Lowest and highest values

Output -> 4,1 - 4,7

---
## 🔗5. Filtering + Aggregation 

```sql 
SELECT 
	AVR(ratings_average) AS avg_rating
FROM wines
WHERE ratings_count > 100;
```
👉 Average rating for **reliable wines only**

Output -> 4.6

>[!example] 💡 Thinking process  
> Filter → aggregate

---
## ⚠️ 6. Important Rule

> You cannot mix aggregated and non-aggregated columns  
> unless you use GROUP BY

### Example

--- ❌ Wrong

```sql
SELECT 
    country,
    AVG(ratings_average)
FROM wines;
```
👉 ❌ Error / undefined behavior

--- ✅ Correct

```
SELECT 
    country,
    AVG(ratings_average)
FROM wines
GROUP BY country;
```

---
## 🔐 7. WHERE vs HAVING (IMPORTANT)

- `WHERE` → filters rows **before aggregation**
- `HAVING` → filters results **after aggregation**

### Example (HAVING)

```sql
SELECT 
    country,
    AVG(ratings_average) AS avg_rating
FROM wines
GROUP BY country
HAVING AVG(ratings_average) > 4.3;
```

👉 Only keep countries with high average rating

---
## ❌ 8. Common Mistakes

- Mixing aggregated and non-aggregated columns ❌
- Forgetting WHERE before aggregation ❌
- Thinking it returns rows (it doesn’t) ❌

---
## 🧠 9. Mental Model

> Aggregation = "compress data into one value"

- Many rows → one result

---
## 🔜 10. Next Step

- Combine:
	- Aggregation + GROUP BY
	- Aggregation + JOIN
	- Aggregation + HAVING

> [!tip]  
> Aggregation is the foundation of dashboards and data analysis

