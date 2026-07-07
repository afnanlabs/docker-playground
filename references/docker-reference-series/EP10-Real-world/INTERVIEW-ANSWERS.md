# Interview Answers for EP10 - Real-World Stack

1. **Benefits of Docker Compose**:
   - Simplifies the orchestration of multi-service applications.
   - Provides a single YAML file to define and manage services, networks, and volumes.

2. **Configuring a reverse proxy with Nginx**:
   - Define an Nginx service in `docker-compose.yml`.
   - Use a custom `nginx.conf` to route traffic to backend services.

3. **Purpose of health checks**:
   - Ensure that services are running and ready to handle requests.
   - Restart unhealthy containers automatically.

4. **Monitoring container metrics**:
   - Use tools like cAdvisor, Prometheus, or Grafana to monitor metrics.
   - cAdvisor provides resource usage statistics for containers.

5. **Best practices for persisting data**:
   - Use named volumes for database data.
   - Regularly back up volumes to prevent data loss.