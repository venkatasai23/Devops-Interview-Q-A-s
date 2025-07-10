# 🔐 Docker – Advanced Level

---

## 1. Secure Docker Containers

- Use non-root users
- Restrict capabilities
- Read-only filesystems
- Use image scanning tools

---

### 2. Scan Docker Images

Tools:

- Trivy
- Snyk
- Docker Scout

---

### 3. What is Docker Content Trust?

Enables image signing and verification for integrity and authenticity.

Enable with:

```bash
export DOCKER_CONTENT_TRUST=1
```

### 4. Restrict Container Capabilities

Use:

docker run --cap-drop ALL ...

### 5. Prevent Running as Root

Use a non-root USER in Dockerfile and file permissions accordingly.

### 6. Docker Swarm

Native container orchestration. Key features:

Services

Scaling

Overlay networks

Rolling updates

### 7. Swarm vs Kubernetes

Feature Docker Swarm Kubernetes
Complexity Simpler More complex
Features Limited Rich ecosystem
Scalability Medium High

### 8. Initialize Swarm

docker swarm init

### 9. Service Discovery in Swarm

Automatic DNS-based service discovery across overlay networks.

### 10. Deploy Stack in Swarm

docker stack deploy -c docker-compose.yml mystack

### 11. docker run vs docker exec

run: Start new container

exec: Run inside existing one

### 12. Remove Unused Objects

docker system prune -a

### 13. Inspect Containers and Images

docker inspect <container_or_image>

### 14. docker ps Output

Shows running containers, ports, uptime, names.

### 15. Docker in CI/CD

Used for:

Building/pushing images

Running test suites

Deploying to environments

### 16. Docker with Jenkins

Build via Dockerfile

Test with docker-compose

Push to registry

### 17. Versioning Docker Images

Use tags like v1, latest, git-commit-sha
