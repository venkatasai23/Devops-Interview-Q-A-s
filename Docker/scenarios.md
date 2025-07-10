# 🧪 Docker – Scenario-Based Questions

---

## 1. Container Keeps Restarting

Check logs:

``` bash

docker logs <container>

```

Check entrypoint, missing files, or health checks.

### 2. Port Not Accessible

Check:

docker ps

Port mapping

Firewall

Container’s internal service

### 3. Build Fails at Specific Layer

Inspect Dockerfile layer

Cache invalidation

Missing dependencies

### 4. Monitor Resource Usage

docker stats

### 5. Container Fails to Start

docker logs
docker inspect

### 6. Reduce Image Size (1GB → 200MB)

Use Alpine base image

Multi-stage builds

Remove caches/files

### 7. Persistent Storage Setup

docker volume create app_data
docker run -v app_data:/data ...

### 8. Services Can’t Communicate

Attach to same network

Use container names

Check DNS resolution

### 9. Run Container as Non-Root User

Dockerfile

RUN useradd -ms /bin/bash appuser
USER appuser

### 10. Docker Build Fails on npm install

Check:

Missing package.json

Permissions

Network/proxy issues

### 11. Logs Not Reaching Host

Check:

Log driver (json-file, fluentd, etc.)

Volume mounts

### 12. Missing Image Locally

docker pull imagename

### 13. Container Using Too Much Memory

Limit:

docker run --memory="512m" ...

### 14. Rollback to Previous Version

Use image tag/version:

docker run myapp:previous
