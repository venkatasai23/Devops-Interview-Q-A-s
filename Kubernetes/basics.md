# 🧩 Kubernetes – Basics

---

## 1. What Is Kubernetes?

Kubernetes (K8s) is an open‑source container orchestration platform for automating deployment, scaling, and management of containerized applications.

---

## 2. Key Concepts

- **Pod**: Smallest deployable unit (one or more containers).  
- **Node**: Worker machine (VM or physical).  
- **Cluster**: Master(s) + Node(s).  
- **Control Plane**: API server, etcd, scheduler, controller-manager.  
- **kubectl**: CLI to interact with the API server.

---

## 3. Deploying a Pod

```bash
kubectl run nginx --image=nginx:1.21 --restart=Never
kubectl get pods
```

### 4. YAML vs Imperative

Imperative

```bash

kubectl create deployment web --image=nginx

```

Declarative (YAML)

```yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx:1.21

```

```bash
kubectl apply -f deployment.yaml

```

### 5. Services

Expose Pods via a stable network endpoint:

```bash
kubectl expose deployment web --port=80 --target-port=80 --type=ClusterIP
kubectl get svc

```
