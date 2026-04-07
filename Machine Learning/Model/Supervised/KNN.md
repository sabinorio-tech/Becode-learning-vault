
Tags: #ml #model
## Intro 

				KNN is a model that predicts based on similarity 
						(distance between data points)

--> Instead of learning a formula like Linear Regression 
--> It uses the closest data points to make a prediction

## Code 

### A) KNN Regressor 

```python
from sklearn.neighbors import KNeighborsRegressor

model = KNeighborsRegressor(
    n_neighbors=5,
    weights="distance"
)

model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```
👉 Output = **number (price)**
### B) KNN Classifier

```python
from sklearn.neighbors import KNeighborsClassifier

model = KNeighborsClassifier(
    n_neighbors=5,
    weights="distance"
)

model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```
👉 Output = **class (0 / 1 / category)**

---
## 1. Core Idea 

>	"Tell me who your neighbours are, and i'll tell you who you are"


- You have a new data point 
- KNN looks at the **K closest points in the dataset**
- Then: 
	- Classification -> Majority vote
	- Regression -> average value

### Example 

|Living Area|Price|
|---|---|
|50|150k|
|60|180k|
|70|210k|
Now a new house: 

	Living Area = 65 

KNN says: 

- Find closest neighbours -> 60 and 70 
- Predict -> average -> ~195k 

---
## 2. How does it know what's close? Euclidean Distance

$$
d = \sqrt{(x_1 - x_2)^2 + (y_1 - y_2)^2}
$$

### Example with 2 features 

Let's say: 
- House A → (Living Area = 60, Bedrooms = 2)
- House B → (Living Area = 70, Bedrooms = 3)

Distance:
$$
d = \sqrt{(60 - 70)^2 + (2 - 3)^2} = \sqrt{100 + 1} = \sqrt{101}
$$

					The smaller the distance -> the more similar

---
## 3. Step-by-Step: How KNN works 

1. Choose K 
	- K = number of neighbours (e.g. 3, 5, 7)
2. Compute distance 
	- Calculate distance to **ALL training points**
		→ this is why KNN can be slow
3. Pick nearest K points
	- Sort distances 
	- Take closest K 
4.  Make prediction
	Classification
	- Majority vote  
	    Example: [A, A, B] → predict A
	Regression
	- Average values  
	    Example: [180k, 200k, 220k] → predict 200k

---
## 4. Choosing K (Important)

- Small K (e.g. 1, 3)
  → very sensitive to noise  
  → low bias, high variance  

- Large K (e.g. 20, 50)
  → smoother predictions  
  → higher bias, lower variance  

👉 K controls the bias-variance tradeoff

---
## Very important: Scaling 

```
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)
```

👉 Distance is affected by feature scale
Example:
- Living Area = 100
- Bedrooms = 3

Distance will be dominated by:  
👉 **Living Area (big numbers)**

So:  
👉 Bedrooms becomes almost useless

---
## Intuition (THIS is the key)

>“You look like these points → so I’ll treat you like them”


| Pros                          | Cons                                                        |
| ----------------------------- | ----------------------------------------------------------- |
| Super simple                  | Slow on large datasets (distance to everything)             |
| No training phase             | Needs scaling                                               |
| Works well for small datasets | Sensitive to noise                                          |
|                               | Bad with many dimensions (distances become less meaningful) |
