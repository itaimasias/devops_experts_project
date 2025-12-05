# 📘 DevOps Experts Project – Flask Application (Docker + Kubernetes)

זהו פרויקט שמדגים יכולות DevOps בסיסיות ומתקדמות:
📦 Containerization עם Docker  
☸️ Orchestration עם Kubernetes  
📈 Scaling ו־Monitoring  
🔐 עבודה עם ConfigMaps, Secrets, HPA, CronJobs  

---

# 🚀 Phase 1 – Docker Containerization

## 📁 Project Structure
```
.
├── app.py
├── Dockerfile
├── docker-compose.yml
├── requirements.txt
└── k8s/          # Kubernetes manifests
```

---

## ▶️ Running the App with Docker

### 1️⃣ Build the Docker image
```bash
docker build -t itaimasias/flask-hello-world:latest .
```

### 2️⃣ Create a Docker volume
```bash
docker volume create flask_data
```

### 3️⃣ Run the container
```bash
docker run -d   -p 5001:5000   --name flask-container   -v flask_data:/app/data   itaimasias/flask-hello-world:latest
```

### 4️⃣ Access the app  
Open:  
http://localhost:5001

### 5️⃣ Stop and remove
```bash
docker stop flask-container
docker rm flask-container
```

---

## 🐳 Docker Compose
```bash
docker-compose up --build
docker-compose down
```

---

## 📤 Publish to Docker Hub
```bash
docker login
docker push itaimasias/flask-hello-world:latest
```

---

# ☸️ Phase 2 – Kubernetes Orchestration

בשלב זה נפרוס את האפליקציה על Minikube עם Deployment, Service, HPA, CronJob ועוד.

---

## 🏁 1. Start Minikube
```bash
minikube start --driver=docker
kubectl get nodes
```

---

## ⚙️ 2. Apply Kubernetes Manifests
מתוך התיקייה `k8s/`:

```bash
kubectl apply -f .
```

זה יוצר:

- Deployment (`flask-deployment`)
- Service (`flask-service`)
- ConfigMap
- Secret
- HPA
- CronJob

---

## 🔍 3. Verify Everything
```bash
kubectl get deploy
kubectl get svc
kubectl get pods
kubectl get hpa
kubectl get cronjob
```

---

## 🌐 4. Access Application via NodePort
```bash
minikube service flask-service --url
```

הפקודה תחזיר URL כגון:
```
http://127.0.0.1:55387
```

---

## 📈 5. Horizontal Pod Autoscaler (HPA)
יש להפעיל את metrics-server:
```bash
minikube addons enable metrics-server
```

---

## ⏰ 6. CronJob
בדיקת ה־CronJob:
```bash
kubectl get jobs
kubectl get pods | grep flask-healthcheck
```

---

# ✔️ Summary

### 🚀 Phase 1 – Docker
- Containerization  
- Volumes  
- Docker Compose  
- Image publishing  

### ☸️ Phase 2 – Kubernetes
- Deployment + ReplicaSet  
- Service (NodePort)  
- HPA  
- ConfigMap  
- Secret  
- CronJob  
- Liveness & Readiness Probes  
- Minikube orchestration  

---

זהו README מלא, מקצועי וברור – מוכן להגשה 👍  
