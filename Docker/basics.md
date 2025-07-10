# 🐳 Docker – Basics

---

## 1. What is Docker and why is it used?

Docker is a platform for building, running, and managing containers. It enables the creation of lightweight, portable, and consistent environments across development, testing, and production.

---

### 2. Difference Between a Container and a Virtual Machine

| Feature        | Container                  | Virtual Machine             |
|----------------|---------------------------|-----------------------------|
| OS Overhead    | Shares host OS             | Full guest OS               |
| Speed          | Faster                     | Slower                      |
| Isolation      | Process-level isolation    | Full isolation              |
| Resource Usage | Lightweight                | Heavy                       |

---

### 3. Key Components of Docker

- **Docker Engine**: Core client-server technology.
- **Images**: Blueprints for containers.
- **Containers**: Running instances of images.
- **Registry**: Stores and shares images (e.g., Docker Hub).
- **Dockerfile**: Script to build images.

---

### 4. Docker Architecture

- **Docker Client**: Sends commands to the Docker Daemon.
- **Docker Daemon**: Builds, runs, and manages containers.
- **Docker Registry**: Stores Docker images.

---

### 5. Docker Image vs Container

- **Image**: Read-only template with application and dependencies.
- **Container**: Runnable instance of an image (isolated process).

---

### 6. What is Docker Hub?

A public registry for Docker images. You can pull official images (e.g., `nginx`, `ubuntu`) or push your own.

---

### 7. Install Docker on Linux

```bash
sudo apt update
sudo apt install docker.io
sudo systemctl enable docker
sudo systemctl start docker
```

---

### 8. Create a Docker Image

```bash
docker build -t myapp:v1 .
```

---

### 9. What is a Dockerfile? Example

A Dockerfile is a script containing instructions to build a Docker image.

```dockerfile
FROM ubuntu
RUN apt update && apt install -y nginx
CMD ["nginx", "-g", "daemon off;"]
```

---

### 10. Best Practices for Dockerfile

- Use minimal base images (e.g., `alpine`).
- Combine commands using `&&` to reduce layers.
- Use `.dockerignore` to exclude unnecessary files.
- Leverage multi-stage builds for smaller images.

---

### 11. ADD vs COPY

- **COPY**: Simple file/directory copy from host to image.
- **ADD**: Like COPY, but also supports remote URLs and auto-extracts archives.

---

### 12. Optimize Docker Images

- Use minimal base images (e.g., `alpine`).
- Clean up temporary files in the same layer.
- Use multi-stage builds to reduce image size.

---

### 13. What is Multi-Stage Build?

A technique to use multiple `FROM` statements in a Dockerfile to build and compile in one stage and deploy in another, reducing the final image size.

---

### 14. Run a Container

```bash
docker run -d -p 80:80 nginx
```

---

### 15. Start/Stop/Restart/Remove Containers

```bash
docker start <container_id>
docker stop <container_id>
docker restart <container_id>
docker rm <container_id>
```

---

### 16. View Container Logs

```bash
docker logs <container_id>
```

---

### 17. Access a Running Container

```bash
docker exec -it <container_id> /bin/bash
```

---

### 18. ENTRYPOINT vs CMD

- **ENTRYPOINT**: Always runs as the main command; cannot be overridden at runtime.

- **CMD**: Provides default arguments to ENTRYPOINT or runs if ENTRYPOINT is not specified; can be overridden at runtime.
