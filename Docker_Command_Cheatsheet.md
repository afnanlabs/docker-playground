# 🐳 Docker Command Cheatsheet

## Basic Commands

```bash
docker run <image>          # Run container
docker run -d <image>       # Run in background
docker run -p 8080:80 <image>  # Port mapping
docker run -it <image> bash # Interactive shell
docker ps                   # Show running containers
docker ps -a                # Show all containers
```

## Management

```bash
docker stop <container>     # Stop container
docker start <container>    # Start container
docker rm <container>       # Remove container
docker rmi <image>          # Remove image
docker logs <container>     # Show logs
docker exec -it <container> bash  # Enter container
```

## Image Operations

```bash
docker images               # List images
docker pull <image>         # Pull image
docker build -t <name> .    # Build image
docker tag <image> <tag>    # Tag image
docker push <image>         # Push image
```

## Docker Compose

```bash
docker-compose up           # Start services
docker-compose up -d        # Start in background
docker-compose down         # Stop and remove
docker-compose ps           # Show status
docker-compose logs         # Show logs
docker-compose build        # Rebuild services
```

## Cleanup

```bash
docker system prune         # Remove unused data
docker system prune -a      # Remove all unused images
docker volume prune         # Remove unused volumes
```
