Links: [[SQL – Filtering]], [[SQL – GROUP BY]], [[SQL – JOIN]]

Tags: #concept #sql #execution-order #database

---
## 🌐 1. What is SQL Execution Order?

SQL queries are:

> Written in one order, but executed in another

Understanding this explains:

- why some queries fail
- why filtering behaves differently
- how JOIN + GROUP BY + WHERE work together

---
## 🧠 2. Execution Order (REAL ORDER)

```
1. FROM
2. JOIN
3. WHERE
4. GROUP BY
5. HAVING
6. SELECT
7. ORDER BY
8. LIMIT
```

👉 This is how the database ACTUALLY runs your query

---
## ⚙️ 3. Example Query

```sql
SELECT 
    country,
    AVG(ratings_average) AS avg_rating
FROM wines
WHERE ratings_count > 50
GROUP BY country
HAVING AVG(ratings_average) > 4.3
ORDER BY avg_rating DESC;
```

## 🔍 4. Step-by-Step Execution

### 1️⃣ FROM

```sql
FROM wines
```

👉 Load the table

### 2️⃣ WHERE

```sql
WHERE ratings_count > 50
```

👉 Filter rows

💡 Only keep **reliable wines**

### 3️⃣ GROUP BY

```sql
GROUP BY country
```

👉 Split data into groups

- France group
- Italy group
### 4️⃣ HAVING

```sql
HAVING AVG(ratings_average) > 4.3
```

👉 Filter groups (NOT rows)
### 5️⃣ SELECT

```sql
SELECT country, AVG(...)
```

👉 Compute final values

### 6️⃣ ORDER BY

```
ORDER BY avg_rating DESC
```

👉 Sort results

### 7️⃣ LIMIT (optional)

```
LIMIT 5
```

👉 Keep only top results

---
## ⚠️ 5. IMPORTANT RULES

### Rule 1 — WHERE cannot use aggregation ❌

```sql
WHERE AVG(ratings_average) > 4.3
```

👉 ❌ Error

### ✅ Correct → use HAVING

```sql
HAVING AVG(ratings_average) > 4.3
```

### Rule 2 — SELECT happens AFTER GROUP BY

👉 That’s why:

```sql
SELECT country, ratings_average
FROM wines
GROUP BY country;
```

👉 ❌ Invalid

### Rule 3 — WHERE happens BEFORE GROUP BY

👉 So:

```sql
WHERE ratings_count > 50
```

👉 filters BEFORE grouping

---
## 🧠 6. Mental Model

Think of SQL as a pipeline:

```text
Raw data
   ↓
FROM → load data
   ↓
WHERE → filter rows
   ↓
GROUP BY → group data
   ↓
HAVING → filter groups
   ↓
SELECT → compute results
   ↓
ORDER BY → sort
   ↓
LIMIT → trim output
```

---
## 🔥 7. Why This Matters

Understanding execution order lets you:

- write correct queries
- debug errors
- combine JOIN + GROUP BY + WHERE correctly
- think like a database engine

---
## 🔗 8. Real Project Example

```sql
SELECT 
    c.name,
    ROUND(
        SUM(w.ratings_average * w.ratings_count) 
        / SUM(w.ratings_count), 
    2) AS weighted_avg_rating
FROM 
	wines w
	JOIN regions r ON w.region_id = r.id
	JOIN countries c ON r.country_code = c.code
WHERE w.ratings_count > 50
GROUP BY c.name
ORDER BY weighted_avg_rating DESC;
```

👉 Flow:

- JOIN tables
- filter reliable wines
- group by country
- compute weighted average
- sort results

---
## 🔜 9. Key Takeaway

> SQL is not executed top → bottom

👉 It follows a logical pipeline

Understanding this = **real SQL mastery**