# Interview Answers for EP8 - Container Security Basics

1. **Running containers as non-root users**:
   - Reduces the risk of privilege escalation attacks.

2. **Best practices for securing Docker images**:
   - Use minimal base images.
   - Remove unnecessary tools and dependencies.
   - Regularly update images to patch vulnerabilities.

3. **Restricting container capabilities**:
   - Use `--cap-drop` to remove capabilities and `--cap-add` to add only necessary ones.

4. **Purpose of `--read-only` flag**:
   - Makes the container's filesystem read-only, preventing unauthorized writes.

5. **Scanning Docker images for vulnerabilities**:
   - Use tools like `docker scan`, Trivy, or Clair to identify vulnerabilities.