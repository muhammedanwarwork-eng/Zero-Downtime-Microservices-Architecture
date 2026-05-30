# 🚀 Zero-Downtime Microservices Architecture on Kubernetes

## 📌 Project Overview

This project demonstrates a complete Kubernetes-based microservices architecture designed for high availability, scalability, and self-healing.

The architecture includes:

* Frontend Application (Nginx)
* Backend Application
* MySQL Database
* Stateful Storage
* Kubernetes Services
* Ingress Routing
* ConfigMaps & Secrets
* Health Probes
* Namespace Isolation

The goal is to simulate a real-world production environment while applying Kubernetes best practices.

---

## 🏗️ Architecture

```text
                    Internet
                        │
                        ▼
                   Ingress
                        │
         ┌──────────────┴──────────────┐
         ▼                             ▼
    Frontend Service            Backend Service
         │                             │
         ▼                             ▼
  Frontend Deployment         Backend Deployment
                                      │
                                      ▼
                             MySQL StatefulSet
                                      │
                                      ▼
                                    PVC
```

---

## 🛠️ Technologies Used

* Kubernetes
* Minikube
* Docker
* Nginx
* MySQL 8
* ConfigMaps
* Secrets
* Services
* Ingress
* StatefulSets
* Persistent Volume Claims (PVC)
* Helm
* GitOps Concepts
* ArgoCD

---

## 📂 Project Structure

```text
.
├── mysql-statefulset.yaml
├── mysql-service.yaml
├── backend-config.yaml
├── backend-secret.yaml
├── backend-deployment.yaml
├── backend-service.yaml
├── frontend-deployment.yaml
├── frontend-service.yaml
├── ingress.yaml
└── README.md
```

---

## 🚀 Deployment Steps

### 1. Create Namespace

```bash
kubectl create namespace project
```

---

### 2. Deploy Database

```bash
kubectl apply -f mysql-statefulset.yaml -n project
kubectl apply -f mysql-service.yaml -n project
```

---

### 3. Deploy Backend Components

```bash
kubectl apply -f backend-config.yaml -n project
kubectl apply -f backend-secret.yaml -n project
kubectl apply -f backend-deployment.yaml -n project
kubectl apply -f backend-service.yaml -n project
```

---

### 4. Deploy Frontend Components

```bash
kubectl apply -f frontend-deployment.yaml -n project
kubectl apply -f frontend-service.yaml -n project
```

---

### 5. Deploy Ingress

```bash
kubectl apply -f ingress.yaml -n project
```

---

## 🔍 Validation Commands

### View Resources

```bash
kubectl get all -n project
```

### View PVC

```bash
kubectl get pvc -n project
```

### View Ingress

```bash
kubectl get ingress -n project
```

### View Services

```bash
kubectl get svc -n project
```

### View Pods

```bash
kubectl get pods -n project
```

---

## ❤️ Self-Healing Demonstration

Delete a backend pod:

```bash
kubectl delete pod <POD_NAME> -n project
```

Kubernetes automatically creates a replacement pod through the Deployment controller.

---

## 📈 Scaling Demonstration

Scale backend replicas:

```bash
kubectl scale deployment backend-deployment --replicas=5 -n project
```

Verify:

```bash
kubectl get pods -n project
```

The Service automatically load balances traffic across all replicas.

---

## 🔐 Configuration Management

### ConfigMap

Stores non-sensitive configuration:

```yaml
DB_HOST: mysql-service
```

### Secret

Stores sensitive data:

```yaml
DB_PASSWORD
```

---

## 💾 Persistent Storage

MySQL uses:

* StatefulSet
* Persistent Volume Claim (PVC)

Benefits:

* Stable storage
* Stable pod identity
* Data persistence after pod recreation

---

## 🌐 Networking

### Services

Provide stable network endpoints:

* frontend-service
* backend-service
* mysql-service

### Ingress

Routes external traffic:

```text
frontend.example.com
      ↓
frontend-service

frontend.example.com/api
      ↓
backend-service
```

---

## 🧠 Kubernetes Concepts Demonstrated

* Pods
* Deployments
* ReplicaSets
* Services
* ConfigMaps
* Secrets
* Namespaces
* Ingress
* DNS
* PVC
* StatefulSets
* Liveness Probes
* Readiness Probes
* Scaling
* Self-Healing
* GitOps Fundamentals
* ArgoCD Fundamentals
* Helm Fundamentals

---

## 🎯 Learning Outcomes

After completing this project, I gained practical experience with:

* Building Kubernetes applications
* Managing stateless workloads
* Managing stateful workloads
* Service discovery
* Persistent storage
* Health monitoring
* Traffic routing
* Scalability
* High availability
* GitOps concepts
* Production-ready Kubernetes architecture

---

## 👨‍💻 Author

**Muhammed Anwar**

Software Engineering Graduate (2024)

DevOps Engineer Learning Journey

Focused on:

* Linux
* Networking
* Docker
* Kubernetes
* CI/CD
* AWS
* GitOps
* Cloud Infrastructure

⭐ If you found this project useful, consider giving it a star.
