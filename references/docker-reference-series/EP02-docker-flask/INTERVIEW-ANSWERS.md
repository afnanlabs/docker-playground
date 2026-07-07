# Interview Answers for EP2 - Dockerizing a Flask App

1. **Purpose of a `Dockerfile`**:
   - A `Dockerfile` is a script that contains instructions to build a Docker image.

2. **Significance of `EXPOSE`**:
   - The `EXPOSE` instruction documents the ports on which the containerized application listens.

3. **Role of `.dockerignore`**:
   - `.dockerignore` excludes unnecessary files from the build context, reducing image size and build time.

4. **Difference between `COPY` and `ADD`**:
   - `COPY` is used to copy files/directories from the build context.
   - `ADD` can also fetch files from URLs and extract tar archives.

5. **Debugging a failing container**:
   - Use `docker logs <container_id>` to view logs.
   - Run interactively: `docker run -it <image> sh`.