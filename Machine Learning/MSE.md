Tags: #ml, #evaluation

## 1. What is it? 

							MSE = Mean Squared Error

It measures:

> “On average, how wrong are my predictions?”

#### Full equation:
$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$
#### Breakdown:

$$
n → total \ number \ of \ samples
$$
$$
\sum_{i=1}^{n} → sum \ over \ all \ data \ points
$$
$$
 y_i = actual \ value (real \ house \ price)
$$
$$
\hat{y}_i = predicted \ value
$$
$$
(y_i - \hat{y}_i) = error
$$
- squared:
	- removes sign (so positive and negative errors don’t cancel out)
	- punishes big errors
	- Creates a smooth function  -> allows optimization (gradient descent)
- mean → average over all samples

You can also think of it like:
$$
MSE= \frac{(error_1​)^2+(error_2​)^2+⋯+(error_n​)^2}{n}​
$$

👉 So MSE = **average squared mistake**

---
## 2. Why does it exist?

Because we need a way to measure **"how far predictions are from actual values"**.

Without MSE: 
- No way to to evaluate or train models effectively
- No way to compare models
- No way to train models


MSE is also a **loss function**:

> Models (like Linear Regression) try to **minimize MSE**

So during training:

- Model predicts
- Computes MSE
- Adjusts parameters to reduce it

👉 This is how the model **learns**

### Why MSE specifically?
 
- Smooth function
- Differentiable everywhere
- Easy to optimize with gradient descent

👉 That’s why it’s widely used

	MSE heavily penalizes large errors because the gradient grows with the error → large mistakes have a stronger influence during training.

- Linear Regression works so well
- Gradient descent converges nicely

---
## 3. When is it useful?

MSE is best when: 

#### ✅ Regression problems

- House prices
- Salary prediction
- Temperature prediction

#### ✅ When big mistakes are BAD

Because squaring exaggerates large errors:

- Error = 10 → squared = 100
- Error = 100 → squared = 10,000 😬

👉 So MSE says:

> “Big mistakes are VERY bad, fix those first.”

---
## 4. When is it bad?

#### ❌ 1. Sensitive to outliers

If one prediction is way off:
- It can dominate the entire score

Example:

- 99 predictions are perfect
- 1 prediction is VERY wrong  
    → MSE becomes huge
#### ❌ 2. Hard to interpret

If you're predicting prices (€):

- Error = 1000€
- MSE = 1,000,000 😐

👉 that number is not directly interpretable in real-world units

#### ❌ 3. Not robust

If your dataset has:

- noise
- weird values
- extreme prices

👉 MSE can be heavily influenced by extreme values

### MSE vs MAE 

- **MSE**  
→ penalizes large errors more  
→ sensitive to outliers  
  
- **MAE**  
→ treats all errors equally  
→ more robust to outliers

| MSE                            | MAE                          |
| ------------------------------ | ---------------------------- |
| -> Penalizes large errors more | -> treats all errors equally |
| -> sensitive to outliers       | -> more robust to outliers   |
  
👉 Use MSE when large errors are very costly  
👉 Use MAE when you want a more robust metric

---
## 5. How to interpret it?

#### Rule #1: Lower = better

- MSE = 0 → PERFECT model
- Higher MSE → worse predictions

#### Rule #2: Compare models, not absolute value

❌ Wrong mindset:

							“Is MSE = 500,000 good?”

✅ Correct mindset:

|     | Model A | Model B |
| --- | ------- | ------- |
| MSE | 500k    | 300k    |
> → B is better
#### Rule #3: Use RMSE for intuition

								RMSE = √MSE

This brings it back to original units:

- MSE = 1,000,000
- RMSE = 1000 €

Now it makes sense:

> “Typical error is around ~1000€”

>[!important] Important insight  
> MSE has **no absolute meaning**  
>  
> It only makes sense:  
> - relative to your dataset  
> - compared to other models

>[!tip] Intuition Summary 
> Think of MSE as:
> 
> 	“A strict teacher that HATES big mistakes”
> - Small errors → fine
> - Big errors → punished HARD


---
## 6. Where is MSE used? 

- Linear Regression → minimizes MSE directly
- Decision Trees → uses MSE to choose best splits
- Random Forest → each tree uses MSE for splits, then predictions are averaged
- Gradient Boosting → reduces MSE step-by-step
