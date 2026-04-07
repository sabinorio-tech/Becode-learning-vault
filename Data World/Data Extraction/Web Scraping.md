Links: [[Concurrency]], [[Parsing]]

Tags: #data #scraping #requests #data-engineering

---
## 🌐 1. What is Web Scraping?

Web scraping is: 

> Extracting data from websites by sending HTTP requests and parsing HTML 

Used when: 
- No API is available  
- Data is only visible on web pages 

---
## 🧠 2. The Big Picture (Pipeline)

Web scraping always follows this pipeline:

```
Request → Parse → Extract → Clean → Structure
```
👉 This is the full workflow from raw HTML to usable data

---
## ⚙️ 3. Structure

### 🧱 Step 1: Request the page

**Goal:** Get raw HTML from the server

**Concepts:**

- `requests.get(url)` → returns a **Response object**
- `response.status_code` → check if request succeeded
- `response.text` → HTML string
- `response.json()` → only for APIs

👉 Uses HTTP

### 🧱 Step 2: Parse the HTML

**Goal:** Turn raw HTML into a searchable structure

**Concept:**

- `BeautifulSoup(response.text, "html.parser")`  
    → creates a **DOM tree**

**Mental model:**

```html
<html><body><p>Hello</p></body></html>
```

becomes:

```text
Tree
 └── body
     └── p
         └── "Hello"
```

### 🧱 Step 3: Locate elements

**Goal:** Find the elements you want

**Tools:**

- `find()` → first match
- `find_all()` → multiple matches
- CSS selectors (advanced)

### 🧱 Step 4: Extract data

**Goal:** Get actual values from elements

Examples:

```python
title.text
link.get("href")
```
👉 HTML → usable data

### 🧱 Step 5: Clean data

**Goal:** Fix messy or inconsistent data

Examples:

- remove whitespace
- convert strings → numbers
- handle missing values

👉 Part of Data Extraction

### 🧱 Step 6: Structure data

**Goal:** Organize into usable format

Examples:

- list of dictionaries
- pandas DataFrame

```python
data = [{"title": t.text} for t in titles]
```

### 🧱 Step 7: Store data

**Goal:** Save data for later use

Options:
- CSV
- JSON
- Database

---
## 🔐 4. Real-world Scraping Constraints

To avoid being blocked:

### Headers (User-Agent)

```python
headers = {"User-Agent": "Mozilla/5.0"}
requests.get(url, headers=headers)
```

### Cookies / Sessions

```python
session = requests.Session()
session.get(url)
```

### Rate Limiting

```python
import time
time.sleep(1)
```
👉 Simulate real user behavior

---
## ⚡ 5. Concurrency (Speed)

To scrape faster:

- Threads
- Async requests

```
Multiple requests → faster scraping
```

---
## 🧠 6. Core Insight

Web scraping transforms:

```
Unstructured HTML → Structured data
```

It is not just “getting data”, but:

- HTTP communication
- parsing structure
- handling real-world constraints
- cleaning and organizing data

👉 This is a **data engineering process**

---
## 🔗 7. Where it fits in your system

```text
								Data Extraction
									   ↓
								  Web Scraping
									   ↓
							 Data Processing / Cleaning
									   ↓
									  EDA
									   ↓
							    Feature Engineering
									   ↓
									 Model
```
👉 Scraping is part of the **data pipeline**, not the API

---
## 💡 Key Insight

Most of the difficulty in data science is not the model.

👉 It is:

- collecting data
- cleaning data
- structuring data