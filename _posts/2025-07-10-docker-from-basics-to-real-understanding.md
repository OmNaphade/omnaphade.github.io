---
title: "Docker: From Basics to Real Understanding"
date: 2026-07-10 05:48:00 +0530
categories: [devops, fundamentals]
tags: [docker, containers, virtualization, devops-basics]
---
# Docker: From Basics to Real Understanding

When I first started learning Docker, it felt simple.
Run a container → App works → Done.
But Docker is not just a tool — it’s a different way of thinking about applications.
---
What Docker Really Is
---
Docker uses LXC (Linux Containers) for containerization.

Its core purpose is simple:
- Package applications
- Ship them anywhere
- Run them consistently

***Build once. Run anywhere.***

Docker on Windows — What Actually Happens

A common misconception:
`Running Linux containers on Windows means Linux runs on Windows.`
Not exactly.

What actually happens:
- Docker creates a lightweight Linux Virtual Machine
- Containers run inside that VM
- So it's:
`Linux Container → Linux VM → Windows`

---
## Containers vs Virtual Machines

| Feature      | Containers                     | Virtual Machines        |
|--------------|-------------------------------|-------------------------|
| Isolation    | OS-level                      | Hardware-level          |
| OS           | Shared kernel                 | Separate OS             |
| Size         | Lightweight (MBs)             | Heavy (GBs)             |
| Boot Time    | Seconds                       | Minutes                 |
| Performance  | Near-native                   | Slight overhead         |
| Use Case     | Microservices, CI/CD          | Full OS applications    |

##### Key Insight
- Containers → Run applications
- VMs → Run operating systems

#### Containers vs Images
- Image → Blueprint / Template
- Container → Running instance of that image

##### Important behavior:
- Containers are process-driven
- When the process stops → container stops

Example:
```bash
docker run ubuntu
```
This exits immediately because no process is running.

Core Docker Commands
---

#### Run & Manage Containers

```bash
docker run image_name
docker ps
docker ps -a
docker stop <container>
docker rm <container>
```

#### Work with Images
```bash
docker images
docker pull image_name
docker rmi image_name
```

#### Understanding Container Behavior
Containers are not like VMs.

They are meant to:
- Run a specific process
- Exit when the process completes

Example:
```bash
docker run ubuntu sleep 5
```
`Container runs → sleeps → exits.`

Useful Runtime Options
---
#### Interactive Mode
```bash
docker run -it image_name
```
Detached Mode
```bash
docker run -d image_name
```
Port Mapping
```bash
docker run -p 80:8080 image_name
```
Volume Mounting
```bash
docker run -v /host/path:/container/path image_name
```
Debugging & Inspection
---
```bash
docker logs <container>
docker exec -it <container> bash
docker inspect <container>
```
Power Commands
---
Remove All Containers
```bash
docker rm -f $(docker ps -aq)
```
Remove All Images
```bash
docker rmi -f $(docker images -aq)
```
Dockerfile — Creating Your Own Image
---
A Dockerfile defines how your image is built.

Example:
```dockerfile
FROM openjdk:17-jdk-slim
WORKDIR /app
COPY app.jar .
CMD ["java", "-jar", "app.jar"]
```

Build & Run
```bash
docker build -t my-app .
docker run my-app
```
#### Image Lifecycle (Real Workflow)
1. Write code
2. Package (JAR, etc.)
3. Create Dockerfile
4. Build image
5. Run container
6. Push to Docker Hub

Custom Java App in Docker
---
Build JAR
```bash
javac Main.java
jar cfe app.jar Main Main.class
```
Run with Docker
```bash
docker build -t my-java-app .
docker run --rm my-java-app
```
Docker Compose — Multi-Container Setup
---
Instead of running multiple containers manually, use docker-compose.yml.

Example:
```yaml
version: "3"
services:
  db:
    image: postgres
  app:
    image: my-app
    ports:
      - "8080:8080"
```
Run everything:
```bash
docker-compose up
```
CMD vs ENTRYPOINT
---
- CMD → gets replaced
- ENTRYPOINT → gets appended

Example:
```dockerfile
ENTRYPOINT ["sleep"]
CMD ["5"]
```
Run:
```bash
docker run image 10
```
Result:
```
sleep 10
```
Key Takeaways
---
- Containers are process-based, not OS-based
- Images are templates, containers are runtime instances
- localhost inside Docker is not your machine
- Containers stop when their main process stops
- Docker simplifies packaging and deployment drastically

Final Thought
---
Docker is not just about commands.
It’s about changing how you think:

From:
- “Where is my app running?”

To:
- “What does my app need to run anywhere?”

Once you understand that shift, Docker stops being confusing — and starts becoming powerful.

