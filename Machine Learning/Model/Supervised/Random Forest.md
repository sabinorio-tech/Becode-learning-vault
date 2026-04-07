
Tags: #ml #model

## Intro

	Random Forest = a group of imperfect decision-makers, each trained on slightly different data, whose averaged opinion is more reliable than any single one.

---
## 1. Core Idea

	Random Forest = many decision trees combined to more stable and accurate predictions

#### Decision Tree recap

- Splits data using **feature-based questions**
- Creates **groups of similar samples**
- Final prediction = **average (regression)** or **majority vote (classification)**
#### Problem with one tree

- Overfits easily
- Memorizes training data
- High variance

>[!Success] Solution: Random Forest
>- Build **many trees**
>- Each tree is slightly different
>- Combine predictions → more stable

---
## 2. The "Random" Part 

This is the heart of Random Forest 

#### A. Random samples (Bootstrap)

Each tree: 
- gets a **random subset of rows with replacement** 
- Some samples may appear multiple times, others not at all

👉 Same dataset → different trees see different data

##### Bagging (Bootstrap Aggregating)

Random Forest uses **bagging**:
- Train multiple models on different random samples
- Combine their predictions

**Goal**: reduce variance

#### B. Random features 

At each split: 
- tree only considers a  **subset of features**

👉 Prevents all trees from using the same dominant feature (like Living Area)

>[!tip] Key insight 
>Randomness reduces correlation between trees, making the average prediction more powerful.

#### Why is correlation important?
Because Random Forest works by **averaging predictions**
👉 Averaging only helps if the errors are different

>[!example] A) High correlation 
**True price = 300k**
>
Tree 1 → 350k  
Tree 2 → 352k  
Tree 3 → 349k 
>
All trees are wrong in the same way.
👉 Average = ~350k → still wrong ❌

>[!example] B) Low correlation 
**True price = 300k**
>
Tree 1 → 260k  
Tree 2 → 340k  
Tree 3 → 300k  
>
Errors cancel out.
👉 Average = ~300k → correct ✅

>[!important] C) The key idea
> Random Forest works because errors cancel out when trees are different.

If trees are too similar:  
👉 you basically just have “many copies of the same tree”

---
## 3. How prediction works

#### Regression: 
- Each tree predicts a number
- Final = **average**

#### Classification: 
- each tree predicts a class 
- final = **majority vote**

--- 
## 4. Why Random Forest works so well 

> [!tip] Why Random Forest works well
> **✔ Handles non-linearity**  
> - no need for straight-line relationships
>
> **✔ Handles feature interactions**  
> - can combine conditions (implicit interaction between features)
>
> **✔ Robust to noise**  
> - one bad tree doesn’t ruin everything
>
> **✔ Reduces overfitting**  
> - compared to a single tree (by reducing variance)

---
## 5. Limitations 

Don’t skip this 👇

- ❌ Less interpretable than a single tree
- ❌ Can still overfit (but less)
- ❌ Slower than simple models
- ❌ Doesn’t extrapolate well (important!)

👉 Example:  
If max price in training = 1M  
It cannot extrapolate beyond the range of training data

---

# 6. RandomForestRegressor


```python
from sklearn.ensemble import RandomForestRegressor  
  
model = RandomForestRegressor(  
n_estimators=300,   
random_state=42,   
)  
  
model.fit(X_train, y_train)  
y_pred = model.predict(X_test)
```

>[!tip] Use case:
>- predicting continuous values

>[!tip] Key idea:
> average of tree predictions

>[!important] Important notes:
>- each tree uses MSE for splitting (same as DecisionTreeRegressor)
>- output = number


---

# 7. RandomForestClassifier

```python
from sklearn.ensemble import RandomForestClassifier  
  
model = RandomForestClassifier(  
n_estimators=300,  
max_depth=None,  
random_state=42,  
n_jobs=-1  
)  
  
model.fit(X_train, y_train)  
y_pred = model.predict(X_test)
```


>[!tip] Use case:
>- predicting categories

>[!tip] Key idea:
> majority vote of trees

>[!important] Important notes:
>- each tree uses Gini impurity or entropy for splitting
>- output = class

