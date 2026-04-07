
Tags: #ml, #model

## Code 

```python
from sklearn.cluster import KMeans

model = KMeans(n_clusters=5, random_state=42, n_init=10)

model.fit(X)
clusters = model.predict(X)
```

## 1. What is Clustering (general idea)

	Grouping similar data points together without labeled target values

👉 It’s **unsupervised learning**

So instead of:

- predicting price (like regression ❌)
- predicting class (like classification ❌)

It just says:

> “These data points look similar → let me group them”

---
## 2. How KMeans works (step-by-step)

KMeans is the most common clustering algorithm.

Let’s break it down SUPER clearly:

#### Step 1 - Choose number of clusters

								KMeans(n_clusters=5)

👉 You decide:

> “I want 5 groups”

#### Step 2 - Place random centers (centroids)

Imagine:

- 5 random points dropped on your Belgium map

							These are called centroids

> Initial centroids are random -> results can vary 
#### Step 3 - Assign points to nearest centroid 

Each property goes to the closest center

👉 Uses distance (usually Euclidean distance)

So:

- house near Brussels → goes to Brussels-like centroid
- house in Liège → goes to another centroid

#### Step 4 - Move centroids

Now each centroid moves to the **middle of its assigned points** 

👉 Like finding the mean position of the cluster

#### Step 5 - Repeat

- Reassign points 
- Move centroids 
- repeat until:
	- centroids stop moving
	- or max iterations reached

#### Final result

- each property has a **cluster label**
- each cluster has a **center**

--- 

## 3. Choosing number of clusters

						How do you pick n_clusters?

Common method: 
  
👉 Elbow Method
- Try different values of K 
- Compute total withing- cluster error (inertia)
- Look for the "elbow" point 

  
👉 That's where adding more clusters stops helping much

---
## 4. What a cluster actually is 

A cluster = 

> A group of points that are **close together in feature space**


---

## 5. Key concepts (VERY IMPORTANT)

### 🔹 Centroid
The “center” of a cluster

👉 mean of all points in the cluster

### 🔹 Distance
KMeans usually uses Euclidean distance to decide similarity

👉 closer = more similar

## 🔹 n_clusters

YOU choose how many groups

👉 super important hyperparameter

---
## 6. Strengths vs Weaknesses

### ✅ Strengths

- Simple and fast
- Great for location-based grouping
- Easy to visualize 
- Helps create new features (`location_cluster`)

## ❌ Weaknesses

- You must choose `n_clusters`
- Only works well with **distance-based patterns**
- Sensitive to scale  > → MUST scale features before using KMeans
- Doesn’t understand meaning (only distance)
- assumes clusters are roughly spherical (circular)

👉 VERY IMPORTANT:  
It doesn’t know price, only geometry

---

## 7. Clustering vs your other models 

|Model|Type|Goal|
|---|---|---|
|Linear Regression|Supervised|Predict price|
|Random Forest|Supervised|Predict price|
|Gradient Boosting|Supervised|Predict price|
|**KMeans (Clustering)**|❌ Unsupervised|Group data|

--- 

## 8. How YOU use it in a pipeline 

Workflow: 

#### Step 1 - Create clusters 

```
kmeans = KMeans(n_clusters=10)
df["location_cluster"] = kmeans.fit_predict(df[["latitude", "longitude"]])
```

#### Step 2 - Use it as a feature 

```
features = [
	...
	"location_cluster"
]
```

👉 So clustering is:

> **feature engineering**, not the final model

---
## 9. Intuition (REAL understanding)

Without clustering: 

> "This house is at (50.85, 4.35)"

Model: 

> “Oh cluster 3 → usually expensive”

---
## 10. When should you use clustering? 

Use it when: 
- You have **geographic data**
- You want to **simplify complex patterns**
- You want to create **new features**
