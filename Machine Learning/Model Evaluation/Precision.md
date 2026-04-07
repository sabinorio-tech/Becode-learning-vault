Tags: #ml, #evaluation

## Intro

	Precision tells you how many of your predicted positive cases are actually correct

---
## 1. General idea 

> Precision measures how **reliable** the model is when predicting the positive class (YES)

---
### 2. Core idea

Precision focuses on:

> Out of all predicted YES, how many were actually YES?

---
## 3. Intuition

From confusion matrix:
> Precision is about avoiding false positives (false alarms)
- TP → correct YES
- FP → wrong YES (false alarm)

👉 Precision only cares about these two

---
## 4. Formula 
$$
Precision = \frac{TP}{TP + FP}
$$

- TP -> Correct YES
- TP + FP -> All predicted YES

So:

> correct YES / all YES predictions

### Example 

|            | Prediction YES | Prediction NO |
| :--------: | :------------: | :-----------: |
| Actual YES |    40 (TP)     |    10 (FN)    |
| Actual NO  |     5 (FP)     |    45 (TN)    |
> Total predicted YES =45 
### Precision: 

$$
\frac{40}{40 + 5} = \frac{40}{45} = 0.89
$$

		When the model predicts YES, it is correct 89% of the time

---

## 5. When to use Precision

Use precision when:

> ❗ False positives are costly (false alarms are bad)

### Examples:

- Spam filter → don’t block real emails
- Fraud detection → don’t accuse innocent users
- Medical test → don’t falsely diagnose healthy people

---

## ## ⚠️ 6. Precision vs Recall Trade-off

- Increasing precision → reduces false positives  
- But may increase false negatives (lower recall)

- Increasing recall → catches more positives  
- But may increase false positives (lower precision)

👉 You need to balance both depending on the problem

---
## 7. Precision vs Recall

- Precision → cares about FP (false alarms)  
- Recall → cares about FN (missed cases)