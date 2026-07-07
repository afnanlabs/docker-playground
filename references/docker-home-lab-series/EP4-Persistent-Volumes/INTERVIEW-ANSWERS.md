# Interview Answers for EP4 - Persistent Volumes

1. **Difference between a named volume and a bind mount**:
   - Named volumes are managed by Docker and stored in Docker's volume directory.
   - Bind mounts map a host directory to a container directory.

2. **Importance of persisting data**:
   - Persisting data ensures that important information is not lost when a container is removed or restarted.

3. **Creating and using a named volume**:
   - Create: `docker volume create myvolume`
   - Use: `docker run -v myvolume:/data myimage`

4. **Common pitfalls with bind mounts**:
   - Incorrect paths can lead to errors.
   - Permissions issues may prevent the container from accessing the mounted directory.

5. **Inspecting Docker volume contents**:
   - Use `docker volume inspect <volume_name>` to view metadata.
   - Mount the volume to a temporary container to explore its contents.