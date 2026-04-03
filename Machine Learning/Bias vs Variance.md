Links: [[Overfitting and Underfitting]] 

Tags: #ml, #concept

## Intro 

	Bias and Variance describe how a model learns from data and why it may underfit or overfit.

They explain the root cause of model behavior.

--- 

## Core idea 


			- High bias → model too simple → misses patterns  
			- High variance → model too complex → sensitive to data

👉 Goal → balance both to achieve good generalisation

---
## Difference between bias & variance with overfitting & underfitting

Think of it like this:
🔍 Bias & Variance = **CAUSES (what’s wrong inside the model)**
 📊 Underfitting & Overfitting = **SYMPTOMS (what you observe)**

---
## 1. Bias 

Bias measures how much the model oversimplifies the problem.

High bias: 
- model is too simple  
- cannot capture real patterns  
- leads to underfitting

---
## 2. Variance 

Variance measures how much the model’s predictions change when the training data changes.

High variance:  
- model changes a lot with small data changes  
- learns [[noise]] instead of real patterns  
- leads to overfitting

---
## 3. Relationship with model behavior

- High bias → [[Overfitting and Underfitting|Underfitting]]  
- High variance → [[Overfitting and Underfitting|Overfitting]] 

---
## 4. Bias-Variance tradeoff 

You cannot minimize both at the same time: 

				- Reducing bias → often increases variance  
				- Reducing variance → often increases bias  
  
👉 Goal = find the balance

---
## 5. Intuition

- High bias → model is too rigid  
- High variance → model is too flexible  