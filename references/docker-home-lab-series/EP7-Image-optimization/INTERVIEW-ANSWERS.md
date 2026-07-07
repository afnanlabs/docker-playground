# Interview Answers for EP7 - Docker Image Optimization

1. **Common anti-patterns**:
   - Including unnecessary tools and files.
   - Using large base images.
   - Not cleaning up temporary files during builds.

2. **Multi-stage builds**:
   - Separate build-time and runtime dependencies, reducing the final image size.

3. **Purpose of `.dockerignore`**:
   - Exclude unnecessary files from the build context, reducing image size and build time.

4. **Inspecting image layers**:
   - Use `docker history <image>` to view the layers of an image.

5. **Minimizing attack surface**:
   - Smaller images reduce vulnerabilities.
   - Removing unnecessary tools and using non-root users enhances security.