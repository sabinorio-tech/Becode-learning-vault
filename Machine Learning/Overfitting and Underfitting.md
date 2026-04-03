Links: [[Generalisation]]

Tags: #ml, #concept

## Intro 


	Overfitting and underfitting describe how well a model learns patterns and how well it generalizes to new data.

They are two common ways a model can fail.

---
## Core idea

				- Overfitting → model too complex → memorizes data  
				- Underfitting → model too simple → misses patterns   
  
👉 Goal → find the balance (good generalisation)
## 1. Overfitting is usually caused by high variance

Overfitting happens when the model learns [[noise]] and specific details instead of general patterns

Example: 

| Size | Price |
| ---- | ----- |
| 80   | 200   |
| 100  | 260   |
| 130  | 320   |
True relationship:

								price ≈ 3 * size

But imagine the model does this:

								80 -> 200
								100 -> 260
								120 -> 320

It memorizes **exact points**.

#### What it looks like in scores 

								Train score: 0.97
								Test score:  0.78

Train = extremely good  
Test = much worse

Meaning:

> The model memorized the training data.

___

## 2.  Underfitting is usually caused by high bias

Underfitting is the opposite. 

The model is **too simple to capture the pattern**.

Example: 

True relationship:

								price = size²

But the model is linear:

								price = a * size

It cannot capture the curve.
So predictions are bad **everywhere**.

####  What it looks like in scores

								Train score: 0.55
								Test score: 0.53

Both are bad.

Meaning:

> The model is too simple.

----
## 3. Good model (ideal case)

The sweet spot: 

								Train score: 0.85
								Test score: 0.83

That means:
- learned real patterns
- works on unseen data
- not memorizing

### Typical interpretation

| Gap             | Interpretation            |
| --------------- | ------------------------- |
| **0 – 0.03**    | Excellent generalization  |
| **0.03 – 0.08** | Very good                 |
| **0.08 – 0.15** | Normal for complex models |
| **0.15 – 0.25** | Some overfitting          |
| **> 0.25**      | Strong overfitting        |

---

## 4. Simple analogy: studying for an exam

**Underfitting**

- You barely study. 
- You understand nothing. 

							You fail both: 
							- Practice questions
							- Real exam

**Overfitting**

You memorize **exact questions from the practice tests**. 

				But the exam asks different ones -> You fail

---
## 5. Connection to deeper concepts

These behaviors are explained by:

- [[Bias vs Variance]]
- [[Model Evaluation and Validation Concepts]]

---
## Important nuance

Bias and variance are not strict categories.

- A model can have both high bias and high variance  
- High variance does not always mean overfitting  
- Data quality and feature selection also affect performance  

They are tendencies that help explain model behavior, not exact rules.