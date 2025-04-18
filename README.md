# 🚀 My Node.js App – Production Grade CI/CD with GitHub Actions & Docker.

Welcome to **My Node.js App**! This is a lightweight Express-based Node.js application that serves a beautiful static webpage and exposes a REST API endpoint. It is containerized using Docker, tested with Jest, and deployed using a full CI/CD pipeline via GitHub Actions and DockerHub.

---

## 🌐 Live Screenshots

### 🖼️ Main Webpage
![Main Page Screenshot](images/main-page.png)

### 🖼️ API Endpoint - `/api/hello`
![API Screenshot](images/api-page.png)

---

## 📁 Project Structure

```bash
.
├── .github/workflows/main.yml   # CI/CD GitHub Actions workflow
├── Dockerfile                   # Multi-stage Docker build
├── index.js                     # Main Express app
├── public/                      # Static HTML content
│   └── index.html
├── test/                        # Jest test for /api/hello
│   └── app.test.js
├── .gitignore
├── package.json
└── README.md
```

## ✨ Features

- Node.js + Express API
- Static frontend served via Express
- Dockerized using multi-stage builds
- Jest + Supertest for automated testing
- GitHub Actions for CI/CD
- DockerHub for image storage
- Clean Git-based deployment strategy

---

## 🧪 How to Run the App Locally

```bash
# 1. Install dependencies
npm install

# 2. Start the app
npm start

# 3. Run tests
npm test

# 4. Open your browser
http://localhost:3000

```

## 🐳 Docker Guide

### 🔨 Build Docker Image Locally

```bash
docker build -t my-node-app .
```

▶️ Run Docker Container Locally
```bash
docker run -p 3000:3000 my-node-app:
```


### ☁️ Run from DockerHub (CI/CD Image)

To pull and run the production image built via GitHub Actions:

```bash
docker run -p 3000:3000 dhanushnadar/my-node-app:build-{workflow-buildnumber}
```

> 🛠 Replace {workflow-buildnumber} with your actual build number (e.g., build-3).


## 🚦 CI/CD Pipeline using GitHub Actions

Defined in `.github/workflows/main.yml`

### ✅ Trigger
✔️ On merge from `dev` → `test`

### 🔁 Pipeline Steps
- ✅ Run **Jest** tests  
- 🐳 **Build** Docker image with tag: `build-<run_number>`  
- ☁️ **Push** image to DockerHub  
- 🔁 **Automatically merge** tested code from `test` → `main`

> This guarantees that `main` always has tested, reliable, production-ready code 🚀

---

## 🛠️ Git Production Strategy

### 📌 Branches

| Branch | Role                         |
|--------|------------------------------|
| `dev`  | Developer contributions      |
| `test` | QA/Test verification branch  |
| `main` | Production/stable code only  |

---

### 🔄 Flow

1. Developers push code to `dev` 🧑‍💻  
2. Testers validate and merge `dev` → `test` ✔️  
3. **GitHub Actions** kicks in:
   - ✅ Runs tests
   - 🛠 Builds and pushes Docker image
   - 🔄 Automatically merges `test` → `main`

---

### ✅ This Strategy Ensures:
- Code is **tested before hitting production**
- `main` stays **stable** and **trustworthy**
- CI/CD workflow is **clean**, **repeatable**, and **reliable**

## 🧠 Summary

With this setup:

- 🧑‍💻 Developers and testers have **isolated roles**
- ✅ Code is **tested** before going to production
- 🐳 Docker images are **versioned** and **reliable**
- 🔒 `main` always has **production-ready** code
- 🤖 Workflows are **automated** and **reproducible**

---

> Made with ❤️ using **Node.js**, **Docker**, **GitHub Actions**, and a love for clean **DevOps pipelines** by Dhanush Nadar.
