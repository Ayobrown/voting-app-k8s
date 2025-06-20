# 🗳️ Voting App - Kubernetes Deployment

This project contains Kubernetes manifests for deploying a microservices-based voting application using custom Docker images and open-source services like Redis and PostgreSQL.

---

## 📦 Project Components

| Component       | Description                                         |
|----------------|-----------------------------------------------------|
| `voting-app`    | Frontend for users to cast votes (e.g., Cats vs Dogs) |
| `result-app`    | Frontend for displaying real-time results           |
| `worker`        | Background processor that reads from Redis and writes to PostgreSQL |
| `redis`         | Queue that temporarily stores votes (fast & in-memory) |
| `postgres`      | Relational database for permanent vote storage      |

---

## 📂 Kubernetes YAML Files

| File                        | Purpose                              |
|-----------------------------|--------------------------------------|
| `voting-app-deploy.yaml`    | Deploys the voting frontend pod      |
| `voting-app-service.yaml`   | Exposes voting app via NodePort      |
| `result-app-deployment.yaml`| Deploys the result frontend pod      |
| `result-service.yaml`       | Exposes result app via NodePort      |
| `worker-deployment.yaml`    | Deploys the background worker        |
| `redis-deploy.yaml`         | Deploys the Redis pod                |
| `redis-service.yaml`        | Makes Redis available to other pods  |
| `postgres-deploy.yaml`      | Deploys the PostgreSQL pod           |
| `postgres-service.yaml`     | Makes PostgreSQL accessible internally|

---

## 🧪 How to Deploy

### 🛑 Prerequisites:
- A running Kubernetes cluster (Minikube or Docker Desktop with K8s enabled)
- `kubectl` configured
- (Optional) `minikube` CLI if you're using Minikube

### 🚀 Steps:

1. Clone the repository:
   ```bash
   git clone git@github.com:ayobrown/voting-app-k8s.git
   cd voting-app-k8s

2. Apply all YAML files: `kubectl apply -f .`

3. Get URL to access the voting and result app:
```bash
minikube service voting-service --url
minikube service result-service --url
