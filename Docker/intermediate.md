# 🐳 Docker – Intermediate Level

---

## 1. Docker Networks

- **bridge**: Default network for containers on a single host.
- **host**: Shares the host’s networking namespace.
- **none**: Disables networking for the container.
- **overlay**: Enables multi-host networking (used with Docker Swarm).

---

## 2. Container-to-Container Communication

- Use a user-defined bridge or overlay network.
- Containers can resolve each other by name within the same network.

---

## 3. Expose Container Port to Host

```bash

docker run -p 8080:80 nginx

```

Maps port 80 in the container to port 8080 on the host.

---

## 4. Inter-Container Communication

- Attach both containers to the same Docker network.
- They can communicate using container names as hostnames.

---

## 5. What is a Bridge Network?

- The default network type for single-host Docker setups.
- Provides NAT and DNS-based container name resolution.

---

## 6. Volumes vs Bind Mounts

| Feature      | Volumes         | Bind Mounts      |
|--------------|----------------|------------------|
| Managed by   | Docker         | Host OS          |
| Use case     | Portable data  | Dev/debugging    |
| Backup       | Easy           | Manual           |

---

## 7. Create and Mount a Volume

```bash
docker volume create data_vol
docker run -v data_vol:/data busybox
```

---

## 8. Where Are Volumes Stored?

Volumes are stored under:

/var/lib/docker/volumes/

---

## 9. What Happens When a Container Using a Volume is Removed?

- The volume persists until explicitly deleted.

```bash
docker volume rm <volume>
```

---

## 10. Can Volumes Be Shared?

- Yes. Mount the same volume in multiple containers for shared data.

---

## 11. What is Docker Compose?

- A tool to define and run multi-container Docker applications using a `docker-compose.yml` file.

---

## 12. Purpose of `docker-compose.yml`

- Defines services, networks, volumes, and configuration for your application.

---

## 13. Scale Services in Compose

```bash
docker-compose up --scale web=3
```

Scales the `web` service to 3 instances.

---

## 14. Override Config in Compose

- Use multiple `docker-compose.override.yml` files or environment variables to override configuration.

---

## 15. `depends_on` vs `links`

- **depends_on**: Specifies the startup order of services.
- **links**: Legacy feature for inter-container communication (not recommended for new projects).
