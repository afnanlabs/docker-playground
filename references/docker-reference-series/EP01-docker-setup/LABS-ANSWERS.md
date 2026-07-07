# Lab Answers for EP1 - Docker Setup and Basics

## Lab 1: Verify Docker Installation
- `docker version` shows the client and server versions.
- `docker info` provides details about the Docker environment, including storage drivers and running containers.

## Lab 2: Run Your First Container
- The `hello-world` container runs and outputs a message, then exits.
- The `--rm` flag ensures the container is removed after it stops.

## Lab 3: Explore Docker CLI
- `docker pull alpine` downloads the Alpine image.
- `docker images` lists all downloaded images.
- `docker run -it alpine sh` starts an interactive shell in the Alpine container.
- `docker ps -a` lists all containers, and `docker rm <container_id>` removes stopped containers.