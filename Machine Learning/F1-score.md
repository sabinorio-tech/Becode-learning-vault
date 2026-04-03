
Tags: #ml, #evaluation


## 1. General idea

> measures the balance between **precision and recall (false positives vs false negatives)**

---

## 2. Core idea

> combines precision and recall using a **harmonic mean**

--- 
## 3. Intuition

> F1-score is high only when BOTH [[precision]] and [[recall]] are high

F1-score punishes imbalance:

- High precision, low recall → low F1  
- Low precision, high recall → low F1  
- Only high when BOTH are high

---
## 4. Formula

$$
F1 = 2 \cdot \frac{Precision \cdot Recall}{Precision + Recall}
$$
---
## 5. Based on confusion matrix

- Precision = TP / (TP + FP)  
- Recall = TP / (TP + FN)

---
## 6. Interpretation

- F1 = 1 → perfect precision and recall  
- F1 = 0 → worst possible  
- Higher = better balance

---
## 7. When to use F1-score

Use F1 when:

- Data is imbalanced  
- You care about BOTH precision and recall  
- You want a single metric instead of choosing between them

---
## Example

Precision = 0.8  
Recall = 0.4  

F1 = 2 * (0.8 * 0.4) / (0.8 + 0.4)  
   = 0.53  

👉 Even though precision is high, F1 is low → recall is weak

---
## Key insight

F1 is strict:

👉 It does NOT reward models that are good at only one thing  
👉 It rewards models that are balanced