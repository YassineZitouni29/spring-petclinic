# 🚀 CI/CD Pipeline for Spring Petclinic

This repository showcases my implementation of a complete **CI/CD pipeline** for the Spring Petclinic application, featuring:

- **Jenkins (Declarative Pipeline)**
- **Docker image automation**
- **GitHub Webhooks**
- **SonarQube static code analysis**
- **Automated build & test workflow**

The goal was to create a professional, end‑to‑end DevOps pipeline similar to those used in real industry environments.

---

## 🔧 What I Implemented

### ✅ 1. Jenkins Setup (Dockerized)
- Ran Jenkins inside a Docker container.
- Installed plugins: Git, Pipeline, Docker, SonarQube, Maven Integration.
- Configured credentials for GitHub & Docker.
- Prepared the environment to:
  - Run Maven builds and tests.
  - Build Docker images.
  - Publish analysis results to SonarQube.

---

### 🔗 2. GitHub → Jenkins Webhook Integration
- Connected my GitHub fork of **spring-petclinic** to Jenkins.
- Configured a webhook so every **git push** triggers the pipeline automatically.
- Used **ngrok** to expose Jenkins locally for webhook testing.
- Verified that commits instantly activate CI.

---

## 🔄 3. Full CI/CD Pipeline (Jenkinsfile)

The pipeline consists of:

### **1. Checkout**
Automatically pulls the latest code from GitHub.

### **2. SonarQube Code Analysis**
Executed via Maven:

```
mvn sonar:sonar \
  -Dsonar.projectKey=petclinic \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=<token>
```

Provides:
- Code smells
- Bugs and vulnerabilities
- Maintainability rating
- Quality Gate feedback

### **3. Test Stage**
Runs the Petclinic test suite:

```
./mvnw test
```

### **4. Build Stage**
Builds the application JAR:

```
./mvnw clean package
```

### **5. Docker Image Build**
Creates an application image versioned with Jenkins build number:

```
docker build -t petclinic:${BUILD_NUMBER} .
```

### **6. (Optional) Deployment**
Local container testing or pushing image to a registry.

---

## 🐳 Docker Support

Test the built image locally:

```bash
docker run -p 8081:8080 petclinic:<tag>
```

---

## 📡 Pipeline Flow (CI/CD Architecture)

```
GitHub Push
      ↓
GitHub Webhook
      ↓
Jenkins Pipeline
      ↓
SonarQube Analysis
      ↓
Maven Tests
      ↓
Maven Build (JAR)
      ↓
Docker Image Creation
```

---

## 🧠 Skills Demonstrated

### 🚀 DevOps & CI/CD
- Jenkins Pipelines (Declarative)
- GitHub Webhook automation
- Pipeline‑as‑Code (Jenkinsfile)
- SonarQube quality analysis
- Docker image automation

### 💻 Backend & Build Tools
- Maven lifecycle mastery
- Spring Boot build & test flow

### 🔐 Code Quality & Security
- Static code analysis (SonarQube)
- Quality Gate evaluation

### 🌐 Networking & Tooling
- Ngrok tunneling for remote webhooks
- Local multi‑container development workflow

---

## ▶️ Running Petclinic Locally

### Without Docker

```bash
mvn clean package
java -jar target/*.jar
```

### With Docker

```bash
docker build -t petclinic .
docker run -p 8081:8080 petclinic
```

---

## 📌 Purpose of This Repository

This fork is intended to **showcase my CI/CD pipeline work**, including Jenkins, Docker, SonarQube, and webhook integration.  
The source code of Spring Petclinic remains unchanged; the focus is on the DevOps workflow.

---
