# Lab Answers for EP10 - Real-World Stack

## Lab 1: Configure a Reverse Proxy
- Nginx routes traffic to the Flask app based on the `nginx.conf` configuration.
- Accessing the app via Nginx confirms the setup.

## Lab 2: Add Health Checks
- Health checks ensure that services are running and ready.
- `docker-compose ps` shows the health status of each service.

## Lab 3: Monitor Metrics
- cAdvisor provides detailed metrics for each container.
- Resource usage statistics help identify bottlenecks and optimize performance.