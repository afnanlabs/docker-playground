# Lab Answers for EP5 - Crash Loops and Configuration

## Lab 1: Reproduce a Crash Loop
- Running the container without required environment variables causes it to crash.
- `docker ps` shows the container repeatedly restarting.

## Lab 2: Debugging
- `docker logs <container_id>` reveals the error causing the crash.
- Running interactively with `docker run -it crash-app sh` allows inspecting the container's environment.
- Fixing the issue (e.g., setting required environment variables) resolves the crash.

## Lab 3: Restart Policies
- `--restart=on-failure` restarts the container only if it exits with a non-zero status.
- Stopping the container manually prevents further restarts.