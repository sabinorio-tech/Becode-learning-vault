
Links: 

Tags: #webdev #flask

---
## 🛣️ What is Routing?

Routing is the process of:

> Mapping a URL → to a specific Python function

---
## 🔗 1. Basic Route

```python
@app.route("/")
def home():
    return "Hello"
```
👉 Meaning:

- `/` → URL path
- `home()` → function that runs

---

## 🧠 2. How Flask Matches URLs

When a user visits a URL:

```text
User → enters URL  
↓  
Flask checks all routes  
↓  
Finds matching path  
↓  
Runs corresponding function  
```

---
## 📍 3. URL Paths

A URL path is the part after the domain:

```text 
http://127.0.0.1:5000/predict
                      ↑
                   this part
```

- `/` → homepage
- `/predict` → prediction page
- `/about` → about page

---
## 🔢 4. Dynamic Routes

You can pass values through the URL:
```python
@app.route("/double/<value>")
def double(value):
    return str(float(value) * 2)
```

Example: 

	/double/5 → returns 10

---
## ⚙️ 5. Route Methods (GET vs POST)

	A route must match BOTH:
	
	URL + METHOD
## 🔹 GET (default)

> “Give me data”
```python
@app.route("/predict")
```

- Automatically GET
- No form data sent (usually)
- Used when opening pages

## 🔸 POST

> “Here is data, do something with it”
```python
@app.route("/predict", methods=["POST"])
```

- Sends data to server
- Used for forms

---
## Example 

```python
@app.route("/", methods=["GET"])
def home():
    return render_template("index.html")

@app.route("/predict", methods=["POST"])
def predict():
    data = request.form
```

Flow: 
```text
User opens page → GET "/"  
↓  
Form is shown  
↓  
User submits form → POST "/predict"  
↓  
Flask runs predict()  
```

--- 

> [!important] 💡 Core Insight
> 
Routing is how Flask decides  
“Which function should run for this URL?”

