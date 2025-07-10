# 🚀 Kubernetes – Advanced

---

## 1. StatefulSets vs Deployments

- **StatefulSet**: Stable network IDs & storage for each Pod (e.g., databases).  
- **Deployment**: Stateless workloads.

---

## 2. DaemonSets

Run a Pod on every Node (e.g., log collector):

```bash

kubectl create daemonset flusher --image=busybox -- /bin/sh -c "echo hello; sleep 3600"

```

### 3. Persistent Volumes & Claims

PV & PVC Example

```yaml

apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-demo
spec:
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /mnt/data
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-demo
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 5Gi
Attach in Pod:

```

```yaml

volumes:
- name: data
  persistentVolumeClaim:
    claimName: pvc-demo

```

### 4. Ingress

YAML for basic HTTP routing:

``` yaml

apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web-ingress
spec:
  rules:
  - host: example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: web
            port:
              number: 80
Apply and check:

```

```bash
kubectl apply -f ingress.yaml
kubectl get ingress

```

### 5. RBAC

Role & RoleBinding

```yaml

kind: Role
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  namespace: dev
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
---
kind: RoleBinding
apiVersion: rbac.authorization.k8s.io/v1
metadata:
  name: read-pods
  namespace: dev
subjects:
- kind: User
  name: jane
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io

```
