Tags: #ml, #evaluation
## Intro
				“How well does my model explain the variance in the data”

---
## Core idea

> It compares your model vs a **dumb baseline model**

Baseline = predict the **average value every time**

---
## Interpretation 

R² measures:

	how much variance your model explains relative to predicting the mean

🔹 Formula 

$$
R^2 = 1 - \frac{\sum (y_i - \hat{y}_i)^2}{\sum (y_i - \bar{y})^2}
$$

- Model Error = sum of squared errors (SSE)
$$
SSE = \sum \left(y_{i}-{\hat {y_{i}}}\right)^{2}
$$
$$
y_i = Actual \ value  
$$
$$
\hat{y}_i = Model \ prediction
$$

- Baseline Error = Total variance (sum of squared differences from the mean)
$$
SST = \sum \left(y_{i}-{\overline{y}}\right)^{2}
$$
$$
y_i = Actual \ value  
$$
$$
\overline{y} = mean \ of \ all \ values
$$
Example of the mean:
Prices: 

		[200k, 300k, 400k]
Mean: 
$$
\overline{y} = 300k
$$
Baseline model: 
	always predicts 300k

| R² Score | Meaning                     |
| -------- | --------------------------- |
| 1.0      | Perfect predictions         |
| 0.0      | Same as predicting the mean |
| < 0      | Worse than the mean         |
| 0.5      | Explains 50% of variance    |

---

## Train vs Test R² 

- High train R², low test R² → overfitting  
- Low train R², low test R² → underfitting  
- Similar high values → good generalization

---
## Intuition 

### Case 1: Your model is GOOD 

- Model error = small
- Baseline error = big
👉 fraction = small  
👉 R² ≈ 1

### Case 2: Your model = baseline

- Model error = baseline error
👉 fraction = 1  
👉 R² = 0

### Case 3: Your model is BAD

- Model error > baseline error
👉 fraction > 1  
👉 R² < 0 

--- 
>[!warning] Important limitations

- R² does NOT tell you if predictions are good in absolute terms  
- A model can have high R² but still make large errors  

👉 Always combine R² with other metrics (like RMSE or MAE)