Links: [[Retry or Backoff Strategy]]
  
Tags: #data #http #backend #performance #reliability #concept

---
## 🌐 1. What is Rate Limiting?  
  
> Controlling how many requests are sent over time to avoid overwhelming a server  
  
👉 Prevents:  
- being blocked (403)  
- hitting limits (429)  
- server overload

---
## 🧠 2. Core Idea  
  
```text  
Too fast → blocked  
Controlled → stable
```
👉 Send requests at a **safe, controlled pace**

---
## ⚠️ 3. Why Rate Limiting Exists

Servers enforce limits to:

- protect resources
- prevent abuse (bots)
- ensure fair usage

Common response:

- **429 Too Many Requests**

---
## ⏱️ 4. Basic Rate Limiting (Delay)

```python
import time

for url in urls:
    requests.get(url)
    time.sleep(1)
```
👉 Simple but effective

---
## 🚀 5. With Concurrency (IMPORTANT)

Concurrency increases speed, BUT:

```text
Too many parallel requests → block
```
👉 You must control:

- number of workers (`max_workers`)
- request frequency

---
## 🔄 6. Rate Limiting + Retry (Best Practice)

When hitting limits:
```text
Request → 429 → wait → retry
```
👉 Combine with [[Retry or Backoff Strategy]]

---
## 🧰 7. Advanced Techniques

### 🟦 A) Fixed Delay

- wait same time between requests

### 🟩 B) Exponential Backoff

- increase delay after failures

### 🟨 C) Adaptive (advanced)

- adjust speed based on server response

---
## 📡 8. API Rate Limits

APIs often specify limits:

Examples:
- 100 requests / minute
- 1000 requests / hour

👉 Sometimes returned in headers:

- `X-RateLimit-Limit`
- `X-RateLimit-Remaining`

---
## ⚠️ 9. Common Mistakes

- sending too many concurrent requests
- ignoring 429 responses
- no delay or backoff
- assuming all sites allow scraping

---
## 🔗 10. Where it fits

```text
							 Request Handling 
									↓
							   Rate Limiting 
									↓
						   Retry / Backoff Strategy 
									↓
								Concurrency 
									↓
						   Data Extraction Pipeline
```

---
## 🧠 11. Mental Model

> "Go fast, but not too fast"

- speed = efficiency
- control = stability

> [!important]  
> Rate limiting protects your pipeline from getting blocked or banned

