# Interview Answers for EP1 - Docker Setup and Basics

1. **Difference between an image and a container**:
   - An image is a read-only template used to create containers.
   - A container is a running instance of an image.

2. **Purpose of `docker run`**:
   - The `docker run` command creates and starts a container from a specified image.

3. **Role of Docker Hub**:
   - Docker Hub is a cloud-based registry where Docker users can store and share container images.

4. **Remove all stopped containers**:
   - Use the command: `docker container prune`

5. **Significance of `--rm` flag**:
   - The `--rm` flag automatically removes the container once it stops, ensuring no leftover stopped containers.