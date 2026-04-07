Links: [[ThreadPoolExecutor]]
  
Tags: #python #concurrency #async #backend #performance 

---
## ⚡ 1. What is Async (Asynchronous Programming)?  
  
> A way to run tasks without blocking the program while waiting for results  
  
👉 Instead of waiting → the program continues doing other work  
  
---
## 🧠 2. Core Idea  
  
```text  
Blocking (normal):  
Request → wait → next request  
  
Async (non-blocking):  
Request → (waiting...) → do other tasks → handle result when ready
```
👉 You don’t waste time waiting

---
## 🔑 3. Key Concept (VERY IMPORTANT)

### 🟦 I/O Bound Tasks

Async is mainly used for:

- API calls
- web scraping
- file reading

👉 Because these tasks spend most of their time **waiting**

---
## 🔄 4. Blocking vs Non-Blocking

- **Blocking** → stops program until done
- **Non-blocking** → allows program to continue

👉 Async = non-blocking

---
## 🧱 5. Core Keywords

### 🟦 async

Defines an asynchronous function:
```python
async def fetch():
    pass
```

### 🟩 await

Waits for a result **without blocking the program**:
```python
await fetch()
```
👉 Allows other tasks to run while waiting

---
## 🧰 6. Basic Example

```python
import asyncio

async def task():
    print("Start")
    await asyncio.sleep(1)
    print("End")

asyncio.run(task())
```
👉 `sleep()` is non-blocking here

---
## 🌐 7. Real Example (Async Web Requests)

```python
import aiohttp
import asyncio

urls = [
    "https://example.com",
    "https://example.org",
    "https://example.net"
]

async def fetch(session, url):
    async with session.get(url) as response:
        return response.status

async def main():
    async with aiohttp.ClientSession() as session:
        tasks = [fetch(session, url) for url in urls]
        results = await asyncio.gather(*tasks)
        print(results)

asyncio.run(main())
```
👉 All requests happen concurrently

---
## 🚀 8. Async vs ThreadPoolExecutor

### 🟦 ThreadPoolExecutor

- uses threads
- easier to use
- good for small/medium tasks

### 🟩 Async

- no threads (event loop)
- more efficient
- better for large-scale I/O

---
## ⚠️ 9. Trade-offs

- harder to understand
- requires async-compatible libraries (aiohttp)
- debugging is more complex

---
## 🔗 10. Where it fits

```text 
								 Request Handling 
										↓
							Async / ThreadPoolExecutor 
										↓
								Concurrent Requests 
										↓
							 Web Scraping / API Calls 
										↓
								  Data Extraction
```

---
## 🧠 11. Mental Model

> "While waiting, do something else"

- normal code = wait → do
- async code = start → switch → return later

> [!important]  
> Async is the most efficient way to handle many I/O operations in Python

