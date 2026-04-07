Links: 
- [[Deployment Pipeline]]
- [[AWS]]

Tags: #cloud #backend #deployment #concept

---
## 🌐 1. What is Cloud Computing?

Cloud Computing is:

> The delivery of computing resources (servers, storage, databases, networking) over the internet

Instead of owning physical machines:

👉 You **rent infrastructure on demand**

---
## 🧠 2. Core Idea

```text
Your computer → limited resources
Cloud → scalable, on-demand resources
```

```text
Local machine → fixed capacity
Cloud → infinite (on demand)
```

👉 You don’t manage hardware  
👉 You use it via the internet

---
## 🏗️ 3. What Does the Cloud Provide?

### 🟦 Compute (Servers)
- Virtual machines (like your computer, but online)
- Example: run backend apps, APIs

### 🟩 Storage
- Store files, datasets, images
- Example: ML datasets, user uploads

### 🟨 Databases
- Managed databases (SQL / NoSQL)
- Example: PostgreSQL in the cloud

### 🟥 Networking
- Control traffic, security, communication
- Example: APIs, web apps

---
## ⚙️ 4. Why Use Cloud?

### ✅ Scalability
- Handle more users easily

### ✅ No Infrastructure Management
- No need to buy or maintain servers

### ✅ Pay-as-you-go
- Only pay for what you use

### ✅ Reliability
- Data centers worldwide

---
## 🔄 5. Where It Fits (Big Picture)

```text
User → API → Backend → Database
                     ↓
                   Cloud ☁️
```

or more detailed:

```text
User
 ↓
API (FastAPI / Flask)
 ↓
Backend Logic
 ↓
Cloud Infrastructure (AWS)
 ├── Compute (server)
 ├── Storage
 └── Database
```

👉 Cloud is the **environment where everything runs**

---
## 🧱 6. Types of Cloud Services

### 🟦 IaaS (Infrastructure as a Service)
- Rent servers, networking
- You manage everything else

👉 Example: virtual machines

### 🟩 PaaS (Platform as a Service)
- Platform handles infrastructure
- You focus on code

👉 Example: deployment platforms

### 🟨 SaaS (Software as a Service)
- Fully ready software

👉 Example: Gmail, Notion

---
## ☁️ 7. Cloud Providers

- [[AWS]] (Amazon Web Services)
- Google Cloud
- Microsoft Azure

👉 They provide the same core services

---
## 🔥 8. Real Example (Your Project)

Without cloud:

```text
Your laptop → runs ML model → local only
```

With cloud:

```text
User → API → Cloud server → ML model → response
```
👉 Anyone can access your app

---
## ⚠️ 9. Key Insight

> Cloud is NOT a database  
> Cloud is NOT a server  

👉 It is a **platform that provides both**

---
## 🧭 10. Mental Model

```text
Cloud = Renting a powerful computer on the internet
```

Instead of:

- buying hardware
- managing servers

👉 You just **use resources when needed**

