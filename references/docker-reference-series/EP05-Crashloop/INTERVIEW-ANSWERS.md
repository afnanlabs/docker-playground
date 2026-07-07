# Interview Answers for EP5 - Crash Loops and Configuration

1. **Crash loop in Docker**:
   - A crash loop occurs when a container repeatedly starts and stops due to errors.
   - Common causes include missing environment variables, misconfigurations, or application errors.

2. **Inspecting logs of a crashing container**:
   - Use `docker logs <container_id>` to view the logs.

3. **Purpose of `--restart` flag**:
   - The `--restart` flag defines the restart policy for a container (e.g., `always`, `on-failure`).

4. **Passing environment variables to a container**:
   - Use the `-e` flag: `docker run -e VAR_NAME=value myimage`.
   - Alternatively, use an `.env` file with `--env-file`.

5. **Debugging a container that exits immediately**:
   - Run interactively: `docker run -it <image> sh`.
   - Check logs: `docker logs <container_id>`.
   - Inspect the Dockerfile and application code for issues.