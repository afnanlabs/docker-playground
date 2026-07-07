# Labs for EP8 - Container Security Basics

## Lab 1: Run as Non-Root
1. Modify the Dockerfile to include a non-root user.
2. Build and run the container: `docker build -t secure-app . && docker run secure-app`
3. Verify the user inside the container: `docker exec <container_id> whoami`

## Lab 2: Restrict Capabilities
1. Run a container with dropped capabilities: `docker run --cap-drop=ALL --cap-add=NET_BIND_SERVICE secure-app`
2. Verify the restricted capabilities.

## Lab 3: Scan for Vulnerabilities
1. Use `docker scan <image>` to scan the image.
2. Analyze the results and identify vulnerabilities.
3. Fix the vulnerabilities by updating the base image or dependencies.