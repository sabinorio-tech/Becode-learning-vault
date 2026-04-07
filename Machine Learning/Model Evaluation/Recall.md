
Tags: #ml, #evaluation

## Intro 

> how many of the **actual positive cases** your model correctly detects

---
## 1. General idea 

> Recall measures how well the model detects actual positive cases (YES)

---
## 2. Core idea

> Out of all actual YES, how many did the model correctly predict as YES?

---
## 3. Intuition

From confusion matrix:

- TP → correctly detected YES
- FN → missed YES

👉 Recall focuses on **not missing positives**

---
## 4. Formula 

$$
Recall = \frac{TP}{TP + FN}
$$

- TP → correct YES
- TP + FN → total actual positives

So:

> detected YES / all real YES

### Example 

|            | Prediction YES | Prediction NO |
| :--------: | :------------: | :-----------: |
| Actual YES |    40 (TP)     |    10 (FN)    |
| Actual NO  |     5 (FP)     |    45 (TN)    |
> Total actual positives = 50
### Recall: 

$$
\frac{40}{40 + 10} = \frac{40}{50} = 0.80
$$

		The model correctly detects 80% of all actual YES cases

---

## 5. When to use Recall

Use recall when:

> ❗ Missing a positive is dangerous

### Examples:

- Medical diagnosis → don’t miss sick patients
- Fraud detection → don’t miss fraud
- Security → don’t miss threats

---
## Key Insight 

	Recall ignores false positives and focuses only on catching real positives

---
## Precision vs Recall

- Precision → “Am I correct when I say YES?”
- Recall → “Did I catch all YES?

---
## ⚠️ Precision vs Recall Trade-off

- Increasing recall → usually increases false positives  
- Increasing precision → usually decreases recall  

👉 You often need to balance both depending on the problem