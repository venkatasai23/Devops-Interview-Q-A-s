# ⚙️ Kubernetes – Intermediate

---

## 1. ReplicaSet vs Deployment

- **ReplicaSet**: Ensures a set number of Pods.  
- **Deployment**: Manages ReplicaSets (rollouts, rollbacks).

---

## 2. ConfigMaps & Secrets

### ConfigMap

```bash
kubectl create configmap app-config --from-literal=LOG_LEVEL=debug

```

YAML:

```yaml

apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  LOG_LEVEL: debug
Mount in Pod:

```

```yaml

env:
- name: LOG_LEVEL
  valueFrom:
    configMapKeyRef:
      name: app-config
      key: LOG_LEVEL

```

Secret

```bash
kubectl create secret generic db-pass --from-literal=password='S3cr3t!'

```

### 3. Rolling Updates & Rollbacks

```bash

kubectl set image deployment/web nginx=nginx:1.22
kubectl rollout status deployment/web
kubectl rollout undo deployment/web

```

### 4. Probes: liveness & readiness

``` yaml

livenessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 5
readinessProbe:
  tcpSocket:
    port: 8080
  initialDelaySeconds: 3

```

### 5. Namespaces

```bash

kubectl create namespace dev
kubectl get pods --namespace=dev

```
