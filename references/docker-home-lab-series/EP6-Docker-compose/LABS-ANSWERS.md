# Lab Answers for EP6 - Docker Compose

## Lab 1: Define and Run a Multi-Service Application
- `docker-compose.yml` defines `web` and `db` services.
- Running `docker-compose up` starts both services.
- `docker-compose ps` shows the running containers.

## Lab 2: Pass Environment Variables
- An `.env` file contains key-value pairs for environment variables.
- Referencing the `.env` file in `docker-compose.yml` passes the variables to the services.

## Lab 3: Scale a Service
- `docker-compose up --scale web=3` creates 3 instances of the `web` service.
- `docker-compose ps` lists all instances of the scaled service.