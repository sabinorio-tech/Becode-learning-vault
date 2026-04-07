Links: [[Model]], [[Model Evaluation and Validation Concepts]], [[Full System Architecture]], [[ML Pipeline]]


Tags: #ml #model #system

---
## 🌐 1. What is Machine Learning?

Machine Learning is:

> A way for computers to learn patterns from data and make predictions or decisions

Instead of writing rules manually, the model learns from data.

---
## 🧠 2. The Big Picture

```text
								   Data
									↓
							 Feature Engineering
									↓
							   Model Training
									↓
							  Model Evaluation
									↓
							    Predictions
```

---
## 🧱 3. Core Components

### A) Data

→ The foundation of ML

Includes:
- Data Extraction
- EDA (Exploratory Data Analysis)

👉 Bad data = bad model

### B) Feature Engineering

→ Transform raw data into useful inputs

Examples:
- scaling
- encoding
- creating new features

👉 Feature Engineering

### C) Model

→ The algorithm that learns patterns

Examples:
- Linear Regression
- Random Forest
- KNN
- Neural Networks

👉 [[Model]]

### D) Evaluation

→ Measure how good the model is

Includes:
- accuracy
- MSE
- R²
- precision / recall

👉 [[Model Evaluation and Validation Concepts]]

---
## 🔄 4. Training Flow

```text
								 Raw data
									↓
							   Cleaned data
									↓
							 Feature engineering
									↓
							    Train model
									↓
							   Evaluate model
									↓
							   Tune / improve
									↓
							   Final model
```

---
## ⚙️ 5. In a Real System

Machine Learning is part of a larger system:

```text
							  Data Extraction
									↓
							   Model Training
									↓
							  Saved Model (.pkl)
									↓
							 API (FastAPI / Flask)
									↓
						       User request → prediction
```
👉 [[Full System Architecture]]

---
## 💡 6. Core Insight

Machine Learning is:

> **Turning data into predictions using learned patterns**

---
## 🧠 7. Mental Model

```text
Data → Knowledge → Prediction
```

- Data = input
- Model = learned knowledge
- Prediction = output

---
## 🎯 8. Your Project Example

```text
								House data
									↓
							Feature engineering
									↓
							    Train model
									↓
							  Evaluate (R², RMSE)
									↓
								Save model
									↓
						 FastAPI endpoint (/predict)
									↓
						  User gets price prediction
```

---
## 🔗 9. Key Idea

Machine Learning is not just models.

It is a **pipeline**:

- data → features → model → evaluation → prediction

