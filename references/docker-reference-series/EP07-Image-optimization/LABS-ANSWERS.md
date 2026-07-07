# Lab Answers for EP7 - Docker Image Optimization

## Lab 1: Identify Bloated Images
- Building the bloated image results in a large size due to unnecessary files and tools.
- `docker history bloated` shows multiple large layers.

## Lab 2: Optimize with Multi-Stage Builds
- The optimized image is significantly smaller.
- Multi-stage builds separate build-time and runtime dependencies.
- The optimized image retains full functionality.

## Lab 3: Use `.dockerignore`
- Adding patterns like `node_modules/` and `.git/` reduces the build context size.
- Rebuilding the image is faster and results in a smaller image.