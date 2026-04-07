Links: 
- [[Model]]  
- [[Generalisation]]

Tags: #ml #evaluation

> Model evaluation = measuring performance, checking generalisation, avoiding overfitting, and selecting the best model using metrics, validation, and tuning.

---
## 1. What are we evaluating?

We evaluate a model to answer:

- How accurate is it?
- Does it generalize to unseen data?
- Is it stable? Does it give consistent results across different data splits?
- Is it too simple or too complex?

---
## 2. Metrics (HOW GOOD is the model?)

These measure model performance.
### 🔹 Regression metrics (predicting numbers)

- **MAE** = average absolute error
- **[[MSE]]** = average squared error (penalizes large errors more)
- **RMSE** = square root of MSE (same unit as target)
- **[[R² score]]** = how much variance the model explains
### 🔹 Classification metrics (predicting categories)

- Accuracy (can be misleading with imbalanced data)
- [[Precision]]
- [[Recall]] 
- [[F1-score]]

Tools:
- [[Confusion matrix]]
- `classification_report()`
- ROC curve (AUC)

> Metrics depend on the type of problem.

---
## 3. Validation methods (HOW do we test it?)

### 🔹 Train / Test split

- Train set → model learns  
- Test set → final evaluation  

> Test set simulates unseen real-world data

### 🔹 Cross-validation

Example: 5-fold [[Cross Validation Score]]

- Train multiple times on different splits
- Output:
  - Mean score → performance
  - Std → consistency across folds

> Reduces randomness from a single split

### 🔹 Validation vs Test

- Validation set → used during model tuning  
- Test set → used ONLY for final evaluation  

👉 Test set must remain untouched to simulate real-world performance

**IMPORTANT**:

			Don’t use test set during training (to avoid data leakage)

---
## 4. What can go wrong?

### 🔹 Overfitting and underfitting

- **Overfitting** → good on train, worse on test  
- **Underfitting** → bad everywhere  

| Case         | Train     | Test  |
| ------------ | --------- | ----- |
| Underfitting | Low       | Low   |
| Good fit     | High      | High  |
| Overfitting  | Very high | Lower |

> Goal = good performance on unseen data

→ See [[Generalisation]]  
→ See [[Bias vs Variance]]

---
## 5. What influences performance?

### 🔹 Hyperparameters

Settings chosen before training:

- Random Forest → `max_depth`, `n_estimators`
- KNN → `n_neighbors`
- Gradient Boosting → `learning_rate`

> They control **bias vs variance** → control model complexity

---
## 6. Model selection

Compare models:

- Linear Regression
- Decision Tree
- Random Forest
- KNN

Using:
- Metrics
- Cross-validation
- Generalisation performance

> Choose the model that performs best on unseen data based on cross-validation and test performance

---
## ⚠️ 9. Data Leakage (Critical)

> Data leakage = using information during training that should not be available

Examples:

- Using test data during training ❌
- Creating features using target variable ❌

👉 Leads to:

- Unrealistically high performance
- Poor real-world results

---
## 7. Final insight

Good evaluation balances:

- Performance (metrics)
- Generalisation (train vs test)
- Stability (cross-validation)
- Complexity (hyperparameters)

> A model is not good because it performs well on known data,  but because it performs well on data it has never seen before.