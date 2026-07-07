# Labs for EP5 - Crash Loops and Configuration

## Lab 1: Reproduce a Crash Loop
1. Build the image: `docker build -t crash-app .`
2. Run the container without required environment variables: `docker run crash-app`
3. Observe the crash loop using `docker ps`.

## Lab 2: Debugging
1. Inspect logs: `docker logs <container_id>`.
2. Run interactively: `docker run -it crash-app sh`.
3. Identify and fix the issue.

## Lab 3: Restart Policies
1. Run the container with a restart policy: `docker run --restart=on-failure crash-app`
2. Observe the behavior when the container crashes.
3. Stop the container: `docker stop <container_id>`.