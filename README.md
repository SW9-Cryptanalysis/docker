# 🐳 Project Docker Environment

Welcome to the brains of the operation — the `docker/` repo! This is your one-stop shop to spin up the entire dev environment for decrypting ciphers using Docker Compose. Whether you're hacking on `homophonic-analyzer`, tweaking `???`, or running full system tests — you're in the right place.

---

## 📁 Project Structure

Here’s how the repos should be structured locally:
```
root/
 │ 
 ├── docker/ -- This repo!
 │      ├── docker-compose.yml 
 │ 
 └── homophonic-analyzer/
```

Each service has its own Dockerfile. The `docker-compose.yml` in the `docker/` folder manages and connects all services.

---

## Requirements

- Docker
- Docker Compose v2+
- Git (to make sure you're on the correct branch)

---

## Getting Started

1. **Ensure you have above project structure**:
Please check that all repos are up to date (at least dev or newer)

2. **Starting the system**:
from docker dir, run below command to start containers
```bash
docker compose up --build
```
To stop and remove containers run below command:
```bash
docker compose down -v
```
To clean up unused resources, run below command:
```bash
docker system prune -a --volumes
```

## Guide to Adding New Services
1. **Ensure Folder Structure**: Make sure your new service has its own folder with a Dockerfile.
2. **Update `docker-compose.yml`**: Add a new service entry in the `docker-compose.yml` file, specifying build context, ports, networks, and dependencies as needed.

Example:
```yaml
service1:
  build: 
    context: ./service1
    dockerfile: Dockerfile
  ports:
    - "8080:80"
  networks:
    - shared-network
  depends_on:
    - service2
```
3. **Rebuild and Restart**: After updating the `docker-compose.yml`, run `docker compose up --build` to rebuild and start your services.

---