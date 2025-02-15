# **FastAPI Beyond CRUD 🚀**

This is a **FastAPI** project focused on building scalable APIs beyond basic CRUD operations.  
It includes **background task processing**, **automated testing**, **CI/CD pipelines**, and **GitHub Actions** for **enforcing commit conventions and nightly builds**.

📌 **Features:**
- ✅ **FastAPI** framework for high-performance APIs
- ✅ **PostgreSQL** database integration
- ✅ **Redis + Celery** for background task processing
- ✅ **GitHub Actions** for **CI/CD & Conventional Commits**
- ✅ **Automated nightly builds** (12 AM SF time)
- ✅ **Failure notifications via SendGrid Email**
- ✅ **Fully Dockerized**: Just run `docker compose up`

---

## **📌 Table of Contents**
1. [Getting Started](#getting-started)
2. [Updated Requirements](#updated-requirements)
3. [Project Structure](#project-structure)
4. [Running the Application](#running-the-application)
5. [Running Tests](#running-tests)
6. [Contributing](#contributing)

---

## **🚀 Getting Started**
### **🔧 Prerequisites**
Ensure you have **Docker** installed before proceeding.

### **📥 Clone the repository**
```bash
git clone [https://github.com/jod35/fastapi-beyond-CRUD.git](https://github.com/SkyeKD/fastapi-beyond-CRUD.git)
cd fastapi-beyond-CRUD/
```
## **📌 Updated Requirements**

✅ **GitHub Actions for Conventional Commits**  
1. Enforces **Conventional Commits** on PRs.  
2. Closes PRs if the commit message is **invalid**.  
3. Sends **failure notifications** to contributors.  

✅ **Nightly Build & Test Workflow**  
1. Runs **every night at 12 AM SF Time** (`cron: "0 8 * * *"`).  
2. Builds and pushes **Docker images** **only if all tests pass**.  
3. **Failure notifications** sent via **SendGrid Email**.  

✅ **Environment Setup**  
- **No extra downloads required**.  
- **Everything runs inside Docker**.

## **📌 Setup Instructions**

### 🔹 **Configure SendGrid for Email Notifications**
To enable email notifications for failed PRs and nightly builds, follow these steps:

1. **Sign up for SendGrid** (if you haven’t already):  
   👉 [SendGrid Sign Up](https://sendgrid.com/)  
   
2. **Create an API Key**:  
   - Go to **Settings** → **API Keys**  
   - Click **Create API Key**  
   - Choose **Full Access** or **Restricted Access (Email Sending)**  
   - Copy the generated API Key

3. **Add the API Key to GitHub Secrets**:
   - Navigate to your GitHub repository  
   - Click on **Settings** → **Secrets and variables** → **Actions**  
   - Click **New repository secret**  
   - Name it `SENDGRID_API_KEY` and paste the copied API key  
   - Click **Save** 
 ## **📁 Project Structure**
 ```bash
fastapi-beyond-CRUD/
│── src/                     # Main application source code
│   ├── auth/                # Authentication module
│   ├── books/               # Books API module
│   ├── reviews/             # Reviews API module
│   ├── tags/                # Tags API module
│   ├── celery_tasks/        # Background task processing with Celery
│   ├── database/            # Database models and migrations
│   ├── middleware/          # Custom middlewares
│   ├── errors/              # Custom error handlers
│   └── __init__.py          # Application entry point
│
│── .github/workflows/       # CI/CD workflows for GitHub Actions
│── tests/                   # Unit and integration tests
│── Dockerfile               # Docker image definition
│── docker-compose.yml        # Docker orchestration
│── .env.example             # Example environment variables
│── requirements.txt         # Project dependencies
│── README.md                # Project documentation
```
## **🚀 Running the Application**
### **🔧 Start API & Background Workers**
1. open Docker Desktop
2. copy .env.example to .env
```bash
copy .env.example .env
```
3. start application 
```bash
docker compose up
```
### **🌍 Access API Endpoints**
**📌 OpenAPI Docs: http://localhost:8000/api/v1/docs**

**📌 Example API Call:**
```
curl -X POST http://localhost:8000/api/v1/auth/login -d '{"username": "test", "password": "pass"}' -H "Content-Type: application/json"
```
```
{"detail":[{"type":"missing","loc":["body","email"],"msg":"Field required","input":{"username":"test","password":"pass"}},{"type":"string_too_short","loc":["body","password"],"msg":"String should have at least 6 characters","input":"pass","ctx":{"min_length":6}}]}
```
## **🧪 Running Tests**
```bash
pytest
```
## **📌 Contributing**
- 1. Fork the repository and create a new branch.
- 2. Use Conventional Commits (GitHub Actions will enforce this).
- 3. Submit a Pull Request (PR).
### **📌 Commit Message Format Example:**
 ```bash
feat: add JWT authentication
fix: resolve API pagination bug
```
## **📌 List of Changes**

### 🔹 **1. Added GitHub Actions**
- Add `commit-check.yml` and `nightly-build.yml`.
- ✅ Enforce **Conventional Commits** on PRs.
- ✅ Automate **Nightly Builds** at **12 AM SF time** (`cron: "0 8 * * *"`).
- ✅ Send **failure notifications** for PRs/tests.

### 🔹 **2. Updated `docker-compose.yml` and `Dockerfile`**
- 🚀 Runs **without extra downloads**.
- 🔧 **Automatically loads** environment variables.

### 🔹 **3. Modified .env.example**
- 🔧 Add configuration.

### 🔹 **4. Enabled Background Task Processing**
- ⚡ **Celery Workers** running inside Docker.

### 🔹 **5. Integrated Email Notifications**
- 📧 **SendGrid Email** for **failure alerts**.
