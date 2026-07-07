# Labs for EP6 - Docker Compose

## Lab 1: Define and Run a Multi-Service Application
1. Create a `docker-compose.yml` file with `web` (Flask) and `db` (Postgres) services.
2. Run the application: `docker-compose up`.
3. Verify both services are running: `docker-compose ps`.

## Lab 2: Pass Environment Variables
1. Add an `.env` file with database credentials.
2. Reference the `.env` file in `docker-compose.yml`.
3. Verify the environment variables are passed to the `db` service.

## Lab 3: Scale a Service
1. Scale the `web` service to 3 instances: `docker-compose up --scale web=3`.
2. Verify the scaled instances: `docker-compose ps`.