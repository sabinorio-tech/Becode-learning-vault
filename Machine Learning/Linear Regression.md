Tags: #ml #model
## Code 

```python
from sklearn.linear_model import LinearRegression  
  
model = LinearRegression()  
  
model.fit(X_train, y_train)  
y_pred = model.predict(X_test)
```

---
## 1. General Idea

		Find a straight line (or hyperplane) that best predicts your target by minimizing error

---
## 2. How it works

This is the heart of linear regression: 

$$
y = \theta_0 + \theta_1 x_1 + \theta_2 x_2 + \cdots + \theta_n x_n
$$

👉 Translation:

- y = predicted price
- x1,x2,... = features (living area, bedrooms, etc.)
- θ = weights (importance of each feature)

---
## 3. Intuition (VERY IMPORTANT)

Think of it like:

> “Each feature contributes a **fixed amount, independent amount**”

>[!tip] test

Example:

- Living area → +€2000 per m²
- Bedrooms → +€10k
- Distance to Brussels → -€5k

👉 It’s all **linear relationships**

---
## 4. How the model learns

Same concept as you saw before:

#### 1. Start with initials weights (θ) OR directly computes them (depending on method)

#### 2. Make predictions

→ calculate predicted prices

#### 3. Measure error using MSE

$$
MSE = \text{average of } (y_{real} - y_{pred})^2
$$

#### 4. Adjust weights to minimize error

→ Find the values of θ that minimize the MSE

---
## 5. ⚠️ Important detail 

👉 In **sklearn LinearRegression**, it usually does **NOT use gradient descent**

Instead:

> It uses a **closed-form solution (Normal Equation)** → directly finds best θ

So:
- No iterations
- No learning rate
- Just **math optimization**

| Pros                | Cons                                              |
| ------------------- | ------------------------------------------------- |
| Fast                | Can only learn linear relationships               |
| Easy to interpret   | Struggles with complex data (like housing prices) |
| Good baseline model | Sensitive to outliers                             |

---

## 6. Final mental model 

👉 Linear Regression =

> “Each feature adds or subtracts a fixed amount to the prediction, and we choose those amounts to minimize prediction error.”

