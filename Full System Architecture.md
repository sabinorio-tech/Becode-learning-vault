
Links: [[Data Extraction]], [[Machine Learning]], [[Backend Architecture]]

Tags: #system #architecture #endtoend #data #backend 

---
## 🌐 1. What is a Full System Architecture?

A full system architecture is:

> The complete flow of how data moves through a system — from collection to user interaction

It connects all parts of an application into one pipeline.

---
## 🧠 2. The Big Picture

```text
								Data Sources
									↓
							   Data Extraction
									↓
						 Data Cleaning / Validation
									↓
						  EDA / Feature Engineering
									↓
						 Model Training / Evaluation
									↓
								Saved Model
									↓
				 API Layer (implemented with Flask / FastAPI)
									↓
						  Deployment (Docker / Render)
									↓
								User Request → Prediction → Response
```

---
## 🧱 3. System Layers

### A) Data Layer

→ Collect and prepare data

Includes:

- [[Data Extraction]]
- Data Sources
- Web Scraping
- Data Cleaning
- Data Validation

-> See [[Data Processing]]
### B) Analysis & Modeling Layer

→ Understand and build intelligence

Includes:

- EDA (Exploratory Data Analysis)
- Feature Engineering
- [[Machine Learning]]

### C) Backend / API Layer

→ Expose functionality to users

Includes:

- API Fundamentals  
- API Frameworks (Flask, FastAPI)

-> [[Backend Architecture]]

### D) Deployment Layer

→ Make the system accessible online

Includes:

- Docker
- Render

-> See [[Backend Architecture]] first

---
## 🔄 4. Runtime Flow (User Perspective)

```text
							 User inputs data
									↓
						  Frontend sends request
									↓
							API receives request
									↓
						    Model processes input
									↓
						   Prediction generated
									↓
						  Response returned (JSON)
									↓
							  User sees result
```

---
## ⚙️ 5. Data Flow (Offline / Training)

```text
							 Raw data collected
									↓
						  Data cleaned and validated
									↓
							   EDA performed
									↓
							 Features engineered
									↓
						 Model trained and evaluated
									↓
						  Model saved (e.g. .pkl)
```

---
## 🚀 6. Deployment Flow

```
							   Code + Model
									↓
						  Docker builds environment
									↓
						   Render deploys container
									↓
					   Server (Uvicorn / Flask) runs API
									↓
						   Public endpoint available
```

---
## 💡 7. Core Insight

A complete system is:

> **Data → Intelligence → Interface → Deployment**

- Data = foundation
- Model = intelligence
- API = access
- Deployment = availability

---
## 🧠 8. Mental Model

```text
Data Layer → feeds → Model Layer
Model Layer → exposed by → API Layer
API Layer → delivered via → Deployment Layer
```
👉 Each layer depends on the previous one

---
## 🎯 9. Example (Your Project)

```text
							   Scraping data
									↓
						   Cleaning + validation
									↓
							  Training model
									↓
							   Saving model
									↓
						 FastAPI endpoint (/predict)
									↓
							  Docker container
									↓
							  Render deployment
									↓
							 User gets prediction
```

---
## 🔗 10. Key Idea

This is not separate parts.

It is **one continuous system** where:

- data flows forward
- each layer adds value
- the final result reaches the user

---
## 🧠 11. Architecture vs Execution

> This diagram shows structure, not time.

- Training flow (offline) builds the model
- Runtime flow (online) serves predictions

👉 A system has both:
- **build phase** (data → model)
- **serve phase** (API → user)