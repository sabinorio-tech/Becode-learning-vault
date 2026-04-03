Links: [[Flask]], [[FastAPI]]

Tags: #api

---
## 🌐 What is an API?

An API (Application Programming Interface) is:

> A way for systems to communicate using requests and responses over HTTP

>[!tip] Intuition
> Think of an API like a restaurant:
>
> - Client → you (customer)
> - Request → your order
> - Server → kitchen
> - Response → your food
>
> You don’t cook the food, you just ask for it.

---
## 🔗 1. Request-Response Cycle

An API works using:

		Client → Request → Server → Response → Client

- **Client** → browser, app, or program
- **Server** → Flask app
- **Request** → asks for something
- **Response** → returns data

---
## 🌍 3. HTTP (How APIs Communicate)

APIs use **HTTP** to communicate.

HTTP defines:

- Methods → GET, POST, PUT, DELETE
- Status codes → 200, 404, 500
- Headers → metadata about the request

> 👉 API = built on top of HTTP

---
## ⚙️ 4. API Endpoint

An endpoint is:

> A specific URL where an API can be accessed

### Example 

```python
@app.route("/predict", methods=["POST"])
def predict():
    return {"price": 300000}
```

Endpoint: 

		/predict

---
## 📦 5. Request Methods

### A) GET  
- Used to **get data**  
- No body (usually)  
- Example: opening a webpage  

### B) POST  
- Used to **send data**  
- Has a body (form, JSON)  
- Example: submitting a form  
  
> [!important]  
> GET = ask  
> POST = send

---
## 📤 6. Status Codes 

The server responds with a status code:

- **200** → Success
- **201** → Created
- **400** → Bad request (client error)
- **404** → Not found
- **500** → Server error

> 👉 These tell the client what happened

---
## 📦 7. JSON (Data Format)

Most APIs use **JSON** to send data:

```
{
  "price": 300000
}
```

> 👉 JSON is the standard format for API communication

---
## 🔁 8. API Flow (Concrete Example)

```text
							User clicks button 
									↓ 
					Frontend sends POST request (/predict) 
									↓ 
							Flask receives request 
									↓ 
						Backend processes logic (ML model) 
									↓ 
						  Returns JSON response 
									↓ 
						 Frontend displays result
````

---
## 🧠 9. API vs Flask vs FastAPI

> Flask is a tool used to create APIs


>[!important]  ⚠️ Important Distinction
>- **API** → concept (communication system)
>- **Flask / FastAPI** → tools to build APIs

Each route:

```python
@app.route("/something")
```

👉 is an API endpoint

---

>[!important] 💡 Core Insight
>
An API is just a system that:
**receives requests → processes them → returns responses**
