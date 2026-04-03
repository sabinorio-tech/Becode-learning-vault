
Links: [[API Fundamentals]], [[Flask]], [[Deployment Pipeline]], [[Docker]], [[Render]]

Tags: #webdev #api #framework #backend

---
## 🌐 1. What is FastAPI?

FastAPI is a Python web framework designed specifically for building APIs quickly and efficiently.

It allows you to:  
- receive HTTP requests  
- process data  
- return responses (usually JSON)

> [!important] 💡 Core Idea  
FastAPI defines **API behavior**, while a server (like Uvicorn) runs it.

---
## ⚙️ 2. What it is used for? 

FastAPI is mainly used to: 

- build API's quickly 
- serve machine learning models 
- create backend services 
- handle requests and return data

>[!Example] 
> User sends house features -> API receives data -> model predicts price -> API returns result

---
## 🚀 3. Why FastAPI is popular

FastAPI is popular because it is: 
- fast
- modern
- easy to write
- uses Python type hints 
- validates input automatically
- generates API docs automatically

---
## 🆚 4. FastAPI vs Flask

Both are Python web frameworks. 

### A) Flask 
- simpler and more flexible  
- good for learning and web apps  
- manual handling of validation

### B) FastAPI 
- API-first design  
- uses type hints  
- automatic validation  
- automatic documentation

---
## 🔄 5. How it works  
  
1. Client sends HTTP request  
2. FastAPI matches the route  
3. Python function runs  
4. Response is returned as JSON

---
## 🧱 6. Basic Example  
  
```python  
from fastapi import FastAPI  
  
app = FastAPI()  
  
@app.get("/")  
def home():  
	return {
		"message": "Hello from FastAPI"
	}
```

### 📥 6.1 Request Body (Validation)
```python
from pydantic import BaseModel  
  
class House(BaseModel):  
size: int  
rooms: int  
  
@app.post("/predict")  
def predict(house: House):  
return {"price": house.size * 1000}
```
👉 FastAPI automatically:

- validates input
- converts JSON → Python object

---
## 📚 7. Automatic Documentation

FastAPI generates docs automatically:

- `/docs` → Swagger UI
- `/redoc` → alternative UI

👉 You can test endpoints directly

---
## 🔍 8. Path & Query Parameters

### Path parameter:
```python
@app.get("/items/{item_id}")  

def get_item(item_id: int):  
    return {"id": item_id}
```
### Query parameter:

```python
@app.get("/search")  

def search(q: str):  
    return {"query": q}
```

---
## ▶️ 9. Running FastAPI

Run using Uvicorn:
```bash
uvicorn app:app --reload
```
- Uvicorn → web server
- FastAPI → framework

---
## 🧱 10. Where it fits in deployment?

						FastAPI is the framework layer. 

Flow: 
```text
							   Code / Model  
									↓  
								 FastAPI  
									↓  
								 Uvicorn  
									↓  
								  Docker  
									↓  
								  Render  
									↓  
								 Live API
```


---
## 🧠 Core Idea

FastAPI allows you to define API endpoints in Python that:
- receive HTTP requests
- process data
- return responses (usually JSON)

It runs on a web server (like Uvicorn), which handles incoming connections.

Each endpoint:
- receives a request
- processes data
- returns a response

### Example:
- `/` → returns welcome message
- `/predict` → receives input data and returns a prediction
