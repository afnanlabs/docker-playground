# Interview Answers for EP3 - Docker Networking

1. **Purpose of a user-defined bridge network**:
   - It allows containers to communicate with each other using container names as hostnames.

2. **Container communication within the same network**:
   - Containers can communicate using their DNS names or IP addresses.

3. **Exposing vs publishing a port**:
   - Exposing a port makes it available to other containers.
   - Publishing a port maps it to the host, making it accessible externally.

4. **Troubleshooting connectivity issues**:
   - Verify network: `docker network inspect <network>`.
   - Check logs: `docker logs <container>`.
   - Test connectivity: `docker exec <container> ping <other_container>`.

5. **Role of DNS in Docker networking**:
   - Docker's embedded DNS resolves container names to their IP addresses within the same network.