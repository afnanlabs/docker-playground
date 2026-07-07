# Labs for EP7 - Docker Image Optimization

## Lab 1: Identify Bloated Images
1. Build the bloated image: `docker build -f Dockerfilebloated -t bloated .`
2. Inspect the image size: `docker images | grep bloated`
3. View the layers: `docker history bloated`

## Lab 2: Optimize with Multi-Stage Builds
1. Build the optimized image: `docker build -f Dockerfileoptimized -t optimized .`
2. Compare the size with the bloated image.
3. Verify the functionality of the optimized image.

## Lab 3: Use `.dockerignore`
1. Add patterns to `.dockerignore` (e.g., `node_modules/`, `.git/`).
2. Rebuild the image and observe the reduced build context size.