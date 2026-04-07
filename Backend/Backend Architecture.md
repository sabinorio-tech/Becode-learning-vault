Links: [[API]], [[Databases]], [[Deployment Pipeline]]

Tags: #backend #system #webdev #architecture

---
## 🌐 1. What is Backend Development?

Backend development is:

> The part of an application that handles logic, data, and communication with databases

It is responsible for:

- processing user requests
- applying business logic
- interacting with databases
- returning responses

---
## 🧠 2. The Big Picture

```text
							User (browser / app)
									↓
								HTTP Request
									↓
					      API Layer (Flask / FastAPI)
									↓
					 Business Logic (Python / ML model)
									↓
						   Data Layer (Database)
									↓
						HTTP Response (JSON / HTML)
									↓
								   User
```

---
## 🔗 3. Core Components

### A) API Layer

→ Handles requests and responses  
→ Entry point of the backend

Built with:

- Flask
- FastAPI

👉 See [[API]] first

### B) Business Logic

→ The “brain” of the application

Handles:

- calculations
- rules
- ML models
- data transformations

Examples:

- price prediction
- authentication
- filtering data

### C) Data Layer (Database)

→ Stores and retrieves data

Includes:

- SQL
- ORM

-> See [[Databases]]
### D) Deployment Layer

→ Makes the backend accessible online

```text
Code → Docker → Render → Live API
```
👉 Docker, Render -> See [[Deployment Pipeline]],

---
## 🔄 4. Full System Flow

### A) Runtime Flow

```text
								User action 
									↓ 
						    Frontend sends request 
									↓ 
							 API receives request 
									↓ 
							 Business logic runs 
									↓ 
						  (Optional) database query 
									↓ 
						Response returned (JSON / HTML) 
									↓ 
							  User sees result
```
### B) Deployment Flow

```text
								Your code
									↓
								  GitHub
									↓
						  Docker builds environment
									↓
						   Render deploys container
									↓
					   Server (e.g., Uvicorn) runs app
									↓
							 Public API is live
```

---
## 💡 5. Core Insight

A backend system is:

> **A system that receives requests → processes logic → returns responses**

Everything else (Flask, FastAPI, Docker, etc.) are tools used to build and run this system.

---
## 🧠 6. Mental Model

```text
API → communication layer
Backend → logic layer
Database → storage layer
Deployment → delivery layer
```
👉 Together, they form a complete application system