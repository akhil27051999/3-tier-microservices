# 📦 Docker Image Build & Push to Docker Hub

**As part of deploying our microservices to Kubernetes, we containerized each service (frontend, backend, and PostgreSQL) and pushed the Docker images to Docker Hub so that they could be pulled and run by Kubernetes pods.**


## 🛠️ Steps to Build & Push Images

### 1. Docker Hub Account Setup

Ensure you have a Docker Hub account. We used the username: `akhilthyadi`.

---

### 2. Login to Docker Hub from CLI

```bash
docker login
```
Enter your Docker Hub username and personal access token (or password) when prompted.

---

### 3. Build Docker Images for Each Service

**Frontend:**

```bash
docker build -t akhilthyadi/frontend:v1 ./frontend
```

**Backend:**

```bash
docker build -t akhilthyadi/backend:v1 ./backend
```

**PostgreSQL (if customized Dockerfile used):**

```bash
docker build -t akhilthyadi/postgres:v1 ./postgres
```

---

### 4. Push Images to Docker Hub

```bash
docker push akhilthyadi/frontend:v1
docker push akhilthyadi/backend:v1
docker push akhilthyadi/postgres:v1
```

### 🔁 Image Usage in Kubernetes
In each Deployment YAML file, we referenced the images like this:

```yaml
containers:
  - name: backend
    image: akhilthyadi/backend:v1
```
This ensures Kubernetes pulls the images directly from Docker Hub during pod creation.

### Output:

![Screenshot 2025-05-24 141234](https://github.com/user-attachments/assets/43a0d941-751e-409a-a0fd-24c60d88b1f3)
