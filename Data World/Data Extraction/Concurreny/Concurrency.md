Links: [[Threads]] [[Async]]
  
Tags: #data #performance #backend #concurrency  
  
---  
## ⚡ 1. What is Concurrency?  
  
> Managing multiple tasks at the same time to improve performance  
  
⚠️ Not always truly parallel (depends on CPU)  
  
---  
## 🧠 2. Core Idea

```text
Sequential:  
Request → wait → Request → wait  
  
Concurrent:  
Request → Request → Request → wait for all
```
👉 Instead of waiting for each request, you send many at once

---
## 🔑 3. Key Concept (VERY IMPORTANT)

### 🟦 I/O Bound vs CPU Bound

- **I/O bound** → waiting (network, disk)
- **CPU bound** → heavy computation

👉 Web scraping = **I/O bound**

👉 Concurrency helps because:

> while waiting for one request → you can send another

---
## 🔄 4. Blocking vs Non-Blocking

- **Blocking** → program waits until task finishes
- **Non-blocking** → program continues while waiting

👉 Async = non-blocking  
👉 Threads = partially blocking (but parallel-like)

---
## 🧱 5. Types of Concurrency

### 🟦 A) Threads

- multiple workers
- simple to use
- good for I/O tasks

👉 [[Threads]]
### 🟩 B) Async (advanced)

- non-blocking execution
- very efficient for many requests

👉 [[Async]]

---
## 🧰 6. Tools / Implementation

- ThreadPoolExecutor -> see [[Threads]] first
- `asyncio`, `aiohttp`

---
## 🚀 7. Example (Real Impact)

Without concurrency:
```text
10 requests × 1 second = 10 seconds
```

With concurrency:
```text
10 requests at once ≈ 1–2 seconds
```
👉 Huge speed improvement

---
## 🚀 8. Why it matters

- speeds up scraping
- scales data pipelines
- enables real-world data collection

---
## ⚠️ 9. Trade-offs

- too many requests → blocked (rate limits)
- harder debugging
- more complex code

---
## 🔗 10. Where it fits

```text
							 Request Handling 
								    ↓
							   Concurrency 
								    ↓
						Web Scraping / API Calls 
								    ↓
							  Data Extraction
```

---
## 🧠 11. Mental Model

> "Don’t wait → do something else while waiting"

- Sequential = slow but simple
- Concurrent = fast but complex

> [!important]  
> Concurrency is essential for scalable data extraction



