Links: [[Deployment Pipeline]], [[FastAPI]], [[Docker]]

Tags: #webdev #ml #framework #streamlit

---
## 🌐 1. What is Streamlit? 

Streamlit is a Python framework used to build simple web apps for data science and machine learning. 

It allows you to turn Python scripts into interactive web applications.

--- 
## ⚙️ 2. What it is used for

Streamlit is mainly used for: 

- create simple user interfaces (UI)  
- visualize data  
- build dashboards  
- showcase machine learning models  
- quickly test ideas

>[!example]  
> User inputs house features → model predicts price → result is shown directly on the page

---
## 🚀 3. Why Streamlit is popular

Streamlit is popular because it is: 

- very easy to use 
- requires little to no frontend knowledge 
- fast to build prototypes 
- interactive (sliders, inputs, buttons)
- great for data visualization 

---
## 4. 🆚 Streamlit vs FastAPI

### A) Streamlit 
- focuses on UI (what the user sees)
- runs everything in one app 
- best for demos and prototypes
- not designed for complex API's
### B) FastAPI
- focuses on backend (logic + data processing)
- handles requests and responses 
- used for production APIs 
- does not provide a UI by default 
### C) Key difference
- FastAPI → builds an API (no interface)  
- Streamlit → builds a UI (with interface)

---
## 🧱 5. Where it fits in deployment

Streamlit is both: 
- frontend (UI)  
- backend (runs Python code)

Flow:  
  
```text  
Code / model  
↓  
Streamlit  
↓  
(Optionally Docker)  
↓  
Render / Streamlit Cloud  
↓  
Live App
```

>[!tip]  
> Streamlit is often used for prototypes and demos,  
> while FastAPI is used for production systems.

---
## 🔁 6. Basic example

```python
import streamlit as st

st.title("House Price Predictor")

area = st.number_input("Enter area (m²)")
bedrooms = st.number_input("Enter number of bedrooms")

if st.button("Predict"):
    st.write(f"Predicted price for {area}m² and {bedrooms} bedrooms")
```

--- 
## 🔄 7. How it works

1. User interacts with the UI (input fields, buttons)
2. Streamlit reruns the script
3. Python processes the input
4. Result is displayed instantly

--- 
## 🧠 Core idea

Streamlit lets you turn Python into a simple interactive web app without needing HTML, CSS, or JavaScript.

			You write Python → Streamlit handles the UI automatically.

Each interaction:

- updates the script
- recalculates results
- refreshes the UI

>[!important]
> Streamlit reruns the entire script from top to bottom every time the user interacts with the app.

