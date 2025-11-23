# 🚀 Flask Hello World – Dockerized Project

This repository contains a simple **Flask Hello World application** packaged inside a Docker container.  
It demonstrates essential DevOps concepts such as building images, running containers, using volumes, and publishing to Docker Hub.

---

## 📁 Project Structure

```
.
├── app.py                 # Flask application
├── Dockerfile             # Docker build configuration
├── docker-compose.yml     # Compose for container orchestration
├── requirements.txt        # Project dependencies
└── README.md              # Documentation
```

---

## 🧰 Prerequisites

Before running the project, ensure you have:

- **Docker Desktop** installed  
  https://www.docker.com/products/docker-desktop  
- (Optional) **Docker Compose** installed  

---

# 🐳 Build & Run Using Docker

## 1️⃣ Build the Docker image

```bash
docker build -t itaimasias/flask-hello-world:latest .
```

Verify the image:

```bash
docker images
```

---

## 2️⃣ Create a persistent Docker volume

```bash
docker volume create flask_data
```

---

## 3️⃣ Run the container

If port 5000 is already in use (e.g., by Minikube), use port 5001:

```bash
docker run -d   -p 5001:5000   --name flask-container   -v flask_data:/app/data   itaimasias/flask-hello-world:latest
```

Now open:

👉 http://localhost:5001

Expected output:

```
Hello World
```

---

## 4️⃣ View container logs

```bash
docker logs flask-container
```

---

## 5️⃣ Stop & remove the container

```bash
docker stop flask-container
docker rm flask-container
```

Remove the volume (optional):

```bash
docker volume rm flask_data
```

---

# 🐙 Run with Docker Compose (Recommended)

To build and start the container with Compose:

```bash
docker-compose up --build
```

To stop:

```bash
docker-compose down
```

---

# 📤 Publish the Image to Docker Hub

Log in:

```bash
docker login
```

Push the image:

```bash
docker push itaimasias/flask-hello-world:latest
```

Your public Docker Hub image:  
👉 https://hub.docker.com/r/itaimasias/flask-hello-world

---

# 🧪 Testing the Application

### Browser
```
http://localhost:5001
```

### Curl test

```bash
curl http://localhost:5001
```

---

# 🧹 Useful Docker Commands

```bash
docker ps                # List running containers
docker ps -a             # List all containers
docker logs <name>       # Show logs
docker stop <name>       # Stop container
docker rm <name>         # Remove container
docker images            # List images
docker volume ls         # List volumes
```

---

# ✅ Summary

This project demonstrates essential DevOps workflows:

- Containerizing a Python app  
- Running with Docker & Compose  
- Using volumes for persistence  
- Publishing images to Docker Hub  
- Writing clear documentation  

The app is now ready for CI/CD pipelines, Kubernetes deployments, or further backend expansion.

---

If you want, I can also add:
🔥 GitHub Actions (CI/CD)  
🔥 Kubernetes manifests  
🔥 Helm chart  
🔥 Automated tests  
🔥 API extensions  
