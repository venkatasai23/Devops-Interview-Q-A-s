# 📦 Docker Registry

---

## 1. What is a Private Docker Registry?

A self-hosted or cloud-based image repository (e.g., Harbor, AWS ECR).

---

### 2.Push/Pull from Docker Hub

```bash

docker login
docker push myrepo/image:tag
docker pull myrepo/image:tag

```

### 3.Authenticate with Private Registry

``` bash
docker login myregistry.com

```

### 4.Common Issues

1.Incorrect credentials

2.Image not tagged properly

3.Firewall or proxy restrictions
