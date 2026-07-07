# Lab Answers for EP8 - Container Security Basics

## Lab 1: Run as Non-Root
- Adding a non-root user in the Dockerfile ensures the container does not run as root.
- `whoami` inside the container confirms the non-root user.

## Lab 2: Restrict Capabilities
- Dropping all capabilities and adding only `NET_BIND_SERVICE` limits the container's privileges.
- This reduces the attack surface.

## Lab 3: Scan for Vulnerabilities
- `docker scan` identifies vulnerabilities in the image.
- Updating the base image and dependencies resolves most vulnerabilities.