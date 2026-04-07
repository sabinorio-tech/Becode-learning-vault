Links: [[Render]], [[Deployment Pipeline]]

Tags: #webdev #deployment #docker #tool #backend

---

## 🌐 1. What is Docker?

Docker is a tool used to package an application and everything it needs into a container.

This ensures the application runs the same way on any machine.

> [!important] 💡 Core Idea  
> Docker packages **code + environment + dependencies** so the app behaves consistently everywhere.

---
## ⚙️ 2. What is it used for?

Docker is mainly used to:

- package applications
- include dependencies and environment setup
- avoid “it works on my machine” problems
- run apps consistently across systems
- prepare apps for deployment

> [!example]  
> A FastAPI or Streamlit app works on your laptop.  
> Docker packages the app, Python, libraries, and setup so it can run the same way on Render or another machine.

---
## 🚀 3. Why Docker is popular

Docker is popular because it is:

- consistent
- portable
- useful for deployment
- good for collaboration
- widely used in real-world development

---
## 🆚 4. Docker vs FastAPI / Streamlit

### A) FastAPI / Streamlit

- used to build the application
- define logic and behavior
- handle requests or UI

### B) Docker

- does not build the app itself
- packages the app and its environment
- makes it easier to run and deploy

> [!important]  
> FastAPI / Streamlit → create the app  
> Docker → packages the app

---

## 🧱 5. Where it fits in deployment

Docker is the **packaging layer**.

```text
							   Code / Model  
									↓  
							FastAPI / Streamlit  
									↓  
								  Docker  
									↓  
								  Render  
									↓  
								 Live App  
```

---
## 📦 6. Core Idea of a Container

A container is an isolated environment that includes:

- your code
- Python
- libraries
- system dependencies
- startup instructions

👉 The app behaves the same wherever the container runs

---
## 🧱 6.1 Image vs Container

- **Image** → blueprint (built from Dockerfile)
- **Container** → running instance of that image

```text
Dockerfile → Image → Container
```

👉 Image = recipe  
👉 Container = running app

---
## 📝 7. Dockerfile

A Dockerfile is a text file that tells Docker how to build an image.

It defines:

- the base image
- the working directory
- files to copy
- dependencies to install
- the command to start the app

---
## 🔁 8. Basic Example

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY . /app

RUN pip install -r requirements.txt

CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
```
👉 This builds an image that runs a FastAPI app

---
## 🔄 9. How it works

1. You write a Dockerfile
```dockerfile
FROM python:3.11-slim
```
👉 Define the environment

2. Docker builds an image
```bash
docker build -t my-app .
```
👉 Creates a blueprint of your app

3. Docker executes instructions
```dockerfile
RUN pip install -r requirements.txt
```
👉 Installs dependencies inside the image

4. The container starts the app
```dockerfile
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
```
👉 Defines what runs when container starts

5. Docker runs the container
```bash
docker run -p 8000:8000 my-app
```
👉 Starts the app and exposes it

---
## 🌐 9.1 Ports (Accessing the App)

Containers are isolated, so ports must be exposed:

```bash
docker run -p 8000:8000 my-app
```

- first 8000 → your machine
- second 8000 → container

👉 This allows users to access your app

---
## 🧠 10. Docker in ML Projects

Docker is especially useful for ML applications:

- ensures correct dependencies
- avoids version conflicts
- makes deployment reproducible

---
## 💡 Core Insight

Docker allows you to:

> package an application with its full environment so it can run the same way anywhere

You don’t just move the code —  
👉 you move the entire system

---
## ✅ Summary

Docker is a tool for packaging applications into containers.

It is useful when:

- you want consistency
- you want easier deployment
- you want reproducibility

> [!tip]  
> FastAPI / Streamlit → build the app  
> Docker → packages the app  
> Render → hosts the app

> [!important]  
> Docker is not a cloud platform.  
> It does not host your app by itself.  
> It prepares the app to run consistently.