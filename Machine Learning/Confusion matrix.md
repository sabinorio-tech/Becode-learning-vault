Tags: #ml, #evaluation

## 1. General Idea

> A confusion matrix shows **how your model is making decisions** and **what kind of mistakes it makes**

Classification cares about: 

> Classification cares not just about being wrong, but about **what type of mistake was made**.

### Simple example

Spam detection:
- Actual: spam
- Predicted: not spam

👉 That’s a **different type of mistake** than:
- Actual: not spam
- Predicted: spam

		Confusion matrix separates these cases on classification problems

---
## 2. The structure


|            | Predicted YES | Predicted NO |
| :--------: | :-----------: | :----------: |
| Actual YES |     ✅ TP      |     ❌ FN     |
| Actual NO  |     ❌ FP      |     ✅ TN     |

What each means: 

#### ✅ TP — True Positive

> You said YES, and it was YES  
> 👉 correct (Type I error)

#### ❌ FP — False Positive

> You said YES, but it was NO  
> 👉 false alarm 

#### ❌ FN — False Negative

> You said NO, but it was YES  
> 👉 missed case (Type II error)

#### ✅ TN — True Negative

> You said NO, and it was NO  
> 👉 correct

#### Key Takeaway 

> Not all errors are equal — and the confusion matrix shows exactly what type of errors your model makes.

---
## 3. Why it matters 

> All classification metrics (accuracy, precision, recall, F1) are calculated from the confusion matrix.

---
## 4. Total predictions

				Total (all predictions) = TP + FP + FN + TN

#### Example: 

|            | Prediction YES | Prediction NO |
| :--------: | :------------: | :-----------: |
| Actual YES |    40 (TP)     |    10 (FN)    |
| Actual NO  |     5 (FP)     |    45 (TN)    |
#### Interpretation:

- TP = 40 → correctly predicted YES
- FN = 10 → missed YES cases
- FP = 5 → false alarms
- TN = 45 → correctly predicted NO

---
## 5. Basic metric from confusion matrix

### Accuracy

$$
Accuracy = \frac{TP + TN}{TP + FP + FN + TN}
$$

👉 Measures overall correctness

---
## When is it useful?

- When different mistakes have different costs  
- When data is imbalanced  
- When accuracy alone is not enough

👉 Example:  
- Medical diagnosis → FN is very dangerous  
- Spam detection → FP is annoying

---
## Final insight 

The confusion matrix is the foundation of all classification metrics — every metric is just a different way of combining TP, FP, FN, and TN.