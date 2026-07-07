# Interview Answers for EP6 - Docker Compose

1. **What is Docker Compose?**:
   - Docker Compose is a tool for defining and running multi-container Docker applications using a YAML file.

2. **Defining multiple services**:
   - Use the `services` section in `docker-compose.yml` to define each service with its configuration.

3. **Purpose of `depends_on`**:
   - Specifies the order in which services are started but does not guarantee readiness.

4. **Passing environment variables**:
   - Use the `environment` key or an `.env` file with `env_file`.

5. **Scaling a service**:
   - Use `docker-compose up --scale <service>=<count>` to scale a service to multiple instances.