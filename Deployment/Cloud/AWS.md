Links: 
- [[Cloud Computing]]

Tags: #cloud #aws #deployment #backend #concept

---
## ☁️ 1. What is AWS?

AWS (Amazon Web Services) is:

> A cloud platform that provides on-demand computing resources over the internet

👉 It is an implementation of [[Cloud Computing]]

---
## 🧠 2. Core Idea

```text
Cloud = concept
AWS = tool that provides the cloud
```

```text
Your laptop → limited
AWS → scalable infrastructure
```

👉 You use AWS to run applications, store data, and manage systems

---
## 🏗️ 3. What AWS Provides

AWS gives you building blocks to create systems:

### 🟦 Compute
- Run servers in the cloud
- Example: backend APIs

### 🟩 Storage
- Store files and datasets
- Example: images, CSVs

### 🟨 Databases
- Managed databases
- Example: PostgreSQL, MySQL

### 🟥 Networking
- Control communication between systems
- Example: APIs, security rules

---
## ⚙️ 4. Core AWS Services

### 🟦 EC2 (Elastic Compute Cloud)

> Virtual server in the cloud

- Run your backend or app
- Full control over environment

👉 Like a remote computer

### 🟩 S3 (Simple Storage Service)

> File storage in the cloud

- Store datasets, images, backups
- Highly scalable

👉 Like a cloud hard drive

### 🟨 RDS (Relational Database Service)

> Managed SQL database

- PostgreSQL, MySQL, etc.
- AWS handles maintenance

👉 Like SQLite but hosted and scalable

### 🟥 Lambda

> Run code without managing servers

- Event-based execution
- No server setup

👉 Serverless computing

---
## 🔄 5. Where It Fits (Big Picture)

```text
									User
									 ↓
							 API (FastAPI / Flask)
									 ↓
								Backend Logic
									 ↓
									AWS ☁️
									 ├── EC2 → runs app
									 ├── S3 → stores data
									 └── RDS → database
```
👉 AWS is where your system lives in production

---
## 🔥 6. Real Example (Your Project)

Without AWS:

```text
Local machine → ML model → local API
```

With AWS:

```text
User → API (EC2) → Model → Data (S3 / RDS)
```

👉 Your app becomes accessible worldwide

---
## 🧱 7. Key Concepts in AWS

### 7.1 🔐 IAM (Identity & Access Management)
- Control permissions
- Who can access what

### 7.2 🌐 Regions & Availability Zones
- AWS data centers worldwide
- Improve reliability and speed

### 7.3 💰 Pay-as-you-go
- Only pay for what you use

---
## ⚠️ 8. Key Insight

> AWS is NOT one tool

👉 It is a **collection of services**

Each service solves a specific problem:
- Compute
- Storage
- Database
- Networking

---
## 🧭 9. Mental Model

```text
AWS = toolbox for building internet systems
```

Instead of:
- owning servers
- managing infrastructure

👉 You assemble services to build your system
