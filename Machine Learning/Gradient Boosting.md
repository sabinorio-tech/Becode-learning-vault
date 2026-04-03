
Tags: #ml #model
## Intro 

	A sequence of weak decision-makers, where each new model focuses on correcting the mistakes of the previous ones. 

---
## 1. Core idea

Gradient Boosting = many trees built **sequentially**, each one improving the previous.

#### Decision Tree recap
- Splits data using **feature-based questions**
- Creates **groups of similar samples**
- Prediction = **average (regression)** or **class (classification)**
#### Problem with one tree
- Overfits easily
- High variance
- Can’t generalize well
#### Problem with Random Forest
- Trees are independent
- does not explicitly correct previous errors (trees are independent)
- Just averages
#### ✔ Solution: Gradient Boosting
- Trees are built **one after another**
- Each tree learns from the **errors of the previous ones**

---
## 2. The boosting part

#### A) Sequential learning 

- Tree 1 makes predictions 
- Tree 2 looks at **errors of Tree 1**
- Tree 3 looks at **errors of Tree 2**, etc.

👉 Each tree = **error corrector**

#### B) Learning from errors 

Instead of predicting the target directly.

👉 Each new tree predicts the **residuals (errors)**

residuals = y_true - y_pred
	-> difference between true value and current prediction

Example: 

							True price = 300k  
							Tree 1 → 250k (error = +50k)  
							Tree 2 → +30k  
							Tree 3 → +20k  

Final prediction: 

						👉 250k + 30k + 20k = 300k ✅

#### C) The key idea 

	Each new tree focuses on what the model is still getting wrong 

#### D) Learning rate

	Controls how much each tree contributes 

Example:
- learning rate = 0.1
	👉 each tree only corrects **10% of the error**

#### Why? 

> Prevents over-correcting -> smoother learning 

#### E) Why it's called Gradient Boosting? 

Gradient Boosting uses **gradient descent**: 

👉 It minimizes a loss function step by step  
👉 Each new tree follows the **direction of the error (gradient)**

In simple terms: 

> each tree moves the model in the direction that reduces error the most 

---
## 3. How prediction works 

#### Regression: 
- Start with initial prediction (often mean)
- Add corrections from each tree 

👉 Final = sum of all tree contributions

#### Classification: 
- Trees improve predictions in terms of probabilities (using log loss)
- Final = class with highest probability 

---
## 4. Why gradient Boosting works so well 

#### ✔ Learns complex patterns
- builds patterns step by step
- very flexible
#### ✔ Reduces bias
- fixes mistakes progressively
- reduces bias over time 
#### ✔ High accuracy
- often better than Random Forest
#### ✔ Works well on structured/tabular data

---
## 5. Limitations 

- ❌ Can overfit easily if too many trees
- ❌ Sensitive to noise (tries to fit errors)
- ❌ Slower (sequential, not parallel)
- ❌ Needs tuning (learning rate, depth, etc.)
- ❌ Harder to tune than Random Forest

---

## 6. GradientBoostingRegressor 

```python
from sklearn.ensemble import GradientBoostingRegressor  
	model = GradientBoostingRegressor(
	    n_estimators=100,
	    learning_rate=0.1,
	    max_depth=3,
	    random_state=42,
	)
	
	model.fit(X_train, y_train)
	y_pred = model.predict(X_test)
```

#### Use case: 
- predicting continuous values 

#### Key idea: 
> sum of sequential corrections 

#### Important notes: 
- fits trees to residuals using MSE as the loss
- output = number
- small trees (weak learners)

---
## 7. GradientBoostingClassifier

```python
from sklearn.ensemble import GradientBoostingClassifier  
	
	model = GradientBoostingClassifier(
		n_estimators=100,
		learning_rate=0.1,
		max_depth=3,
		random_state=42,
	)
	
	model.fit(X_train, y_train)
	y_pred = model.predict(X_test)
```

#### Use case: 
- predicting categories 

#### Key idea: 
> Sequential improvement of classification errors

#### Important notes: 
- uses log loss (not MSE)
- output = predicted class

---
## Final takeaway 

- **Random Forest** → trees are **independent** → reduce variance
- **Gradient Boosting** → trees are **dependent (sequential)** → reduce bias