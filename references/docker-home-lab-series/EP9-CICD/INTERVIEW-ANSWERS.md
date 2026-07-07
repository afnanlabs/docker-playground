# Interview Answers for EP9 - CI/CD with Docker

1. **Purpose of CI/CD**:
   - Automates the build, test, and deployment processes, ensuring faster and more reliable software delivery.

2. **Docker in CI/CD**:
   - Docker ensures consistent environments across development, testing, and production.
   - Images can be built and tested in CI pipelines and deployed in CD pipelines.

3. **Benefits of GitHub Actions**:
   - Seamless integration with GitHub repositories.
   - Pre-built actions for common tasks.
   - Scalable and customizable workflows.

4. **Configuring Docker build and push**:
   - Use `docker/build-push-action` to build and push images to a registry.
   - Define secrets for registry credentials.

5. **Best practices for caching**:
   - Cache dependencies and layers to speed up builds.
   - Use `actions/cache` for caching files between workflow runs.