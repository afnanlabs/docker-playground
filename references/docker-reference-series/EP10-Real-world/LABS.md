# Labs for EP10 - Real-World Stack

## Lab 1: Configure a Reverse Proxy
1. Define an Nginx service in `docker-compose.yml`.
2. Use `nginx.conf` to route traffic to the Flask app.
3. Verify the setup by accessing the app via Nginx.

## Lab 2: Add Health Checks
1. Add health checks to the `docker-compose.yml` file for the Flask and Postgres services.
2. Verify the health status using `docker-compose ps`.

## Lab 3: Monitor Metrics
1. Add a cAdvisor service to `docker-compose.yml`.
2. Access cAdvisor at http://localhost:8080 to view container metrics.
3. Analyze resource usage for each service.