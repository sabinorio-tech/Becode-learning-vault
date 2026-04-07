Links: [[Threads]]
  
Tags: #python #concurrency #backend #performance #tool  
  
---  
## ⚡ 1. What is ThreadPoolExecutor?  
  
> A tool in Python that allows you to run multiple tasks concurrently using threads  
  
👉 Part of the `concurrent.futures` module  
  
---  
## 🧠 2. Core Idea  
  
Instead of doing tasks one by one:  
  
```text  
Task → wait → Task → wait
```

You use a pool of workers:

```text 
Worker 1 → Task  
Worker 2 → Task  
Worker 3 → Task  
```
👉 Tasks run concurrently → faster execution

---
 ## 🧱 3. How It Works

1. Create a pool of threads
2. Assign tasks to the pool
3. Threads execute tasks in parallel
4. Collect results

---
## 🧰 4. Basic Usage

```python
from concurrent.futures import ThreadPoolExecutor

def task(x):
    return x * 2

with ThreadPoolExecutor(max_workers=5) as executor:
    results = executor.map(task, [1, 2, 3, 4, 5])

print(list(results))
```
👉 `max_workers` = number of threads running at the same time

---
## 🌐 5. Real Example (Web Requests)

```python
import requests
from concurrent.futures import ThreadPoolExecutor

urls = [
    "https://example.com",
    "https://example.org",
    "https://example.net"
]

def fetch(url):
    response = requests.get(url)
    return response.status_code

with ThreadPoolExecutor(max_workers=3) as executor:
    results = executor.map(fetch, urls)

print(list(results))
```
👉 Multiple requests sent at the same time

---
## 🔄 6. map() vs submit()

### 🟦 map()

- simpler
- returns results in order

```python
executor.map(func, iterable)
```

### 🟩 submit()

- more control
- returns Future objects

```python
futures = [executor.submit(fetch, url) for url in urls]

for future in futures:
    print(future.result())
```
👉 Use `submit()` when you need flexibility

---
## ⚠️ 7. When to Use It

✅ Good for:

- API calls
- Web scraping
- File I/O

❌ Not good for:

- heavy CPU tasks (use multiprocessing instead)

---
## 🚀 8. Why it matters

- speeds up data extraction massively
- simple way to implement concurrency
- widely used in real-world pipelines

---
## ⚠️ 9. Common Mistakes

- too many threads → blocked / rate limited
- no timeout handling in requests
- ignoring errors inside threads
- using it for CPU-heavy tasks

---
## 🔗 10. Where it fits

```text 
								 Request Handling 
										↓
								ThreadPoolExecutor 
										↓
								Concurrent Requests 
										↓
							 Web Scraping / API Calls 
										↓
								  Data Extraction
```

---
## 🧠 11. Mental Model

> "Hire multiple workers to do the same job faster"

- threads = workers
- tasks = jobs
- executor = manager

> [!important]  
> ThreadPoolExecutor is the easiest way to add concurrency to Python programs

