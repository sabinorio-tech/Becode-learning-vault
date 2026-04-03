Links: [[SQL – Aggregation]], [[SQL – JOIN]]

Tags: #syntax #sql #groupby #database #query

---
## 🌐 1. What is GROUP BY?

GROUP BY is:

> Splitting data into groups and applying aggregation to each group

Instead of one result → you get **one result per category**

---

## 🧠 2. Core Idea

> GROUP BY turns one summary → into multiple summaries

- Split data into groups
- Apply aggregation (AVG, SUM, COUNT)
- Return one result per group

---

## ⚙️ 3. Basic Syntax

```sql
SELECT 
	column, AGG_FUNCTION(column)
FROM 
	table_name
GROUP BY column;
```

---
## 🔍 4. Example: retail_sales

|id|name|ratings_average|ratings_count|country|
|---|---|---|---|---|
|1|Wine A|4.5|120|France|
|2|Wine B|4.2|80|France|
|3|Wine C|4.7|200|Italy|
|4|Wine D|4.1|60|Italy|
### A) SUM per category

```sql 
SELECT 
    country, 
    AVG(ratings_average) AS avg_rating
FROM wines
GROUP BY country;
```
👉 Average wine rating per country

Output:

|country|avg_rating|
|---|---|
|France|4.35|
|Italy|4.40|
### B) COUNT per category 

```sql 
SELECT 
	country,
    COUNT(*) AS wine_count
FROM wines
GROUP BY country;
```
👉 Number of wines in each country

Output:

|country|wine_count|
|---|---|
|France|2|
|Italy|2|

---
## 🔗 5. GROUP BY + Filtering

```sql 
SELECT 
    country,
    AVG(ratings_average) AS avg_rating
FROM wines
WHERE ratings_count > 50
GROUP BY country;
```
👉 Only include **reliable wines**, then group


| Country | avg_rating |
| ------- | ---------- |
| France  | 4.35       |
| Italy   | 4.40       |

>[!example] 💡 Thinking process  
Filter  →  group →  aggregate

---
## 🔗 6. GROUP BY with multiple columns

```sql
SELECT 
    country,
    ratings_count,
    COUNT(*) AS wine_count
FROM wines
GROUP BY country, ratings_count;
```
👉 Group by **country + review volume**

|kind_of_business|sales|COUNT(*)|
|---|---|---|
|Book stores|100|1|
|Book stores|200|1|
|Hobby stores|150|1|
|Sporting goods stores|300|1|

---
## ⚠️ 7. Important Rule

> Every column in SELECT must be:
> 	- either in GROUP BY
> 	- or inside an aggregation function

### Example

❌ Wrong
```sql 
SELECT 
    kind_of_business,
    sales
FROM retail_sales
GROUP BY kind_of_business;
```
👉 ❌ Error / undefined behavior

✅ Correct
```sql
SELECT 
    kind_of_business,
    SUM(sales)
FROM retail_sales
GROUP BY kind_of_business;
```

---
## 🔐 8. WHERE vs HAVING (IMPORTANT)

- `WHERE` → filters rows **before grouping**
- `HAVING` → filters groups **after grouping**

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
## ❌ 9. Common Mistakes

- Forgetting GROUP BY when using aggregation ❌
- Selecting columns not in GROUP BY ❌
- Confusing WHERE and HAVING ❌

---
## 🧠 10. Mental Model

> GROUP BY = "split → apply → combine"

- Split data into groups
- Apply aggregation
- Combine results

---
## 🔜 11. Next Step

- Learn [[SQL – JOIN|joins]]

> [!tip]  
> GROUP BY is used constantly in data analysis and dashboards