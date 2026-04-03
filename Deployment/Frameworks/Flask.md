Links: [[Flask Templates (Jinja)]], [[Flask - Request Handling]], [[API Fundamentals]]  
  
Tags: #webdev #api #flask #backend #framework 

---
## 🌐 1. What is Flask?

Flask is a Python web framework.

It allows Python to:
- run a web server  
- handle URLs (routes)  
- receive HTTP requests  
- return HTTP responses (HTML, JSON, etc.)

> [!important] 💡 Core idea  
Flask connects **HTTP requests → Python logic → HTTP responses**

---

## 🧱 2. Basic Setup
```python
from flask import Flask, request, render_template

app = Flask(__name__)

```

> [!important]  You import Flask tools.
> - `Flask`  
→ Used to create the app itself
> - `request`  
→ Used to read incoming data from the user
>- `render_template`  
→ Used to return HTML files from the `templates` folder
>- `jsonify` 
→ return JSON

---
## ⚙️ 3. The App Object
```python
 app = Flask(__name__)
```

> “Create the web application”

- Initializes your Flask app
- Tells Flask where your project is located
- Needed for templates and static files

👉 Think of it as the **brain of your backend**

---
## 🛣️ 4. Routing (Core Mechanism)

Flask works using **routes + decorators**: 

```python
@app.route("/")
def home():
    return "Hello"
```

What happens:
1. User visits `/`
2. Flask matches the route
3. Runs the function
4. Returns response

### 📡 4.1 Route Methods

Routes can handle different HTTP methods:

```python
@app.route("/predict", methods=["POST"])  
def predict():  
	return "Prediction"
```

- GET → retrieve data
- POST → send data

👉 Same endpoint, different behavior

---
## 🎯5. The Decorator (@)
```python
@app.route("/")
```

A decorator registers the function to a URL.
	👉 “When someone visits `/`, run the function below”

>[!tip]  
Without the decorator, Flask would not know which function belongs to which URL.

---
## 📦 6. Returning Responses

### A) Text / HTML

```python
return "Hello"
```
### B) JSON (API)
```python
return jsonify({"message": "Hello"})
```
👉 JSON is used for APIs

---
## 📥 7. Reading Request Data

Flask can read incoming data:

### JSON (API)

```python
data = request.get_json()
```
### Form (HTML)
```python
name = request.form["name"]
```
👉 This is how user input reaches your backend

---
## 🔄 8. How Everything Works Together

```text
								   User  
									↓  
							Browser sends request  
									↓  
							Flask receives request  
									↓  
							 Route matches URL  
									↓  
							  Function runs  
									↓  
						(Optional) read user input  
									↓  
						Return response (HTML / JSON)  
									↓  
							 User sees result
```

---
## 🌐 9. Flask Use Cases

Flask can be used for:

- Websites → return HTML
- APIs → return JSON

👉 Same tool, different outputs

---
## 📁 10. Basic Project Structure

```text
project/  
│  
├── app.py  
├── templates/  
│   └── index.html  
├── static/  
│   └── style.css
```

👉 Flask automatically uses:

- `templates/` → HTML
- `static/` → CSS / JS

---
## 💡 Core Insight

Flask maps:

> **URL → function → response**  

