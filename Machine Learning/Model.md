Links: 
- [[Feature Engineering]]  
- [[Model Evaluation and Validation Concepts]]

Tags: #ml #model

---
## Intro 

A model is a mathematical function that learns the **approximate relationship** between input features and a target variable, so it can make predictions on new data.

👉 Its goal is to [[Generalisation]]

you can think of it as **a machine that converts inputs into predictions**

>[!example] Model Formula 
Prediction = f(inputs, θ)

- **Inputs (X)**    -->   The features of the data
- **θ (Theta)**     -->   The parameters the model learns
- **f**                  -->   The mathematical function

---
## 1. Simple Intuition 

Imagine your ImmoEliza project.

|Living Area|Bedrooms|Bathrooms|Energy|→ Price|
|---|---|---|---|---|
|120|3|1|200|350k|
|200|4|2|150|520k|
|80|2|1|300|200k|

The model studies thousands of rows and learns patterns like: 

- Bigger houses --> Higher price
- More bathrooms --> Higher price
- Closer to Brussels --> Higher price

After learning, it can predict: 
- Living Area: 150
- Bedrooms: 3
- Bathrooms: 2
- Energy: 180
--> Predicted price: 430k 

That learned rule = **The trained model**

---
## 2. What a model actually is mathematically 

A model is usually **a mathematical function (often a formula)**.

Example: Linear Regression 

$$
price = \theta_0 + \theta_1 \cdot living\_area + \theta_2 \cdot bathrooms + \theta_3 \cdot bedrooms
$$

Example prediction: 

	Price = 50k
	      + 2500 * living_area
	      + 15000 * bathrooms
	      + 8000 * bedrooms

Those numbers (2500, 15000, etc.) are the **parameters θ**.

The **training process** finds the best values for those by minimizing error using a **loss function** (measured with [[Model Evaluation and Validation Concepts#1. Metrics|metrics]])

---
## 3. Types of Models 

- **Supervised Learning**
    - Has target variable (price)
    - Example: regression, classification
- **Unsupervised Learning**
    - No target variable
    - Example: clustering

---
## 4. Different models

Different models use different ways to represent patterns in data.

| Model                     | What it is                                                           |
| ------------------------- | -------------------------------------------------------------------- |
| [[Linear Regression]]     | linear relationship                                                  |
| [[Polynomial Regression]] | curved relationship                                                  |
| [[Decision Tree]]         | series of if/else splits                                             |
| [[Random Forest]]         | many decision trees                                                  |
| [[Gradient Boosting]]     | many decision trees sequentially, each tree corrects previous errors |
| [[KNN]]                   | predicts using nearby data points based on distance                  |
| [[Clustering]]            | groups similar points without a target variable                      |
| [[Neural Network]]        | complex nonlinear function inspired by the brain                     |


Example for **Random Forest** (your project): 

Instead of one formula, it uses **hundreds of decision trees** trained on different subsets of data and averages their predictions.

---
## 5. In sklearn terms


When you write: 
```python
model = RandomForestRegressor()
```
you created a **model object**

Then: 
```python
model.fit(X_train, y_train)
```
The model **learns the parameters**

Then: 
```python
model.predict(X_test)
```
The model **makes predictions**

---
## 6. Model Evaluation 

[[Model Evaluation and Validation Concepts]]

---
## 🧠 7. Training vs Prediction

### 🏋️ Training phase

Model learns parameters θ from data
```python
model.fit(X_train, y_train)
```

### 🔮 Prediction phase

Model uses learned parameters to make predictions
```python
model.predict(X_test)
```

👉 This distinction is **fundamental in ML**

---

>[!quote] A model is only as good as the features it receives



