# Labs for EP4 - Persistent Volumes

## Lab 1: Create and Use a Named Volume
1. Create a volume: `docker volume create mydata`
2. Run a container with the volume: `docker run -d -v mydata:/data alpine sleep 1000`
3. Write data to the volume: `docker exec <container_id> sh -c "echo 'Hello' > /data/hello.txt"`
4. Verify data persistence by starting a new container with the same volume.

## Lab 2: Bind Mounts
1. Create a directory on the host: `mkdir ~/mybind`
2. Run a container with a bind mount: `docker run -d -v ~/mybind:/data alpine sleep 1000`
3. Write data to the bind mount: `echo 'Hello from host' > ~/mybind/hello.txt`
4. Verify the data inside the container: `docker exec <container_id> cat /data/hello.txt`.

## Lab 3: Inspect Volumes
1. Inspect a volume: `docker volume inspect mydata`
2. Mount the volume to a temporary container and explore its contents.