DOCKER CHEATSHEETS

# Docker Basics

You have probably faced this
"It works on my system but not on yours"

# Why does this happens?

1st POV : Works fine on my laptop
2nd POV : Get's error on client's laptop

The Problem -
Every system has different:

- OS (Windows,macOS,Linux)
- Libraries & Dependencies
- Configuration & Settings
- Installed Software Versions

Note: Even small differences can brake your app

That's why the same app behaves differently on different systems

# What is Docker?

Docker is platform that packages your application along with all it's dependencies into a single unit called Images

It includes everything you app needs
Application + Libraries + Dependencies + OS = Docker images

💡Once the image is created, you can run it anywhere and it will behave the same

# Let's move the most important topic -

Docker Images vs Docker Container

Docker image:

- It is like a blueprint
- Read-only template
- Used to create containers

Docker Container:

- It's a running instance
- Read-Write
- Created from an image

In Simple words -
Image is a blueprint which is run into a Container which is running instance
[One image can create many containers!]

Image is static,
Container is dynamic!

# How Docker Works?

The basic flow is simple

1. Write Dockerfile -> We define the environment and dependencies
2. Build Image -> Docker reads the Dockerfile and creates ana Imagem
3. Run Container -> We run the image and get a running container.

💡 Write -> Build -> Run

# Why use Docker?

Docker makes our lives so much easier!

1. Consistent Environment - Runs the same everywhere - no "it works on my machine" problem!
2. Fast & Lightweight - Container starts in seconds and use fewer resources
3. Easy to Share & Port - Packages once and share anywhere. Run it on your laptop, server or cloud!
4. Better Isolation - Each container is islated, so apps don't mess with each other.
5. Save Time & Money - Automate setup, reduce errors, and focus on building your app!

💡 Docker = Consistency + Speed + Probability
That's why it's the foundation of DevOps

# Docker in Real World

Docker is used everywhere in DevOps!

- Where is DOCKER used?
  Cloud Deployment + CI/CD Pipelines + Microservices Architecture + Development Tools + Any Apps, Any Languages

From small projects to big systems, Docker is the foundation!

✅ Before Kubernetes comes in, we need something to create, run and manage container. That's something is Docker!
💡Kubernetes manages CONTAINER, Docker creates them!

Docker makes our lives easier by packaging our app and running it the same everywhere.

# Docker DEEP DIVE

This section contains

1. Volumes - Persist data beyong container.
2. Networks - Connect containers to talk to each other.
   3.Docker Compose - Run multi-Container apps with a single commands
3. Environmental Variables - Configure apps the smart way.
4. Secrets - Keep sensitive data safe.
5. Real World Use - Where does Docker is used in real projects
6. Best Practices - Simple tips to write better Docker setups

## What are Docker Volumes?

Container are temporary.
Volumes make your data permanent.

The Problem:
When a container is stopped or removed, all the data inside it is lost forever!

The Solution:
Use Docker Volumes to store data outside the container. Your data stays safe, no matter what!

### What can be stored in Volumes?

1. Database Data
2. Log Files
3. App Configurations
4. User Uploads & Files
5. Any Persistent Data

💡 Volumes = Data Persistence = Peace of Mind

## Docker Networks

Docker Networks allows containers to commumicate with each other securely
Think of it as a private network for your container!

Why this matter?

- Containers can talk to each other.
- Better isolation
- Easy app communication.
- More control & security

### Examples -

[![docker-eg.jpg](https://i.postimg.cc/XqL9zZLd/docker-eg.jpg)](https://postimg.cc/hQJJJtHt)

### Common Network Types

1. Bridges (Default) - Containers on the same Docker host can communicate.
2. Overlay - For multi-host communication (Docker Swarm)
3. Host - Container shares the host's network.
4. None - No networking for the container. (Fully isolated)
