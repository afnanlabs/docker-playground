# Labs for EP9 - CI/CD with Docker

## Lab 1: Build and Push Docker Images
1. Create a GitHub Actions workflow file: `.github/workflows/docker.yml`.
2. Use `docker/build-push-action` to build and push an image to Docker Hub.
3. Trigger the workflow by pushing a commit.

## Lab 2: Add Caching
1. Modify the workflow to use `actions/cache` for caching Docker layers.
2. Observe the reduced build time in subsequent runs.

## Lab 3: Extend the Workflow
1. Add a `workflow_dispatch` trigger for manual runs.
2. Tag images with the Git SHA and branch name.
3. Test the extended workflow.