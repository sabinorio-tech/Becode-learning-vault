Links: [[Random Forest]], [[Gradient Boosting]]

Tags: #ml, #model
## Code 

### A) Decision Tree Regressor 
```python
from sklearn.tree import DecisionTreeRegressor  
  
model = DecisionTreeRegressor(random_state=42)  
  
model.fit(X_train, y_train)  
y_pred = model.predict(X_test)
```
👉 Output = **number** (price)
### B) Decision Tree Classifier
```python
from sklearn.tree import DecisionTreeClassifier  
  
model = DecisionTreeClassifier(  
max_depth=10,  
random_state=42  
)  
  
model.fit(X_train, y_train)  
y_pred = model.predict(X_test)
```
👉 Output = **class** (0 / 1 / category)
## 1. What is a Decision Tree? 

A **Decision Tree** is just: 
>	A series of yes/no questions that split your data step by step

Example (house price)

								[Root Node]
							Living Area <= 120?
							   /            \
						 [Node A]        [Node B]
					   Bathrooms <= 2     (Leaf)
						 /      \
					 [Leaf]   [Leaf]

And it keeps going... 

Until you reach an **end point** (called a **leaf**): 

-> Predicted price = 320000

---

## 2. General Idea (Intuition)? 

At its core:

👉 It’s trying to **group similar target values together**

Instead of:

> “predict price with a formula”

Think:

> “put similar houses in the same bucket, then average their prices”

### Example 
Imagine a group of houses:

|Living Area|Price|
|---|---|
|50|150k|
|60|160k|
|200|400k|
|220|420k|
A tree might split like:

								Living Area <= 100?

Now you get: 

|          | Left Group | Right group |
| -------- | :--------: | :---------: |
| sample 1 | 50 → 150k  | 200 → 400k  |
| sample 2 | 60 → 160k  | 220 → 420k  |
| Average  |   ≈ 155k   |   ≈ 410k    |
👉 The goal: make groups where values are **as similar as possible**

---
## 3. How does it choose Split

At each node, the tree asks:

> “Which question splits the data into the most similar groups?”

For regression:
👉 It minimizes **prediction error**, usually measured with **MSE (Mean Squared Error)**

For Tree:
👉 It chooses the best split **at the current step**, not globally.

#### A) Intuition of MSE 

| Left Group | Right Group |
| ---------- | ----------- |
| Low MSE    | High MSE    |
| 300k       | 150k        |
| 310k       | 300k        |
| 305k       | 500k        |
| Low  MSE   | High MSE    |
#### B) What happens during a split?

The tree tries different questions like:

- split by Living Area <= 120?
- split by Bathrooms <= 2?
- split by distance <= 10?

And picks the **best one**

For each possible split:
👉 it computes:

						MSE_left + MSE_right (weighted)

This happens at every step:

				Split → Left group → split again → split again...

Each time:  
👉 same logic → minimize MSE

> Then selects the **lowest error split**
#### 🧠 C) Feature importance

Feature importance is basically:
> how much a feature helped reduce MSE across all splits in all trees

#### D) Why trees overfit 

If the tree keeps splitting:
Eventually:

	Leaf:  
	[305k]

👉 average = 305k  
👉 MSE = 0

Perfect fit… but:

👉 it memorized that exact house ❌

#### E) Full process 

At a node: 

1. Try a split (e.g. Living Area <= 120)

2. Split data into:
   → Left group
   → Right group

3. For EACH group:
   → compute average price (this is the prediction)

4. Compute weighted MSE:

$$
(n_{left} / n) * MSE_left + (n_{right} / n) * MSE_right
$$

5. Total error = Weighted MSE

6. Keep the split with lowest total error

---
## 4. What is a leaf? 

A **leaf** is the final group.

Inside a leaf:

👉 prediction = average of their values

So:

							Leaf:
							[300k, 320k, 310k]
							→ prediction = 310k

If a leaf contains only one sample:  
  
👉 prediction = that value  
👉 training error = 0

---
## 5. Why Decision Trees Overfit

They are **too good at memorizing** 😅

They can keep splitting until:
👉 each leaf contains very few samples (even 1)

	this exact house → exact price

That means:
- very high **train score**  
- worse **test score**

👉 This is **overfitting (high variance)**

--- 
## 6. Random Forest 🌲🌲🌲

[[Random Forest]] is using **many trees**, instead of **one tree**

Each tree:
- sees slightly different data (bootstrap sampling)
- uses different features

👉 Predictions are averaged → more stable → less overfitting

---

## 7. In-depth: How a Split REALLY Happens 

### Example Dataset

|Living Area|Price|
|---|---|
|60|150|
|80|180|
|100|200|
|120|300|
|140|320|
### Step 1 - Generate candidate splits

For each feature: 

	Living area: 60, 80, 100, 120, 140  
	→ candidates:  
	<70, <90, <110, <130

👉 Many thresholds (conditions) per feature
👉 These are your **candidates**
### Step 2 - Evaluate each candidate 

We'll test **2 candidates** to keep it clear: 

For EACH candidate: 

1. Split data -> left/right
2. Compute:
	- mean_left
	- mean_right
3. Compute
	- MSE_left 
	- MSE_right
4. Compute total: 
👉 weighted MSE

#### 🔹Candidate A: Living Area < 90
#### 1. Split 

|             | Left Group |  Right group  |
| ----------- | :--------: | :-----------: |
| Living Area |   60, 80   | 100, 120, 140 |
| Price       |  150, 180  | 200, 300, 320 |

#### 2. Mean per group 

Left mean = 
$$
(150+180)/2=165
$$

Right mean = 

$$
(200+300+320)/3≈273.3
$$
#### 3. MSE per group 

Left: 
$$
\begin{aligned}
(150−165)^2+(180−165)^2=225+225 =450 \\ MSE_L=450/2=225
\end{aligned}
$$
Right:

$$
\begin{aligned}
(200−273.3)^2+(300−273.3)^2+(320−273.3)^2
\\ ≈5377+711+2178≈8266 \\ MSE_R≈8266/3≈2755
\end{aligned}
$$
#### Total weighted MSE 

$$
MSE_{split​}=(2/5)∗225+(3/5)∗2755 ≈90+1653=1743
$$

#### 🔹 Candidate B: Living Area < 110
#### 1. Split 
|             |  Left Group  | Right group |
| ----------- | :----------: | :---------: |
| Living Area |  60, 80,100  |  120, 140   |
| Price       | 150, 180,200 |  300, 320   |
#### 2. Means

Left mean: 
$$
(150+180+200)/3≈176.7
$$
Right mean: 
$$
(300+320)/2=310
$$

#### 3. MSE 

Left: 
$$
\begin{aligned}
(150−176.7)^2+(180−176.7)^2+(200−176.7)^2
\\ ≈712+11+542≈1265 \\ MSE_L≈1265/3≈422
\end{aligned}
$$
Right: 

$$
\begin{aligned}
(300−310)^2+(320−310)^2=100+100 =200 \\ MSE_R=200/2=100
\end{aligned}
$$

#### 4. Total weight MSE

$$
MSE_{split​}=(3/5)∗422+(2/5)∗100 ≈253+40=293
$$


### Step 3 - Choose best split 

| Canditate | MSE    |
| --------- | ------ |
| <90       | 1743 ❌ |
| <110      | 293 ✅  |

👉 Compare ALL candidates  
👉 Pick the one with lowest MSE

❌ Not per feature  
✅ Across ALL features

### Step 4 - Apply split 

👉 Now (and only now):

Node → Left + Right

								        Root
							     Living Area < 110
							        /         \
							   Left           Right
### Step 5 - Repeat recursively 

👉 Each node:
- gets subset of data
- repeats full process
### Step 6 - Stop condition 

Eventually you get: 

	Leaf: [200]

👉 Mean = 200  
👉 MSE = 0  
👉 Stop

- No improvement possible
- or constraints (max_depth, etc.)

---

## 8. Prediction Phase (How a tree gives ONE value)

For a new sample: 

		1. Start at root
		2. Follow conditions 
		3. End in ONE leaf

👉 Prediction = mean of that leaf

---
## 9. Mathematical Objective 

At each node, the tree: 

1. Computes prediction: 
$$
\bar{y} = \frac{1}{n}\sum_i y_i
$$
2. Computes error:
$$
MSE = \frac{1}{n}\sum_i (y_i - \bar{y})^2
$$
3. For each split:
$$
MSE_{split} = \frac{n_L}{n} MSE_L + \frac{n_R}{n} MSE_R
$$

4. Chooses:

$$
\arg\min MSE_{split}
$$

---

## 10. Regression vs Classifiers 

| Regression Tree     | Classification Tree              |
| ------------------- | -------------------------------- |
| -> predicts numbers | -> predicts classes              |
| -> uses MSE         | -> uses Gini impurity or entropy |

