
Links: [[Bias vs Variance]]
  
Tags: #ml #practical

## Goal  
  
		Improve model performance by reducing bias and variance.  
  
---  
  
## 1. Fixing high bias (underfitting)  

Symptoms:  
- Train score → low  
- Test score → low

Problem:  
- Model too simple  
- Cannot learn patterns  
  
>[!tip] Solutions:  
>- Use a more complex model  (e.g. Linear → Polynomial / Tree / Ensemble)  
>- Add better features  (feature engineering)  
>- Reduce regularization  
>- Train longer (for some models)  
  
---  
  
## 2. Fixing high variance (overfitting)  

Symptoms:  
- Train score → very high  
- Test score → lower  
- Cross-validation scores unstable

Problem:  
- Model too complex  
- Learns noise  
  
>[!tip] Solutions:  
>- Reduce model complexity  (e.g. limit depth, fewer parameters)  
>- Regularization  (L1, L2, pruning)  
>- Add more relevant data (not just more, but useful)  
>- Remove noisy / irrelevant features  
>- Data cleaning (handle [[noise]], outliers)  
>- Feature scaling (important for distance-based models like KNN)
  
---  
  
## 3. When both are high  
  
Problem:  
- Model is bad AND unstable  
  
Strategy:  
  
1. Fix bias first  
2. Then reduce variance  
  
---  
  
## 4. Data-related issues  
  
Problem:  
- Model performs differently on different datasets  
  
Solutions:  
  
- Add missing features (e.g. location)  
- Improve data quality  
- Use better sampling (stratified split)  
  
---  
  
## 5. Quick decision guide  


|     |     | Problem       | What to do                             |     |     |
| --- | --- | ------------- | -------------------------------------- | --- | --- |
|     |     | High bias     | Increase complexity / add features     |     |     |
|     |     | High variance | Simplify model / regularize / add data |     |     |
|     |     | Both          | Fix bias first                         |     |     |
|     |     | Data issue    | Improve data / features                |     |     |
  
---  
  
## Final insight  
  
Improving a model is about balancing:  
- Complexity  
- Data  
- Stability  
  
Not just increasing performance blindly.

--- 
## Practical mindset

Start simple:
1. Diagnose the problem  
2. Apply one change at a time  
3. Re-evaluate using validation  

Avoid changing everything at once.