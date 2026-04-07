
Tags: #ml, #concept
## Intro

A model **generalizes** when it can make **good predictions on data it has never seen before**. 

Example:

You train a model to predict house prices using **20,000 houses**.

If it can correctly predict prices for **new houses that were not in the dataset**, then the model **generalizes well**.

So:

**Generalization = performing well on unseen data.**

---

## Why this matters

Machine learning is **not about memorizing the dataset**. 

It's about learning **patterns**. 

Example dataset: 

|Size|Bedrooms|Price|
|---|---|---|
|80m²|2|200k|
|120m²|3|320k|
|150m²|4|420k|
A good model learns:

						“Bigger houses usually cost more.”

Then when a **new house appears**:

|Size|Bedrooms|Price|
|---|---|---|
|100m²|3|?|

It predicts **~260k**.

That is **generalization**

	A model may seem good on training data, but we need a way to verify if it truly generalizes.

---
## How we measure generalisation

We evaluate generalisation using:

- [[Model Evaluation and Validation Concepts]]
- Metrics like:
  - R²
  - MSE
  - Accuracy, Precision, Recall (for classification)

---
## When generalisation fails

A model can fail to generalize in two main ways:

- [[Overfitting and Underfitting]]

These are caused by deeper issues:

- [[Bias vs Variance]]

---
## Key idea

- [[Bias vs Variance]] explains *why* models overfit or underfit  
- [[Overfitting and Underfitting]] shows *how it appears* in practice
