Links: [[Docker]], [[Local vs Production]], [[Cloud]]

Tags: #webdev #deployment #backend #system

---
## 🚀 1. Goal

Deployment is:

> Taking your code and making it accessible online

👉 So users can interact with your application through a URL

---
## 🔄 2. Full Flow

```text
						   Code (ML model)
								↓
			  Framework (Flask / FastAPI / Streamlit)
								↓
					Server (Uvicorn / Flask server)
								↓
						 Docker (packaging)
								↓
						Platform (Render)
								↓
				  Live Application (public URL)
```

---
## 🧱 3. Components

### 🌐 Frameworks (Application Layer)

- Flask → web apps + APIs
- FastAPI → API-first backend
- [[Streamlit]] → data apps / UI
👉 Defines logic and behavior

### ▶️ Server (Execution Layer)

- Uvicorn (FastAPI)
- Flask built-in server
👉 Runs your application and handles requests

### 📦 Tools (Packaging Layer)

- [[Docker]]

👉 Packages:

- code
- dependencies
- environment

### ☁️ Platforms (Hosting Layer)

- Render

👉 Hosts your app and makes it accessible online

---
## ⚙️ 4. What Happens During Deployment

### Step-by-step:

```text
					1. You push code to GitHub
								↓
				 2. Platform (Render) pulls your code
								↓
				 3. Docker builds the environment
								↓
				4. Server (Uvicorn) starts your app
								↓
				  5. App is exposed via a public URL
```

---
## 🌐 5. Runtime Flow (User Perspective)

```text
						User (browser / app)
								↓
							HTTP request
								↓
						 Live API (Render)
								↓
						  Server (Uvicorn)
								↓
					  Framework (FastAPI / Flask)
								↓
					 Business logic (ML model)
								↓
						Response (JSON / HTML)
								↓
						  User sees result
```

---
## 🔁 6. Local vs Production

### 🖥️ Local

- runs on your machine
- uses local environment
- accessed via `localhost`

### 🌍 Production

- runs on a remote server
- accessible via public URL
- used by real users

👉 [[Local vs Production]]

---
## 🧠 7. Concepts

- API Fundamentals → how requests/responses work
- [[Docker]] → ensures consistent environment
- Render → deploys and hosts the app

---
## 🔗 8. Where it fits in your system

```
Data → Model → API → Docker → Render → User
```

👉 Deployment is the **final step** of the pipeline

---
## 💡 Core Insight

Deployment connects:

```
Your code → real users
```

Without deployment:

- your app only works locally

With deployment:

- your app becomes a real product

---
## ✅ Summary

Deployment is the process of:

- packaging your application
- running it on a server
- making it accessible online

> [!tip]  
> Framework → builds the app  
> Server → runs the app  
> Docker → packages the app  
> Render → hosts the app

> [!important]  
> Deployment is what turns your project into a real, usable application