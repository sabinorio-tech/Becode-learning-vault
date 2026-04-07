Links: [[Linear Regression]]

Tags: #ml, #model
## Code 

```python
from sklearn.preprocessing import PolynomialFeatures  
from sklearn.linear_model import LinearRegression  
from sklearn.pipeline import Pipeline  
  
model = Pipeline([  
("poly", PolynomialFeatures(degree=2)),  
("model", LinearRegression())  
])  
  
model.fit(X_train, y_train)  
y_pred = model.predict(X_test)
```

___
## 1. What is Polynomial Degree? 

	It's a way to make linear regression capture non-linear relationships

Instead of: 

$$
y=θ_0​+θ_1​x
$$

you extend it to: 

$$
y = \theta_0 + \theta_1 x + \theta_2 x^2 + \theta_3 x^3 + \cdots
$$

👉 This lets the model fit **curves instead of straight lines**

---

## 2. Example (intuitive)

### Degree = 1 (normal linear regression)

👉 straight line

### Degree = 2

👉 curve (parabola)

### Degree = 3+

👉 more flexible curves ((**higher risk of overfitting**))

---
## 3. What's REALLY happening 

It **creates new features automatically**

If you had:

		Living Area

Degree 2 → becomes:

		Living Area  
		(Living Area)^2

If you had multiple features:

		x1, x2

You get:

		x1, x2, x1², x2², x1*x2

---
## 4. IMPORTANT 

### High degree = danger

- Degree 2 → often good
- Degree 3 → depends
- Degree 10 → high risk of overfitting

👉 Model starts memorizing data → **high variance**

---
## 5. When do you use it? 

Mainly with:

- Linear Regression
- Ridge / Lasso

NOT usually needed for:

- Random Forest 🌳
- Gradient Boosting 🚀

Because those already capture non-linearity