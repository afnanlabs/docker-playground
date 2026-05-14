# Docker: Complete Learning Roadmap
### From Absolute Beginner to Expert — A Structured Course with Commands, Examples & Projects

---

> **How to use this document:**
> Read each stage in order. Build every project. Run every command.
> Use the 📝 **Mini Notes** sections to copy into your own notes app.
> Docker is learned by doing — reading alone is not enough.

---

## Table of Contents

- [Stage 1 — Beginner](#stage-1--beginner)
- [Stage 2 — Intermediate](#stage-2--intermediate)
- [Stage 3 — Advanced](#stage-3--advanced)
- [Stage 4 — Expert](#stage-4--expert)

---

---

# STAGE 1 — BEGINNER

> **What this level means:**
> You have never used Docker. You may have heard the phrase "it works on my machine." By the end of this stage, you will understand what Docker is, why it exists, how containers work, and be able to pull images, run containers, and issue basic commands confidently.

**⏱️ Estimated Time: 1–2 weeks** (2–3 hours per day)

---

## 1.1 The Problem Docker Solves

Imagine you build a Node.js application on your laptop. It runs perfectly. You send it to a colleague, and it crashes immediately. They have a different version of Node.js, different operating system libraries, or different environment variables.

This is the **"it works on my machine"** problem — one of the most frustrating problems in software development.

**Docker solves this by packaging your application AND everything it needs to run into a single portable unit called a container.**

### Real-World Analogy

Think of a **shipping container** on a cargo ship. Before standardized containers, loading goods onto ships was chaotic — different sizes, shapes, fragile items mixed with heavy ones. When standardized metal containers were introduced, it didn't matter what was inside. Any ship could carry any container. Any port could load/unload any container.

Docker containers work the same way:
- Your app is packed inside a container with all its dependencies
- That container runs the same way on your laptop, a colleague's Windows PC, a Linux server, or a cloud platform
- The "ship" (the machine running it) doesn't care what's inside

---

## 1.2 What is Docker?

**Docker** is an open-source platform for developing, shipping, and running applications inside **containers.**

Docker was released in 2013 and changed how software is built and deployed. It is now used by virtually every tech company in the world.

Docker consists of:

| Component | What it is |
|-----------|-----------|
| **Docker Engine** | The core runtime that creates and runs containers |
| **Docker CLI** | The command-line tool you use to interact with Docker |
| **Docker Hub** | A public registry where Docker images are stored and shared |
| **Docker Desktop** | A GUI app for macOS and Windows that includes everything |
| **Docker Compose** | A tool for running multi-container applications |

---

## 1.3 Containers vs Virtual Machines

This is one of the most important concepts to understand early.

### Virtual Machines (VMs)

A VM emulates an entire computer, including its own operating system kernel, virtual hardware (CPU, RAM, disk), and all system libraries. Each VM is a full OS running inside your OS.

```
┌─────────────────────────────────────────┐
│            Your Machine (Host OS)        │
│  ┌──────────────┐  ┌──────────────────┐ │
│  │   VM 1       │  │    VM 2          │ │
│  │  ┌────────┐  │  │  ┌────────────┐  │ │
│  │  │ App A  │  │  │  │   App B    │  │ │
│  │  │ Libs   │  │  │  │   Libs     │  │ │
│  │  │ OS     │  │  │  │   OS       │  │ │
│  │  └────────┘  │  │  └────────────┘  │ │
│  └──────────────┘  └──────────────────┘ │
│           Hypervisor (VMware, VirtualBox) │
└─────────────────────────────────────────┘
```

### Containers

Containers share the **host OS kernel** but isolate everything else. They are much lighter and faster.

```
┌──────────────────────────────────────────────────┐
│               Your Machine (Host OS)              │
│                                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌────────┐ │
│  │ Container 1  │  │ Container 2  │  │ Cont 3 │ │
│  │  App A       │  │  App B       │  │ App C  │ │
│  │  Libs        │  │  Libs        │  │ Libs   │ │
│  └──────────────┘  └──────────────┘  └────────┘ │
│                                                  │
│              Docker Engine (shared kernel)        │
└──────────────────────────────────────────────────┘
```

### Comparison Table

| Feature | Container | Virtual Machine |
|---------|-----------|----------------|
| Startup time | Milliseconds | Minutes |
| Size | Megabytes | Gigabytes |
| OS | Shares host kernel | Own full OS |
| Isolation | Process-level | Hardware-level |
| Performance | Near-native | Overhead |
| Portability | Excellent | Good |
| Use case | Apps, microservices | Full OS, legacy apps |

---

## 1.4 Docker Architecture

```
┌───────────────────────────────────────────────────────┐
│                   Docker Client (CLI)                  │
│              docker run, docker build, etc.            │
└───────────────────────┬───────────────────────────────┘
                        │ REST API
┌───────────────────────▼───────────────────────────────┐
│                   Docker Daemon (dockerd)              │
│         Manages images, containers, networks,          │
│         volumes, and communicates with the OS          │
└───────┬──────────────────────────────┬────────────────┘
        │                              │
┌───────▼──────┐              ┌────────▼──────────┐
│ Local Images │              │  Docker Registry  │
│ (image cache)│              │  (Docker Hub, ECR)│
└──────────────┘              └───────────────────┘
```

- **Docker Client** — the `docker` CLI you type commands into
- **Docker Daemon** — the background service that does the actual work
- **Docker Registry** — where images are stored (Docker Hub is the public one)

---

## 1.5 Images vs Containers

This distinction is fundamental. Many beginners confuse the two.

| | Image | Container |
|---|-------|-----------|
| **What it is** | A blueprint / template | A running instance of an image |
| **Analogy** | A class in OOP | An object/instance of that class |
| **Another analogy** | A recipe | The actual cooked dish |
| **State** | Read-only, static | Running, has state |
| **Created by** | `docker build` | `docker run` |

One image can spawn **many containers.** If you have an `nginx` image, you can run 10 separate nginx containers from it.

---

## 1.6 Installing Docker

### Docker Desktop (macOS and Windows)

1. Go to [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Download and install for your operating system
3. Start Docker Desktop
4. Open a terminal and verify:

```bash
docker --version
# Docker version 24.x.x, build xxxxxxx

docker info
# Shows system-wide information about Docker
```

### Linux (Ubuntu)

```bash
# Update package index
sudo apt-get update

# Install Docker
sudo apt-get install -y docker.io

# Start Docker service
sudo systemctl start docker
sudo systemctl enable docker

# Add your user to the docker group (so you don't need sudo every time)
sudo usermod -aG docker $USER

# Log out and back in, then verify
docker --version
```

---

## 1.7 Docker Hub

**Docker Hub** is the world's largest public container registry. It's where official images for Node.js, Python, Nginx, MySQL, Redis, and thousands of others live.

Think of it as **npm for Docker images** — a central place to find and share images.

- Website: [hub.docker.com](https://hub.docker.com)
- Free account gives you unlimited public repos + 1 private repo
- Official images are maintained by the software's creators or Docker

### Image Naming Convention

```
[registry/][username/]image-name[:tag]

Examples:
  nginx                        → official nginx, latest tag
  nginx:1.25                   → nginx version 1.25
  node:20-alpine               → Node.js 20 on Alpine Linux
  postgres:15                  → PostgreSQL 15
  myusername/my-app:v1.0       → your custom image on Docker Hub
  ghcr.io/user/app:latest      → GitHub Container Registry
```

The **tag** is a version label. If you don't specify one, Docker uses `latest` by default.

---

## 1.8 Core Docker Commands

### Pulling and Running Images

```bash
# Pull an image from Docker Hub (downloads it locally)
docker pull nginx

# Run a container from an image
docker run nginx

# Run a container in detached mode (background)
docker run -d nginx

# Run with a name
docker run -d --name my-nginx nginx

# Run and map ports (host:container)
docker run -d -p 8080:80 --name my-nginx nginx
# Now visit http://localhost:8080 in your browser

# Run interactively with a terminal
docker run -it ubuntu bash
# -i = interactive, -t = allocate a terminal
# Now you're inside the Ubuntu container!
# Type 'exit' to leave
```

### Container Management

```bash
# List running containers
docker ps

# List ALL containers (including stopped ones)
docker ps -a

# Stop a running container
docker stop my-nginx

# Start a stopped container
docker start my-nginx

# Restart a container
docker restart my-nginx

# Remove a stopped container
docker rm my-nginx

# Force remove a running container
docker rm -f my-nginx

# Remove all stopped containers
docker container prune
```

### Image Management

```bash
# List all local images
docker images

# Remove an image
docker rmi nginx

# Remove all unused images
docker image prune

# Remove all unused images (including tagged ones not referenced by any container)
docker image prune -a

# Search Docker Hub from CLI
docker search postgres
```

### Logs and Inspection

```bash
# View container logs
docker logs my-nginx

# Follow logs in real time (like tail -f)
docker logs -f my-nginx

# View last 50 lines of logs
docker logs --tail 50 my-nginx

# Inspect container details (IP, mounts, env vars, etc.)
docker inspect my-nginx

# View container resource usage (CPU, memory)
docker stats

# View stats for a specific container
docker stats my-nginx
```

### Executing Commands Inside a Running Container

```bash
# Open a bash shell inside a running container
docker exec -it my-nginx bash

# Run a single command inside a container
docker exec my-nginx ls /etc/nginx

# Run as a specific user
docker exec -u root -it my-nginx bash
```

---

## 1.9 Your First Container — Step by Step

Let's run a real web server and see it in action.

```bash
# Step 1: Pull the nginx image
docker pull nginx
# You'll see layers downloading. Each layer = one filesystem change.

# Step 2: Run it, map port 8080 on your machine to port 80 in the container
docker run -d -p 8080:80 --name my-first-nginx nginx

# Step 3: Check it's running
docker ps
# You'll see: CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES

# Step 4: Visit http://localhost:8080 in your browser
# You should see the default nginx welcome page!

# Step 5: Check the logs
docker logs my-first-nginx

# Step 6: Go inside the container
docker exec -it my-first-nginx bash
# You're now inside the container
ls /usr/share/nginx/html
# index.html  50x.html
cat /usr/share/nginx/html/index.html
exit

# Step 7: Stop and remove
docker stop my-first-nginx
docker rm my-first-nginx
```

---

## 1.10 Understanding Port Mapping

Port mapping is one of the most confusing topics for beginners. Let's make it clear.

```
YOUR MACHINE (host)         CONTAINER (isolated network)
                           ┌──────────────────────┐
  localhost:8080  ──────►  │  port 80 (nginx)     │
                           └──────────────────────┘
  localhost:3000  ──────►  ┌──────────────────────┐
                           │  port 3000 (node app) │
                           └──────────────────────┘
```

```bash
# Format: -p HOST_PORT:CONTAINER_PORT
docker run -p 8080:80 nginx      # your 8080 maps to container's 80
docker run -p 3000:3000 node-app # your 3000 maps to container's 3000
docker run -p 5432:5432 postgres # your 5432 maps to container's 5432

# Map to a specific interface (only accessible from localhost)
docker run -p 127.0.0.1:8080:80 nginx
```

The container has its own internal network. Without `-p`, nothing from outside can reach it.

---

## 1.11 Environment Variables

Many applications are configured through environment variables. Docker makes this easy.

```bash
# Pass a single environment variable
docker run -e NODE_ENV=production my-node-app

# Pass multiple environment variables
docker run \
  -e NODE_ENV=production \
  -e PORT=3000 \
  -e DB_HOST=localhost \
  my-node-app

# Read from a .env file
docker run --env-file .env my-node-app
```

Example `.env` file:
```
NODE_ENV=production
PORT=3000
DB_PASSWORD=supersecret
API_KEY=abc123
```

---

## 📝 Stage 1 Mini Notes

```
Docker = platform to build, ship, run apps in containers
Container = isolated process using host OS kernel
Image = blueprint; Container = running instance of image

Key difference from VMs:
  VMs = full OS, slow, heavy (GBs)
  Containers = shared kernel, fast, light (MBs)

Essential Commands:
  docker pull <image>          → download image from Docker Hub
  docker run <image>           → create and start a container
  docker run -d                → run in background (detached)
  docker run -p host:container → map ports
  docker run -e KEY=VAL        → set environment variable
  docker run -it <image> bash  → run interactively with terminal
  docker ps                    → list running containers
  docker ps -a                 → list all containers
  docker stop <name>           → stop container
  docker rm <name>             → remove container
  docker images                → list local images
  docker rmi <image>           → remove image
  docker logs <name>           → view container output
  docker exec -it <name> bash  → shell into running container
  docker inspect <name>        → detailed container info

Image naming: name:tag  (e.g., node:20-alpine, postgres:15)
Port mapping: -p 8080:80 means your machine's 8080 → container's 80
```

---

## ⚠️ Stage 1 Common Mistakes

- Confusing images and containers — images are static blueprints, containers are running instances.
- Forgetting `-d` flag — container runs in foreground and blocks your terminal.
- Not mapping ports — container is running but you can't reach it from your browser.
- Removing a container and wondering why data is gone — containers are ephemeral by default.
- Pulling without a tag and getting unexpected `latest` version.
- Running `docker rm` on a running container — use `docker rm -f` or stop it first.

---

## 🏋️ Stage 1 Practice Tasks

1. Install Docker Desktop and verify with `docker version` and `docker info`.
2. Pull and run an `nginx` container on port 8080. Visit it in your browser.
3. Pull and run a `postgres:15` container with environment variables `POSTGRES_PASSWORD=secret`.
4. Use `docker exec -it` to open a bash shell inside your running nginx container.
5. Run `docker stats` and observe CPU and memory usage.
6. Pull and run `hello-world` — read the output explaining what Docker just did.
7. Run an Ubuntu container interactively. Install `curl` inside it with `apt-get install curl`. Exit and remove the container.
8. Run two separate nginx containers on different host ports (8080 and 8081) simultaneously.

---

---

# STAGE 2 — INTERMEDIATE

> **What this level means:**
> You can pull and run existing images. Now you will learn to BUILD your own images using Dockerfiles, understand how Docker layers and caching work, persist data with volumes, and connect containers with networking.

**⏱️ Estimated Time: 2–3 weeks** (2–3 hours per day)

---

## 2.1 The Dockerfile

A **Dockerfile** is a text file with instructions for building a Docker image. Each instruction adds a new **layer** to the image.

### Basic Dockerfile Structure

```dockerfile
# Every Dockerfile starts with FROM — the base image
FROM node:20-alpine

# Set the working directory inside the container
WORKDIR /app

# Copy files from your machine into the container
COPY package*.json ./

# Run a command during the build process
RUN npm install

# Copy the rest of the application
COPY . .

# Document which port the container uses (informational only)
EXPOSE 3000

# The command to run when the container starts
CMD ["node", "server.js"]
```

### Key Dockerfile Instructions

| Instruction | Purpose | Example |
|-------------|---------|---------|
| `FROM` | Set the base image | `FROM node:20-alpine` |
| `WORKDIR` | Set working directory | `WORKDIR /app` |
| `COPY` | Copy files from host to image | `COPY . .` |
| `ADD` | Like COPY, but can also extract tarballs and fetch URLs | `ADD app.tar.gz /app` |
| `RUN` | Execute a command during build | `RUN npm install` |
| `CMD` | Default command when container starts (can be overridden) | `CMD ["node", "app.js"]` |
| `ENTRYPOINT` | Like CMD but harder to override — defines the executable | `ENTRYPOINT ["node"]` |
| `EXPOSE` | Document which port the app uses | `EXPOSE 3000` |
| `ENV` | Set environment variables | `ENV NODE_ENV=production` |
| `ARG` | Build-time variable (not available at runtime) | `ARG VERSION=1.0` |
| `VOLUME` | Declare a volume mount point | `VOLUME ["/data"]` |
| `USER` | Set the user to run commands as | `USER node` |
| `LABEL` | Add metadata to the image | `LABEL version="1.0"` |

---

## 2.2 Building Your First Custom Image

### Project: Dockerize a Node.js App

Create this project structure:

```
my-node-app/
  ├── server.js
  ├── package.json
  └── Dockerfile
```

**`package.json`:**
```json
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js"
  },
  "dependencies": {
    "express": "^4.18.0"
  }
}
```

**`server.js`:**
```javascript
const express = require('express');
const app = express();
const PORT = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.json({
    message: 'Hello from Docker!',
    environment: process.env.NODE_ENV || 'development',
    hostname: require('os').hostname()  // shows container ID
  });
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

**`Dockerfile`:**
```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

### Building and Running

```bash
# Build the image (from inside my-node-app/ directory)
# -t = tag (name:version)  . = build context (current directory)
docker build -t my-node-app:1.0 .

# Watch the output — each step is one Dockerfile instruction
# STEP 1/7 : FROM node:20-alpine
# STEP 2/7 : WORKDIR /app
# ...

# List your images — you should see my-node-app
docker images

# Run a container from your new image
docker run -d -p 3000:3000 --name my-app my-node-app:1.0

# Test it
curl http://localhost:3000
# or open in browser

# Check logs
docker logs my-app
```

---

## 2.3 Docker Layers and Caching

This is one of the most important concepts for writing efficient Dockerfiles.

Every instruction in a Dockerfile creates a **layer**. Layers are cached. When you rebuild, Docker reuses unchanged layers and only rebuilds from the first changed layer downward.

```
FROM node:20-alpine          → Layer 1 (downloaded once, cached forever)
WORKDIR /app                 → Layer 2 (tiny, cached)
COPY package*.json ./        → Layer 3 (only re-runs if package.json changes)
RUN npm install              → Layer 4 (expensive — only re-runs if Layer 3 changes)
COPY . .                     → Layer 5 (changes every time you edit code)
CMD ["node", "server.js"]    → Layer 6 (cached)
```

### Why order matters

```dockerfile
# ❌ BAD — npm install re-runs every time ANY file changes
FROM node:20-alpine
WORKDIR /app
COPY . .           ← copies everything first
RUN npm install    ← runs after any file change

# ✅ GOOD — npm install only re-runs when package.json changes
FROM node:20-alpine
WORKDIR /app
COPY package*.json ./   ← copy package.json first
RUN npm install         ← cached unless package.json changed
COPY . .                ← source code changes don't invalidate npm install cache
```

### Checking the Build Cache

```bash
# Rebuild without cache (force rebuild all layers)
docker build --no-cache -t my-node-app:1.0 .

# See the layers of an image
docker history my-node-app:1.0
```

---

## 2.4 The .dockerignore File

Just like `.gitignore`, a `.dockerignore` file tells Docker which files to **exclude** from the build context.

```
# .dockerignore
node_modules/       # Don't copy node_modules — rebuild inside container
.git/               # Don't copy git history
.env                # Don't copy secret env files
*.log               # Don't copy log files
.DS_Store           # macOS metadata
dist/               # Don't copy build output (will be generated during build)
coverage/           # Test coverage reports
README.md
```

Without `.dockerignore`, Docker sends your entire `node_modules` folder (potentially hundreds of MB) to the Docker daemon unnecessarily. Always create this file.

---

## 2.5 Volumes — Persistent Data

Containers are **ephemeral** — when you remove a container, all data inside it is lost. **Volumes** solve this by storing data outside the container.

```
┌─────────────────────────────────────────────┐
│              Your Machine                    │
│                                             │
│  /var/lib/docker/volumes/my-data/           │
│                    │                        │
│         ┌──────────┼──────────────┐         │
│         │          │              │         │
│  ┌──────▼──────┐   │   ┌──────────▼─────┐  │
│  │ Container 1  │   │   │  Container 2   │  │
│  │  /app/data   │   │   │  /app/data     │  │
│  └─────────────┘       └────────────────┘  │
└─────────────────────────────────────────────┘
```

### Named Volumes (managed by Docker)

```bash
# Create a named volume
docker volume create my-data

# List volumes
docker volume ls

# Run container with a named volume
docker run -d \
  -p 5432:5432 \
  -e POSTGRES_PASSWORD=secret \
  -v my-data:/var/lib/postgresql/data \
  --name my-postgres \
  postgres:15

# The database data is now stored in the volume
# Even if you delete the container, the data survives

# Inspect a volume (see where it's stored on host)
docker volume inspect my-data

# Remove a volume
docker volume rm my-data

# Remove all unused volumes
docker volume prune
```

### Bind Mounts (map a specific host directory)

```bash
# Map a host directory to a container directory
# Changes in the host directory are reflected immediately in the container
docker run -d \
  -p 3000:3000 \
  -v $(pwd)/src:/app/src \
  my-node-app:1.0

# This is extremely useful for development:
# Edit files on your machine → changes appear instantly in the container
# No need to rebuild the image on every code change
```

### Volume vs Bind Mount

| | Named Volume | Bind Mount |
|---|-------------|-----------|
| **Managed by** | Docker | You |
| **Path on host** | `/var/lib/docker/volumes/...` | Any path you specify |
| **Best for** | Databases, persistent data | Development, live code reloading |
| **Portability** | High | Low (path depends on machine) |

---

## 2.6 Docker Networking

By default, Docker creates several networks. Every container can be connected to one or more networks.

```bash
# List Docker networks
docker network ls
# NETWORK ID   NAME      DRIVER    SCOPE
# abc123       bridge    bridge    local   ← default
# def456       host      host      local
# ghi789       none      null      local
```

### Network Drivers

| Driver | What it does |
|--------|-------------|
| `bridge` | Default. Containers on same bridge network can talk to each other by name |
| `host` | Container shares the host's network stack directly |
| `none` | No networking at all |
| `overlay` | For Docker Swarm / multi-host networking |

### Creating a Custom Network

```bash
# Create a custom bridge network
docker network create my-network

# Run containers on the same network
docker run -d \
  --name my-postgres \
  --network my-network \
  -e POSTGRES_PASSWORD=secret \
  postgres:15

docker run -d \
  --name my-app \
  --network my-network \
  -p 3000:3000 \
  my-node-app:1.0

# Now my-app can reach my-postgres using the hostname "my-postgres"
# e.g., DB_HOST=my-postgres in the Node.js app
# Docker's built-in DNS resolves container names to their IPs
```

### Why use custom networks?

On the **default bridge network**, containers cannot reach each other by name — only by IP. On a **custom network**, Docker provides automatic DNS resolution so containers can reach each other by container name. Always use custom networks for multi-container setups.

---

## 2.7 CMD vs ENTRYPOINT

This confuses many developers. Here's the clear explanation:

```dockerfile
# CMD: default command, easily overridden
CMD ["node", "server.js"]

# To override CMD:
docker run my-image node other-script.js    # runs other-script.js instead

# ENTRYPOINT: the executable, not easily overridden
ENTRYPOINT ["node"]
CMD ["server.js"]   # default argument to ENTRYPOINT

# This runs: node server.js
docker run my-image

# Override CMD argument (still uses node as ENTRYPOINT)
docker run my-image other-script.js        # runs: node other-script.js
```

### Common Pattern

```dockerfile
ENTRYPOINT ["docker-entrypoint.sh"]   # runs a startup script
CMD ["node", "server.js"]             # default arguments to the script
```

---

## 2.8 Multi-Stage Builds

Multi-stage builds let you use multiple `FROM` statements. The final image only includes what you copy from earlier stages — great for keeping production images small.

### Example: Building a React App

```dockerfile
# Stage 1: Build
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
# /app/dist now contains the built static files

# Stage 2: Serve (the final image)
FROM nginx:alpine
# Copy ONLY the built files from the builder stage
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

```bash
docker build -t my-react-app .
docker images my-react-app
# SIZE: ~25MB instead of ~400MB (without multi-stage)
```

The final image contains only nginx and the built static files — no Node.js, no source code, no dev dependencies.

---

## 2.9 Dockerizing a Node.js App (Full Example)

```dockerfile
FROM node:20-alpine

# Install system dependencies if needed
RUN apk add --no-cache python3 make g++

# Create a non-root user (security best practice)
RUN addgroup -S appgroup && adduser -S appuser -G appgroup

WORKDIR /app

# Copy dependency files first (cache optimization)
COPY package*.json ./

# Install production dependencies only
RUN npm ci --only=production

# Copy application source
COPY . .

# Change ownership to non-root user
RUN chown -R appuser:appgroup /app

# Switch to non-root user
USER appuser

EXPOSE 3000

# Use exec form (not shell form) for proper signal handling
CMD ["node", "server.js"]
```

```bash
# Build
docker build -t my-node-app:prod .

# Run with environment variables and volume
docker run -d \
  --name my-app \
  -p 3000:3000 \
  -e NODE_ENV=production \
  -e DB_HOST=my-postgres \
  my-node-app:prod
```

---

## 2.10 Pushing Images to Docker Hub

```bash
# Log in to Docker Hub
docker login
# Enter your Docker Hub username and password

# Tag your image with your username/repository:tag
docker tag my-node-app:1.0 yourusername/my-node-app:1.0

# Push to Docker Hub
docker push yourusername/my-node-app:1.0

# Now anyone can pull it with:
docker pull yourusername/my-node-app:1.0
```

---

## 📝 Stage 2 Mini Notes

```
Dockerfile instructions:
  FROM     = base image
  WORKDIR  = set working directory
  COPY     = copy files into image
  RUN      = execute command at build time
  CMD      = default command at runtime (overridable)
  EXPOSE   = document port (informational only)
  ENV      = set environment variable
  USER     = run as specific user

Build command:
  docker build -t name:tag .

Layer caching rule:
  Copy package.json first → run npm install → copy rest of code
  This way npm install is only re-run when package.json changes

Volumes:
  Named volumes  → docker run -v my-vol:/container/path   (persistent data)
  Bind mounts    → docker run -v $(pwd):/app               (dev hot reload)

Networking:
  Always create custom networks for multi-container apps
  Containers on same network can reach each other by name
  docker network create my-network

.dockerignore = exclude node_modules, .git, .env from build context

Multi-stage builds:
  FROM ... AS builder  → build the app
  FROM nginx:alpine    → serve it (tiny final image)
```

---

## ⚠️ Stage 2 Common Mistakes

- Copying `node_modules` from host into the image — always add `node_modules/` to `.dockerignore`.
- Wrong layer order — copying all source code before `npm install` breaks caching.
- Running as root in production containers — always add a non-root `USER`.
- Forgetting `.dockerignore` — slow builds, accidentally including `.env` files.
- Using `npm install` in production instead of `npm ci` (`ci` is stricter and faster in CI).
- Not understanding that `EXPOSE` doesn't actually publish a port — you still need `-p`.
- Hardcoding secrets in the Dockerfile — never do `ENV DB_PASSWORD=secret` in a Dockerfile.

---

## 🏋️ Stage 2 Practice Tasks

1. Dockerize the Node.js Express app from the example above. Build and run it.
2. Create a `.dockerignore` file. Verify `node_modules` and `.git` are not included.
3. Intentionally put `COPY . .` before `RUN npm install`. Rebuild twice and observe the cache being invalidated.
4. Fix the order and rebuild — observe how the cache is now used for `npm install`.
5. Run a PostgreSQL container with a named volume. Insert some data. Delete the container. Recreate it with the same volume. Verify data survived.
6. Create a custom Docker network. Run a Node.js app and a PostgreSQL container on it. Verify the Node app can ping Postgres by container name.
7. Build a multi-stage Dockerfile for a React app (or a simple static HTML page served by nginx).
8. Push your Node.js image to Docker Hub.

---

---

# STAGE 3 — ADVANCED

> **What this level means:**
> You can build and run individual containers. Now you learn to orchestrate multiple containers together with Docker Compose, handle real-world full-stack application setups, implement production patterns, and debug complex issues.

**⏱️ Estimated Time: 3–4 weeks** (2–3 hours per day)

---

## 3.1 Docker Compose

**Docker Compose** is a tool for defining and running **multi-container** applications. Instead of typing long `docker run` commands, you define everything in a `docker-compose.yml` file.

### Without Compose (painful)

```bash
docker network create app-network

docker run -d \
  --name postgres \
  --network app-network \
  -e POSTGRES_DB=mydb \
  -e POSTGRES_USER=admin \
  -e POSTGRES_PASSWORD=secret \
  -v postgres-data:/var/lib/postgresql/data \
  postgres:15

docker run -d \
  --name backend \
  --network app-network \
  -p 3000:3000 \
  -e DB_HOST=postgres \
  -e DB_NAME=mydb \
  -e DB_USER=admin \
  -e DB_PASSWORD=secret \
  my-backend:latest

docker run -d \
  --name frontend \
  --network app-network \
  -p 80:80 \
  my-frontend:latest
```

### With Compose (clean)

```yaml
# docker-compose.yml
version: '3.8'

services:
  postgres:
    image: postgres:15
    environment:
      POSTGRES_DB: mydb
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
    volumes:
      - postgres-data:/var/lib/postgresql/data
    networks:
      - app-network

  backend:
    build: ./backend
    ports:
      - "3000:3000"
    environment:
      DB_HOST: postgres
      DB_NAME: mydb
      DB_USER: admin
      DB_PASSWORD: secret
    depends_on:
      - postgres
    networks:
      - app-network

  frontend:
    build: ./frontend
    ports:
      - "80:80"
    depends_on:
      - backend
    networks:
      - app-network

volumes:
  postgres-data:

networks:
  app-network:
    driver: bridge
```

```bash
# Start all services (build if needed)
docker compose up

# Start in detached mode
docker compose up -d

# Build and start
docker compose up --build

# Stop all services
docker compose down

# Stop and remove volumes (destroys data!)
docker compose down -v

# View status of all services
docker compose ps

# View logs of all services
docker compose logs

# Follow logs of a specific service
docker compose logs -f backend

# Execute a command in a running service
docker compose exec backend bash

# Rebuild a specific service
docker compose build backend

# Scale a service (run 3 instances of backend)
docker compose up --scale backend=3
```

---

## 3.2 Docker Compose — Full Stack Project

Let's build a real full-stack app: React + Node.js + PostgreSQL + Redis.

### Project Structure

```
full-stack-app/
  ├── docker-compose.yml
  ├── docker-compose.dev.yml
  ├── docker-compose.prod.yml
  ├── backend/
  │   ├── Dockerfile
  │   ├── Dockerfile.dev
  │   ├── package.json
  │   └── src/
  │       └── server.js
  └── frontend/
      ├── Dockerfile
      ├── Dockerfile.dev
      ├── package.json
      └── src/
```

### `docker-compose.yml` (base config)

```yaml
version: '3.8'

services:
  # PostgreSQL Database
  db:
    image: postgres:15-alpine
    restart: unless-stopped
    environment:
      POSTGRES_DB: ${POSTGRES_DB:-appdb}
      POSTGRES_USER: ${POSTGRES_USER:-admin}
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD:?DB password required}
    volumes:
      - pgdata:/var/lib/postgresql/data
      - ./backend/db/init.sql:/docker-entrypoint-initdb.d/init.sql
    networks:
      - backend-network
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U ${POSTGRES_USER:-admin}"]
      interval: 10s
      timeout: 5s
      retries: 5

  # Redis Cache
  redis:
    image: redis:7-alpine
    restart: unless-stopped
    volumes:
      - redisdata:/data
    networks:
      - backend-network
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 5s
      retries: 5

  # Node.js Backend API
  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile
    restart: unless-stopped
    environment:
      NODE_ENV: production
      PORT: 3000
      DB_HOST: db
      DB_PORT: 5432
      DB_NAME: ${POSTGRES_DB:-appdb}
      DB_USER: ${POSTGRES_USER:-admin}
      DB_PASSWORD: ${POSTGRES_PASSWORD:?DB password required}
      REDIS_HOST: redis
      REDIS_PORT: 6379
      JWT_SECRET: ${JWT_SECRET:?JWT secret required}
    ports:
      - "3000:3000"
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_healthy
    networks:
      - backend-network
      - frontend-network

  # React Frontend
  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile
    restart: unless-stopped
    ports:
      - "80:80"
    depends_on:
      - backend
    networks:
      - frontend-network

volumes:
  pgdata:
  redisdata:

networks:
  backend-network:
    driver: bridge
  frontend-network:
    driver: bridge
```

### `docker-compose.dev.yml` (development overrides)

```yaml
version: '3.8'

services:
  backend:
    build:
      context: ./backend
      dockerfile: Dockerfile.dev
    volumes:
      - ./backend/src:/app/src   # live reload
    environment:
      NODE_ENV: development
    command: npm run dev          # use nodemon

  frontend:
    build:
      context: ./frontend
      dockerfile: Dockerfile.dev
    volumes:
      - ./frontend/src:/app/src  # live reload
    ports:
      - "5173:5173"             # Vite dev server
    command: npm run dev
```

```bash
# Run development setup (combines base + dev overrides)
docker compose -f docker-compose.yml -f docker-compose.dev.yml up

# Or use an alias in your project
```

---

## 3.3 Health Checks

Health checks let Docker know if a container is actually healthy and ready, not just "running."

```yaml
# In docker-compose.yml
services:
  backend:
    image: my-backend
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s      # check every 30 seconds
      timeout: 10s       # fail if check takes > 10 seconds
      retries: 3         # mark unhealthy after 3 consecutive failures
      start_period: 40s  # don't start checking until 40s after start
```

```javascript
// Add a health endpoint to your Express app
app.get('/health', (req, res) => {
  res.status(200).json({
    status: 'healthy',
    uptime: process.uptime(),
    timestamp: new Date()
  });
});
```

---

## 3.4 Debugging Docker Containers

### Common Debugging Commands

```bash
# See why a container exited
docker ps -a
docker logs failed-container
docker inspect failed-container | grep -i "exitcode"

# Shell into a running container
docker exec -it my-container bash
# If bash isn't available (Alpine):
docker exec -it my-container sh

# Shell into a stopped container by running a new one from its image
docker run -it --entrypoint sh my-image

# Check container filesystem
docker exec my-container ls -la /app

# Check environment variables inside container
docker exec my-container env

# Check which processes are running
docker exec my-container ps aux

# Check network connectivity from inside a container
docker exec my-container curl http://other-service:3000
docker exec my-container ping other-container

# Copy files out of a container for inspection
docker cp my-container:/app/logs/error.log ./error.log

# Look at container events
docker events --filter container=my-container
```

### Debugging with a Temporary Container

```bash
# Attach a debug sidecar to an existing container's network namespace
docker run -it --network container:my-app nicolaka/netshoot
# Now you can run tcpdump, curl, dig, nmap, etc.

# Or just use Alpine with curl/wget
docker run -it --network my-network alpine sh
apk add curl
curl http://backend:3000/health
```

---

## 3.5 Docker with Databases

### PostgreSQL

```yaml
# docker-compose.yml
services:
  postgres:
    image: postgres:15-alpine
    environment:
      POSTGRES_DB: myapp
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
    volumes:
      - pgdata:/var/lib/postgresql/data
      # Run SQL scripts on first startup
      - ./init.sql:/docker-entrypoint-initdb.d/01-schema.sql
    ports:
      - "5432:5432"    # expose for local dev tools like DBeaver
```

```bash
# Connect to PostgreSQL inside the container
docker exec -it postgres-container psql -U postgres -d myapp

# Run a SQL file
docker exec -i postgres-container psql -U postgres -d myapp < migration.sql

# Dump database
docker exec postgres-container pg_dump -U postgres myapp > backup.sql

# Restore database
docker exec -i postgres-container psql -U postgres myapp < backup.sql
```

### MySQL

```yaml
services:
  mysql:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: rootsecret
      MYSQL_DATABASE: myapp
      MYSQL_USER: appuser
      MYSQL_PASSWORD: secret
    volumes:
      - mysqldata:/var/lib/mysql
    ports:
      - "3306:3306"
```

### MongoDB

```yaml
services:
  mongodb:
    image: mongo:7
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: secret
      MONGO_INITDB_DATABASE: myapp
    volumes:
      - mongodata:/data/db
    ports:
      - "27017:27017"
```

---

## 3.6 Image Optimization

### Use Alpine Base Images

```dockerfile
# Regular Node image: ~900MB
FROM node:20

# Alpine image: ~170MB
FROM node:20-alpine

# Even smaller — use specific version, not latest
FROM node:20.10-alpine3.18
```

### Use `npm ci` Instead of `npm install`

```dockerfile
# npm ci: uses exact versions from package-lock.json, faster in CI
RUN npm ci --only=production
```

### Remove Unnecessary Files

```dockerfile
FROM node:20-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production && \
    npm cache clean --force    # ← removes npm cache in the same layer
COPY . .
```

### Combine RUN Commands

```dockerfile
# ❌ Creates 3 separate layers
RUN apt-get update
RUN apt-get install -y curl
RUN rm -rf /var/lib/apt/lists/*

# ✅ One layer — and cleanup is in the same step
RUN apt-get update && \
    apt-get install -y curl && \
    rm -rf /var/lib/apt/lists/*
```

### Multi-Stage Build Recap

```dockerfile
# Stage 1: builder (big image, has all dev tools)
FROM node:20 AS builder
WORKDIR /app
COPY . .
RUN npm ci && npm run build

# Stage 2: production (tiny image, only what's needed to run)
FROM node:20-alpine
WORKDIR /app
COPY --from=builder /app/dist ./dist
COPY --from=builder /app/node_modules ./node_modules
EXPOSE 3000
CMD ["node", "dist/server.js"]
```

### Checking Image Sizes

```bash
docker images
docker history my-image:latest

# Use dive tool for layer-by-layer analysis
docker run --rm -it \
  -v /var/run/docker.sock:/var/run/docker.sock \
  wagoodman/dive my-image:latest
```

---

## 3.7 Container Security Basics

### 1. Run as Non-Root User

```dockerfile
FROM node:20-alpine

RUN addgroup -S appgroup && \
    adduser -S appuser -G appgroup

WORKDIR /app
COPY --chown=appuser:appgroup . .

USER appuser   # ← Switch to non-root BEFORE CMD
CMD ["node", "server.js"]
```

```bash
# Verify the user inside the container
docker exec my-container whoami
# should say "appuser", not "root"
```

### 2. Read-Only Filesystem

```bash
docker run --read-only my-image
# Container can't write anywhere except explicitly declared volumes
```

### 3. Limit Resources

```bash
docker run \
  --memory="512m" \
  --memory-swap="512m" \
  --cpus="0.5" \
  my-image
# Container gets max 512MB RAM and 50% of one CPU core
```

### 4. Drop Linux Capabilities

```bash
docker run --cap-drop=ALL --cap-add=NET_BIND_SERVICE my-image
# Drops all Linux capabilities except the ability to bind to ports < 1024
```

### 5. Scan Images for Vulnerabilities

```bash
# Docker Scout (built into Docker Desktop)
docker scout cves my-image:latest

# Or use Trivy
docker run --rm \
  -v /var/run/docker.sock:/var/run/docker.sock \
  aquasec/trivy image my-image:latest
```

### 6. Use Secrets, Not Environment Variables

For truly sensitive values (DB passwords, API keys), Docker Secrets are more secure:

```yaml
# docker-compose.yml
services:
  backend:
    secrets:
      - db_password
    environment:
      DB_PASSWORD_FILE: /run/secrets/db_password

secrets:
  db_password:
    file: ./secrets/db_password.txt
```

---

## 3.8 Docker Compose with Environment Files

```bash
# .env file (at same level as docker-compose.yml)
POSTGRES_DB=myapp
POSTGRES_USER=admin
POSTGRES_PASSWORD=secret123
JWT_SECRET=myjwtsecretkey
```

```yaml
# docker-compose.yml reads .env automatically
services:
  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: ${POSTGRES_PASSWORD}

  backend:
    environment:
      - JWT_SECRET=${JWT_SECRET}
```

```bash
# Use a different env file
docker compose --env-file .env.production up

# Validate your compose file
docker compose config
```

---

## 📝 Stage 3 Mini Notes

```
Docker Compose commands:
  docker compose up -d          → start all services (detached)
  docker compose up --build     → rebuild and start
  docker compose down           → stop and remove containers
  docker compose down -v        → also removes volumes
  docker compose ps             → status of services
  docker compose logs -f <svc>  → follow logs of a service
  docker compose exec <svc> sh  → shell into a service

depends_on with health checks:
  depends_on:
    db:
      condition: service_healthy

Health check: test, interval, timeout, retries, start_period

Multiple compose files:
  docker compose -f docker-compose.yml -f docker-compose.dev.yml up

Security checklist:
  ✅ Non-root USER in Dockerfile
  ✅ Read-only filesystem where possible
  ✅ Resource limits (--memory, --cpus)
  ✅ Scan images with Trivy or Docker Scout
  ✅ Never hardcode secrets — use .env or Docker Secrets

Image optimization:
  ✅ Alpine base images
  ✅ Multi-stage builds
  ✅ npm ci --only=production
  ✅ Combine RUN commands
  ✅ .dockerignore
```

---

## ⚠️ Stage 3 Common Mistakes

- Using `depends_on` without health checks — the app starts before the DB is ready and crashes.
- Not separating dev and prod compose files — same image with dev tools in production.
- Storing secrets in `docker-compose.yml` and committing to git.
- Not using `.env` files for configuration — hardcoded values in compose.
- Running the database and application on the same network (frontend should NOT access the DB directly).
- Not setting resource limits — one runaway container can take down the whole host.
- Image bloat — 1GB+ images when 50MB is achievable with multi-stage builds.

---

## 🏋️ Stage 3 Practice Tasks

1. Create a `docker-compose.yml` for a Node.js + PostgreSQL app. Add health checks for the database.
2. Add a Redis service to the compose file. Connect the backend to both Postgres and Redis.
3. Create separate `docker-compose.dev.yml` with bind mounts for hot reloading.
4. Add an `.env` file and use `${VARIABLE}` substitution in your compose file.
5. Add `USER` to your Dockerfile. Verify with `docker exec` that the container runs as non-root.
6. Use `docker compose --scale` to run 3 instances of the backend service.
7. Intentionally break something and practice using `docker compose logs`, `docker exec`, and `docker inspect` to diagnose.
8. Add a Trivy scan to verify your image has no critical vulnerabilities.

---

---

# STAGE 4 — EXPERT

> **What this level means:**
> You build and run production-grade Docker setups. You understand orchestration, CI/CD pipelines, monitoring, scaling, and how Docker fits into the modern DevOps workflow. You know when Docker is the right tool and when it's not.

**⏱️ Estimated Time: 4–6 weeks** (project-based, ongoing learning)

---

## 4.1 Container Orchestration — The Problem

Docker Compose is great for running containers on a **single machine.** But production applications need:

- **High availability** — if one server goes down, others take over
- **Auto-scaling** — add more containers when traffic spikes
- **Rolling updates** — deploy new versions with zero downtime
- **Self-healing** — automatically restart failed containers
- **Load balancing** — distribute traffic across multiple instances
- **Multi-host networking** — containers spread across multiple servers

This is where **container orchestration** tools come in.

```
Single machine (Docker Compose):
  [Server 1]
  ├── container: backend-1
  ├── container: frontend-1
  └── container: db-1

Multi-machine (Orchestration):
  [Server 1]          [Server 2]          [Server 3]
  ├── backend-1       ├── backend-2       ├── backend-3
  └── frontend-1      └── frontend-2      └── db-1 (primary)
                                          └── db-2 (replica)
```

---

## 4.2 Introduction to Docker Swarm

**Docker Swarm** is Docker's built-in orchestration tool. It is simpler than Kubernetes and suitable for smaller deployments.

```bash
# Initialize a swarm (on the manager node)
docker swarm init --advertise-addr <manager-ip>
# Outputs a token to join worker nodes

# On worker nodes:
docker swarm join --token <token> <manager-ip>:2377

# Deploy a stack (like compose, but on a swarm)
docker stack deploy -c docker-compose.yml my-app

# List services
docker service ls

# Scale a service
docker service scale my-app_backend=5

# Rolling update
docker service update --image my-backend:2.0 my-app_backend

# View service logs
docker service logs my-app_backend

# Remove the stack
docker stack rm my-app
```

---

## 4.3 Introduction to Kubernetes

**Kubernetes (K8s)** is the industry standard for container orchestration at scale. It is used by Netflix, Airbnb, Spotify, and almost every major tech company.

### Key Concepts

| Concept | What it is |
|---------|-----------|
| **Cluster** | A set of machines (nodes) running Kubernetes |
| **Node** | A single machine in the cluster (can be a VM or physical server) |
| **Pod** | The smallest deployable unit — one or more containers |
| **Deployment** | Manages a set of identical Pods, handles scaling and rollouts |
| **Service** | A stable network endpoint to reach a set of Pods |
| **Ingress** | HTTP routing rules — routes external traffic to Services |
| **ConfigMap** | Non-sensitive configuration data |
| **Secret** | Sensitive data (passwords, tokens) |
| **Namespace** | Virtual cluster within a cluster — for organizing resources |

### Kubernetes Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Kubernetes Cluster                        │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐   │
│  │                  Control Plane (Master)               │   │
│  │   API Server  │  Scheduler  │  Controller Manager     │   │
│  │                   etcd (cluster state)                │   │
│  └──────────────────────────────────────────────────────┘   │
│                          │                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐   │
│  │  Worker Node │  │  Worker Node │  │   Worker Node    │   │
│  │  ┌─────────┐ │  │  ┌─────────┐ │  │   ┌─────────┐   │   │
│  │  │  Pod    │ │  │  │  Pod    │ │  │   │   Pod   │   │   │
│  │  │[cont 1] │ │  │  │[cont 1] │ │  │   │ [cont]  │   │   │
│  │  └─────────┘ │  │  └─────────┘ │  │   └─────────┘   │   │
│  │   kubelet    │  │   kubelet    │  │    kubelet       │   │
│  └──────────────┘  └──────────────┘  └──────────────────┘   │
└─────────────────────────────────────────────────────────────┘
```

### Getting Started with Kubernetes (local)

```bash
# Install minikube (local Kubernetes)
# https://minikube.sigs.k8s.io

minikube start

# Install kubectl (Kubernetes CLI)
# https://kubernetes.io/docs/tasks/tools

# Basic kubectl commands
kubectl get nodes
kubectl get pods
kubectl get services
kubectl get deployments
kubectl get namespaces
```

### Deploying to Kubernetes

```yaml
# deployment.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: backend
  labels:
    app: backend
spec:
  replicas: 3                    # 3 instances
  selector:
    matchLabels:
      app: backend
  template:
    metadata:
      labels:
        app: backend
    spec:
      containers:
      - name: backend
        image: myusername/my-backend:1.0
        ports:
        - containerPort: 3000
        env:
        - name: NODE_ENV
          value: "production"
        - name: DB_PASSWORD
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: password
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 3000
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 3000
          initialDelaySeconds: 5
          periodSeconds: 5

---
# service.yml
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  selector:
    app: backend
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: ClusterIP
```

```bash
# Apply configuration
kubectl apply -f deployment.yml
kubectl apply -f service.yml

# Check status
kubectl get pods
kubectl describe pod backend-xyz-123

# Scale up
kubectl scale deployment backend --replicas=5

# Rolling update (zero downtime)
kubectl set image deployment/backend backend=myusername/my-backend:2.0

# Watch rollout progress
kubectl rollout status deployment/backend

# Rollback
kubectl rollout undo deployment/backend

# View logs
kubectl logs -f deployment/backend
```

---

## 4.4 CI/CD Integration with Docker

In modern software companies, every code push automatically builds, tests, and deploys a Docker image. This is CI/CD (Continuous Integration / Continuous Deployment).

### The CI/CD Pipeline Flow

```
Developer pushes code
        │
        ▼
  CI System runs:
  1. Checkout code
  2. docker build
  3. Run tests in container
  4. docker push (tag with commit SHA or version)
        │
        ▼
  CD System deploys:
  5. Pull new image on server(s)
  6. docker compose up --build (or kubectl apply)
  7. Health check passes
  8. Old containers removed
```

### GitHub Actions — Full CI/CD Pipeline

```yaml
# .github/workflows/deploy.yml
name: Build, Test, and Deploy

on:
  push:
    branches: [main]

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  build-and-push:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v4

    - name: Log in to GitHub Container Registry
      uses: docker/login-action@v3
      with:
        registry: ${{ env.REGISTRY }}
        username: ${{ github.actor }}
        password: ${{ secrets.GITHUB_TOKEN }}

    - name: Extract metadata (tags, labels)
      id: meta
      uses: docker/metadata-action@v5
      with:
        images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
        tags: |
          type=sha,prefix=sha-
          type=raw,value=latest,enable={{is_default_branch}}

    - name: Build and test
      run: |
        docker build -t test-image --target builder .
        docker run --rm test-image npm test

    - name: Build and push production image
      uses: docker/build-push-action@v5
      with:
        context: .
        push: true
        tags: ${{ steps.meta.outputs.tags }}
        labels: ${{ steps.meta.outputs.labels }}
        cache-from: type=gistry,ref=${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:buildcache
        cache-to: type=registry,ref=${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}:buildcache,mode=max

  deploy:
    needs: build-and-push
    runs-on: ubuntu-latest

    steps:
    - name: Deploy to server via SSH
      uses: appleboy/ssh-action@v1
      with:
        host: ${{ secrets.SERVER_HOST }}
        username: ${{ secrets.SERVER_USER }}
        key: ${{ secrets.SSH_PRIVATE_KEY }}
        script: |
          cd /opt/my-app
          docker compose pull
          docker compose up -d --remove-orphans
          docker image prune -f
```

---

## 4.5 Production Deployment Patterns

### Blue-Green Deployment

Run two identical environments (Blue = current live, Green = new version). Switch traffic from Blue to Green when ready.

```bash
# Bring up the new "green" version alongside the existing "blue"
docker compose -f docker-compose.green.yml up -d

# Test the green environment
curl https://green.myapp.com/health

# Switch the load balancer to green
# (update nginx or traefik config to point to green containers)

# Green is now live. Blue becomes standby.
# Tear down blue when confident
docker compose -f docker-compose.blue.yml down
```

### Rolling Update (with Docker Compose)

```bash
# Pull new image
docker compose pull backend

# Update without downtime (if you have multiple replicas)
docker compose up -d --no-deps backend

# For true zero-downtime rolling updates, use a reverse proxy
# like Traefik or Nginx that can rebalance as containers are replaced
```

### Using Traefik as a Reverse Proxy

```yaml
# docker-compose.yml with Traefik
services:
  traefik:
    image: traefik:v3.0
    command:
      - "--api.insecure=true"
      - "--providers.docker=true"
      - "--providers.docker.exposedbydefault=false"
      - "--entrypoints.web.address=:80"
      - "--entrypoints.websecure.address=:443"
    ports:
      - "80:80"
      - "443:443"
      - "8080:8080"  # Traefik dashboard
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock:ro

  backend:
    image: my-backend:latest
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.backend.rule=Host(`api.myapp.com`)"
      - "traefik.http.routers.backend.entrypoints=websecure"
      - "traefik.http.services.backend.loadbalancer.server.port=3000"
```

---

## 4.6 Monitoring Docker Containers

### Built-in Monitoring

```bash
# Real-time stats for all containers
docker stats

# Events stream
docker events

# System-wide disk usage
docker system df
```

### Prometheus + Grafana Stack

```yaml
# monitoring/docker-compose.yml
services:
  prometheus:
    image: prom/prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana
    ports:
      - "3001:3000"
    volumes:
      - grafana-data:/var/lib/grafana
    environment:
      GF_SECURITY_ADMIN_PASSWORD: admin

  cadvisor:
    image: gcr.io/cadvisor/cadvisor:latest
    volumes:
      - /:/rootfs:ro
      - /var/run:/var/run:ro
      - /sys:/sys:ro
      - /var/lib/docker/:/var/lib/docker:ro
    ports:
      - "8081:8080"
    # Exposes container metrics to Prometheus

volumes:
  grafana-data:
```

```yaml
# prometheus.yml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'cadvisor'
    static_configs:
      - targets: ['cadvisor:8080']
```

After setting this up: Prometheus scrapes metrics from cAdvisor, and Grafana displays dashboards of CPU, memory, network, and disk usage per container.

### Centralized Logging with Loki + Promtail

```yaml
services:
  loki:
    image: grafana/loki:latest
    ports:
      - "3100:3100"

  promtail:
    image: grafana/promtail:latest
    volumes:
      - /var/lib/docker/containers:/var/lib/docker/containers:ro
      - ./promtail-config.yml:/etc/promtail/config.yml
```

All container logs are shipped to Loki and viewable in Grafana.

---

## 4.7 Production Best Practices — Full Checklist

### Dockerfile Best Practices

```dockerfile
# ✅ Use specific version tags, never 'latest' in production
FROM node:20.10-alpine3.18

# ✅ WORKDIR before COPY
WORKDIR /app

# ✅ Separate dependency copy from source copy (caching)
COPY package*.json ./
RUN npm ci --only=production && npm cache clean --force

COPY . .

# ✅ Non-root user
RUN addgroup -S app && adduser -S app -G app
RUN chown -R app:app /app
USER app

# ✅ Use exec form for CMD
CMD ["node", "server.js"]

# ✅ Add meaningful labels
LABEL maintainer="team@company.com"
LABEL version="1.0.0"
LABEL description="Backend API service"
```

### Docker Compose Production Best Practices

```yaml
services:
  backend:
    image: registry.company.com/backend:${VERSION}  # pinned version
    restart: unless-stopped                          # auto-restart on crash
    read_only: true                                  # read-only filesystem
    security_opt:
      - no-new-privileges:true                       # prevent privilege escalation
    cap_drop:
      - ALL                                          # drop all capabilities
    cap_add:
      - NET_BIND_SERVICE                             # add only what's needed
    deploy:
      resources:
        limits:
          cpus: '0.50'
          memory: 512M
        reservations:
          cpus: '0.25'
          memory: 256M
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
    logging:
      driver: "json-file"
      options:
        max-size: "10m"
        max-file: "3"
```

---

## 4.8 Real-World Docker in Software Companies

### How Companies Use Docker

**Development:**
- Every developer runs the entire stack locally with `docker compose up`
- No more "install PostgreSQL, then Redis, then configure..." — one command starts everything
- New developers are productive on day one

**Testing:**
- CI pipeline builds a Docker image on every pull request
- Tests run inside containers — consistent environment
- Parallel test execution across containers

**Staging:**
- Staging environment mirrors production exactly — same Docker images, same compose config
- "If it works in staging, it works in production" actually holds true

**Production:**
- Images built once, deployed to multiple environments
- Kubernetes or ECS manages scaling and availability
- Rolling deployments with zero downtime
- Instant rollbacks by switching image tags

### Example: A Startup's Typical Docker Workflow

```
Developer:
  1. git pull
  2. docker compose up (full local stack in 30 seconds)
  3. Code, test locally
  4. git push → triggers CI/CD

CI (GitHub Actions):
  1. docker build
  2. docker run tests
  3. docker push to registry (tagged with commit SHA)

CD (automated or manual trigger):
  1. SSH to server
  2. docker compose pull
  3. docker compose up -d --remove-orphans
  4. Verify health check passes
  5. Slack notification: "Deploy 1.2.3 successful ✅"
```

---

## 4.9 Docker Registries in Production

```bash
# GitHub Container Registry (ghcr.io)
docker login ghcr.io -u USERNAME -p TOKEN
docker tag my-app ghcr.io/org/my-app:1.0
docker push ghcr.io/org/my-app:1.0

# AWS Elastic Container Registry (ECR)
aws ecr get-login-password --region us-east-1 | \
  docker login --username AWS --password-stdin \
  123456789.dkr.ecr.us-east-1.amazonaws.com
docker tag my-app 123456789.dkr.ecr.us-east-1.amazonaws.com/my-app:1.0
docker push 123456789.dkr.ecr.us-east-1.amazonaws.com/my-app:1.0

# Self-hosted registry
docker run -d -p 5000:5000 --name registry registry:2
docker tag my-app localhost:5000/my-app:1.0
docker push localhost:5000/my-app:1.0
```

---

## 4.10 Docker System Maintenance

```bash
# Show disk usage by Docker
docker system df

# Remove everything unused (containers, images, networks, volumes)
docker system prune

# Also remove volumes (DANGER: destroys data!)
docker system prune --volumes

# Remove only stopped containers
docker container prune

# Remove only unused images
docker image prune -a

# Remove only unused networks
docker network prune

# Remove only unused volumes
docker volume prune
```

---

## 4.11 Advanced Dockerfile Patterns

### Build Arguments for Flexible Images

```dockerfile
ARG NODE_VERSION=20
FROM node:${NODE_VERSION}-alpine

ARG APP_ENV=production
ENV NODE_ENV=${APP_ENV}
```

```bash
docker build --build-arg NODE_VERSION=18 --build-arg APP_ENV=staging .
```

### Docker BuildKit (modern build system)

```bash
# Enable BuildKit (default in Docker 23+)
DOCKER_BUILDKIT=1 docker build .

# Or set in Docker daemon config:
# { "features": { "buildkit": true } }

# BuildKit features:
# - Parallel build stages
# - Better caching
# - Secret mounting (no secrets in layers)
# - SSH forwarding

# Mount secrets during build (doesn't add to image layers)
RUN --mount=type=secret,id=npmrc cat /run/secrets/npmrc > .npmrc && \
    npm ci && \
    rm .npmrc

docker build --secret id=npmrc,src=.npmrc .
```

### Heredoc Syntax (newer Dockerfile feature)

```dockerfile
# Run multiple commands more readably
RUN <<EOF
  apt-get update
  apt-get install -y curl git
  rm -rf /var/lib/apt/lists/*
EOF
```

---

## 4.12 Dockerizing Different Application Types

### React (Vite) Production Build

```dockerfile
# Dockerfile
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
ARG VITE_API_URL
ENV VITE_API_URL=$VITE_API_URL
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

```nginx
# nginx.conf
server {
    listen 80;
    root /usr/share/nginx/html;
    index index.html;

    # Handle React Router (SPA routing)
    location / {
        try_files $uri $uri/ /index.html;
    }

    # Proxy API calls to backend
    location /api/ {
        proxy_pass http://backend:3000/;
        proxy_http_version 1.1;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }

    # Cache static assets
    location ~* \.(js|css|png|jpg|gif|ico|svg)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

### Python FastAPI

```dockerfile
FROM python:3.12-slim

WORKDIR /app

# Install system deps
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    && rm -rf /var/lib/apt/lists/*

# Copy and install Python dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Non-root user
RUN adduser --disabled-password --gecos '' appuser
COPY --chown=appuser:appuser . .
USER appuser

EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

## 📝 Stage 4 Mini Notes

```
Orchestration:
  Docker Swarm → built-in, simpler, good for smaller deployments
  Kubernetes   → industry standard, complex, scales to millions of containers

Kubernetes basics:
  Pod          = one or more containers (smallest deployable unit)
  Deployment   = manages pods, handles rollouts and scaling
  Service      = stable network endpoint to reach pods
  Ingress      = external HTTP routing

kubectl commands:
  kubectl get pods/services/deployments
  kubectl apply -f file.yml
  kubectl scale deployment name --replicas=5
  kubectl rollout undo deployment/name
  kubectl logs -f deployment/name

CI/CD pipeline:
  push code → build image → test → push to registry → deploy

GitHub Actions: docker/build-push-action for building and pushing

Production checklist:
  ✅ Pin image versions (no 'latest' in production)
  ✅ Non-root user
  ✅ Resource limits
  ✅ restart: unless-stopped
  ✅ Health checks
  ✅ Log rotation (max-size, max-file)
  ✅ Read-only filesystem
  ✅ Security options (no-new-privileges)
  ✅ Secrets from environment, not baked in

Monitoring:
  cAdvisor → collects container metrics
  Prometheus → stores metrics
  Grafana → visualizes metrics
  Loki + Promtail → centralized logging

docker system prune → clean up unused resources
docker system df    → see disk usage
```

---

## ⚠️ Stage 4 Common Mistakes

- Using `latest` tag in production — you can't roll back if you don't know what changed.
- Not setting memory/CPU limits — one container can starve others.
- Not implementing proper health checks — orchestrators can't detect unhealthy apps.
- Skipping log rotation — containers eventually fill the disk with logs.
- `docker system prune --volumes` in production — destroys all data volumes.
- Not understanding that Kubernetes is for scale — overkill for a single server.
- Building without layer caching in CI — 10-minute builds instead of 1-minute.
- Embedding secrets in images — always use environment variables or secrets management.

---

## 🏋️ Stage 4 Practice Tasks

1. Set up GitHub Actions to automatically build and push your Docker image to GitHub Container Registry on every push to `main`.
2. Add a test stage to the CI pipeline — run `npm test` inside a container before pushing.
3. Deploy your full-stack app to a VPS (DigitalOcean, Linode, AWS EC2) using Docker Compose.
4. Set up Traefik as a reverse proxy with automatic SSL (Let's Encrypt).
5. Add a Prometheus + Grafana + cAdvisor monitoring stack to your compose setup.
6. Install minikube locally and deploy your Node.js app with a Kubernetes Deployment + Service.
7. Practice scaling: `kubectl scale deployment backend --replicas=5` and watch the pods spin up.
8. Set up log rotation in your production compose file and verify logs don't grow unbounded.

---

---

## Final Summary: The Complete Docker Journey

```
STAGE 1 — Beginner (1–2 weeks)
  What Docker is, containers vs VMs, images vs containers,
  Docker Hub, pulling and running images, essential commands
  (run, ps, stop, rm, logs, exec), port mapping, environment vars

STAGE 2 — Intermediate (2–3 weeks)
  Writing Dockerfiles, layer caching, .dockerignore,
  building custom images, CMD vs ENTRYPOINT, multi-stage builds,
  volumes (named + bind mounts), Docker networking,
  Dockerizing Node.js apps, pushing to Docker Hub

STAGE 3 — Advanced (3–4 weeks)
  Docker Compose, multi-container applications,
  health checks, depends_on, dev vs prod compose files,
  database containers, image optimization, security
  (non-root user, resource limits, image scanning),
  container debugging, environment files

STAGE 4 — Expert (4–6 weeks+)
  Container orchestration (Swarm, Kubernetes intro),
  CI/CD pipelines (GitHub Actions), production deployment patterns
  (blue-green, rolling), reverse proxies (Traefik, Nginx),
  monitoring (Prometheus, Grafana, cAdvisor),
  production best practices checklist, real-world workflows,
  BuildKit, Docker registries (ECR, GHCR), system maintenance
```

---

## Quick Reference Card

```bash
# ─── Images ───────────────────────────────────────────
docker pull nginx:latest          # download image
docker images                     # list local images
docker rmi image:tag              # remove image
docker build -t name:tag .        # build from Dockerfile
docker push user/name:tag         # push to registry

# ─── Containers ───────────────────────────────────────
docker run -d -p 8080:80 nginx    # run detached, map port
docker run -it ubuntu bash        # run interactive
docker ps                         # list running
docker ps -a                      # list all
docker stop name                  # stop container
docker start name                 # start stopped container
docker rm name                    # remove container
docker rm -f name                 # force remove running container

# ─── Logs & Debug ─────────────────────────────────────
docker logs name                  # view logs
docker logs -f name               # follow logs
docker exec -it name bash         # shell into container
docker inspect name               # detailed info
docker stats                      # resource usage

# ─── Volumes ──────────────────────────────────────────
docker volume create vol-name     # create named volume
docker volume ls                  # list volumes
docker volume rm vol-name         # remove volume
docker run -v vol-name:/data img  # mount named volume
docker run -v $(pwd):/app img     # mount bind mount

# ─── Networks ─────────────────────────────────────────
docker network create my-net      # create network
docker network ls                 # list networks
docker run --network my-net img   # attach to network

# ─── Compose ──────────────────────────────────────────
docker compose up -d              # start all services
docker compose up --build         # build and start
docker compose down               # stop and remove
docker compose down -v            # also remove volumes
docker compose ps                 # service status
docker compose logs -f svc        # follow service logs
docker compose exec svc bash      # shell into service
docker compose build svc          # rebuild service

# ─── System ───────────────────────────────────────────
docker system df                  # disk usage
docker system prune               # remove all unused
docker image prune -a             # remove unused images
```

---

> **Keep learning:** Once you finish this course, explore: AWS ECS/Fargate, Google Cloud Run, Docker Scout, Helm charts for Kubernetes, ArgoCD for GitOps, and Distroless base images for ultra-secure containers.

---

*Document prepared for complete Docker learning — Beginner to Expert.*
