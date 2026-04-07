Links: [[Model Evaluation and Validation Concepts]], [[Generalisation]]

Tags: #ml #model #core

---
## 🌐 1. What is a Model?

A model is:

> A mathematical function that learns the **relationship between inputs (features) and a target variable** to make predictions on new data

👉 Its goal is to [[Generalisation]]

You can think of it as:

> **A system that converts inputs into predictions**

---
## 🧠 2. Core Idea

```text
Inputs (X) → Model (f, θ) → Prediction (ŷ)
```

- **X (inputs)** → features of the data
- **θ (parameters)** → values learned during training
- **f** → mathematical function
- **ŷ (prediction)** → output

---
## ⚙️ 3. Mathematical View

A model is usually a function:

```
Prediction = f(X, θ)
```

### Example: Linear Regression

$$  
price = \theta_0 + \theta_1 \cdot living_area + \theta_2 \cdot bathrooms + \theta_3 \cdot bedrooms  
$$

Example:

```
Price = 50k
      + 2500 * living_area
      + 15000 * bathrooms
      + 8000 * bedrooms
```

👉 The model learns the **best θ values** by minimizing error (loss)

---
## 🧱 4. Intuition (Your Project)

Example data:

|Living Area|Bedrooms|Bathrooms|Energy|→ Price|
|---|---|---|---|---|
|120|3|1|200|350k|
|200|4|2|150|520k|
|80|2|1|300|200k|

The model learns patterns:

- Bigger houses --> Higher price
- More bathrooms --> Higher price
- Closer to Brussels --> Higher price

Then predicts:

```text
Input → (150, 3, 2, 180)
↓
Prediction → ~430k
```
👉 This learned rule = **trained model**

---
## 🔄 5. Training Process

```text
								   Data
									↓
							 Feature Engineering
									↓
								Model.fit()
									↓
							 Learn parameters (θ)
									↓
						Minimize error (loss function)
```
👉 The model adjusts θ to reduce prediction error

---
## 🔮 6. Prediction Phase

```text
								 New data
									↓
							  Model.predict()
									↓
								Prediction
```
👉 Uses learned θ — no more learning happens

---
## ⚖️ 7. Model Evaluation

To measure performance:

👉 [[Model Evaluation and Validation Concepts]]

Examples:

- MSE
- RMSE
- R²
- Precision / Recall

---
## 🧩 8. Types of Models

### A) Supervised Learning

- Has target variable
- Examples:
    - regression
    - classification

### B) Unsupervised Learning

- No target variable
- Example:
    - clustering

---
## 🧠 9. Different Models

Different models represent patterns differently:

| Model                                                                      | What it is                  |
| -------------------------------------------------------------------------- | --------------------------- |
| [[Linear Regression]]                                                      | linear relationship         |
| [[Polynomial Regression]]                                                  | curved relationship         |
| [[Machine Learning/Model/Supervised/Decision Tree\|Decision Tree]]         | series of if/else splits    |
| [[Machine Learning/Model/Supervised/Random Forest\|Random Forest]]         | many trees averaged         |
| [[Machine Learning/Model/Supervised/Gradient Boosting\|Gradient Boosting]] | sequential error correction |
| [[KNN]]                                                                    | distance-based              |
| [[Clustering]]                                                             | grouping                    |
| [[Neural Network]]                                                         | complex nonlinear function  |

---
## ⚙️ 10. In Practice (sklearn)

```python
model = RandomForestRegressor()
```
👉 create model

```python
model.fit(X_train, y_train)
```
👉 learn parameters

```python
model.predict(X_test)
```
👉 make predictions

---
## 💡 11. Core Insight

A model is:

> **A function that learns patterns from data to make predictions**

---
## 🧠 12. Mental Model

```
Data → Features → Model → Prediction
```

---
## 🔗 13. Key Idea

A model is NOT everything.

It depends on:

- good data
- good features
- proper evaluation

> [!quote]  
> A model is only as good as the features it receives





