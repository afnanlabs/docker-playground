# Lab Answers for EP4 - Persistent Volumes

## Lab 1: Create and Use a Named Volume
- `docker volume create mydata` creates a named volume.
- Writing data to `/data/hello.txt` persists it in the volume.
- Starting a new container with `-v mydata:/data` shows the persisted data.

## Lab 2: Bind Mounts
- `mkdir ~/mybind` creates a host directory.
- Writing data to `~/mybind/hello.txt` makes it accessible in the container at `/data/hello.txt`.
- Changes in the host directory are reflected in the container and vice versa.

## Lab 3: Inspect Volumes
- `docker volume inspect mydata` shows metadata like mount point.
- Mounting the volume to a temporary container allows exploring its contents.