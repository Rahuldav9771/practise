# Kubernetes Practice Manifests

This repository contains Kubernetes (`apps/v1`) Deployment manifests for practicing container orchestration and deployment management using `kubectl`.

## 📁 Repository Structure

```
.
├── postgress-deploy.yml   # PostgreSQL Database Deployment
├── pgadmin-deploy.yml     # pgAdmin 4 Web GUI Deployment
└── deployment-firefox.yml # Web-based Firefox Browser Deployment
```

---

## 🚀 Manifest Details

### 1. PostgreSQL Database (`postgress-deploy.yml`)
* **Image**: `postgres:17.10`
* **Container Port**: `5432`
* **Environment Variables**:
  * `POSTGRES_USER`: `admin`
  * `POSTGRES_PASSWORD`: `admin@12345`
  * `POSTGRES_DB`: `mydatabase`

### 2. pgAdmin 4 Web Interface (`pgadmin-deploy.yml`)
* **Image**: `dpage/pgadmin4:latest`
* **Replicas**: `4`
* **Container Port**: `80`
* **Environment Variables**:
  * `PGADMIN_DEFAULT_EMAIL`: `admin@example.com`
  * `PGADMIN_DEFAULT_PASSWORD`: `admin@12345`

### 3. Firefox Web GUI (`deployment-firefox.yml`)
* **Image**: `jlesage/firefox`
* **Container Port**: `3001`

---

## 🛠️ Usage Instructions

### Prerequisites
* A running Kubernetes cluster ([Minikube](https://minikube.sigs.k8s.io/), [Kind](https://kind.sigs.k8s.io/), Docker Desktop Kubernetes, or remote cluster).
* `kubectl` CLI installed and configured.

### Deploying the Manifests

To apply all deployment manifests at once:
```bash
kubectl apply -f .
```

To apply manifests individually:
```bash
# Deploy PostgreSQL
kubectl apply -f postgress-deploy.yml

# Deploy pgAdmin 4
kubectl apply -f pgadmin-deploy.yml

# Deploy Firefox
kubectl apply -f deployment-firefox.yml
```

---

## 🔍 Verification & Troubleshooting

Check the status of deployed workloads:

```bash
# Check deployment status
kubectl get deployments

# List running pods
kubectl get pods

# View pod logs
kubectl logs -l app=myapp
kubectl logs -l app=pgadmin
kubectl logs -l app=firefox
```

To remove the deployments:
```bash
kubectl delete -f .
```
