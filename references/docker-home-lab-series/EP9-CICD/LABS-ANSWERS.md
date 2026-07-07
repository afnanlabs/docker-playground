# Lab Answers for EP9 - CI/CD with Docker

## Lab 1: Build and Push Docker Images
- The workflow builds and pushes the image to Docker Hub using `docker/build-push-action`.
- Secrets for `DOCKER_USERNAME` and `DOCKER_PASSWORD` are used for authentication.

## Lab 2: Add Caching
- Adding `actions/cache` caches Docker layers, reducing build time.
- Subsequent runs reuse cached layers, speeding up the process.

## Lab 3: Extend the Workflow
- `workflow_dispatch` allows manual triggering of the workflow.
- Tagging images with Git SHA and branch name ensures traceability.
- The extended workflow is tested and verified.