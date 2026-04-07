Links: 

Tags: #ml, #evaluation
## Intro 

```python
cross_val_score(model, X, y, cv=5)
```

Split the dataset into k-folds, in this case the dataset will be split into 5 folds with each having 20% of random samples/rows of the data.

## 1. Train/Split  

in a 5 fold split, the program will use 4 folds for training and 1 for testing. This process will be done 5 times. 

| Example     | Case 1      | Case 2       | Case 3        | Case 4         | Case 5      |
| ----------- | ----------- | ------------ | ------------- | -------------- | ----------- |
| Train (80%) | Folds 2 - 5 | Folds 1, 3-5 | Folds 1,2,4,5 | Folds 1 - 3, 5 | Folds 1 - 4 |
| Test (20%)  | Fold 1      | Fold 2       | Fold 3        | Fold 4         | Fold 5      |
| Train Score |             |              |               |                |             |
| Test Score  | 0.836       | 0.848        | 0.824         | 0.814          | 0.834       |

## 2. Interpretation

If the fold scores looks like this : 

							[0.90, 0.62, 0.88, 0.65, 0.91]

Then your model is **UNSTABLE**. The model performs well on some parts of the dataset but poorly on others. 

a) Reasons

- Heterogeneity 
- Not enough data
- Overfitting
- Important Feature imbalance

b) Best approach to check 

--> STANDARD DEVIATION 

|      | Stable | Unstable |
| ---- | ------ | -------- |
| Mean | 0.83   | 0.83     |
| Std  | 0.01   | 0.08     |
					Check List for Std: 
						  < 0.03       -->  Excellent
						  0.03 - 0.06  -->  Normal
						  > 0.07       -->  Investigate
			
