# Labs for EP1 - Docker Setup and Basics

## Lab 1: Verify Docker Installation
1. Run `docker version` to check the installed version.
2. Run `docker info` to view system-wide information.

## Lab 2: Run Your First Container
1. Execute `docker run --rm hello-world`.
2. Observe the output and understand the lifecycle of the container.

## Lab 3: Explore Docker CLI
1. Pull an image: `docker pull alpine`
2. List images: `docker images`
3. Run a container: `docker run -it alpine sh`
4. Stop and remove containers: `docker ps -a`, `docker rm <container_id>`.