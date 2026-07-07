# Lab Answers for EP3 - Docker Networking

## Lab 1: Create and Use a Custom Network
- `docker network create mynet` creates a user-defined bridge network.
- Containers on `mynet` can communicate using their names.
- `docker exec container1 ping container2` verifies connectivity.

## Lab 2: Publish Ports
- `docker run -d -p 8080:80 nginx` maps port 80 in the container to port 8080 on the host.
- Accessing http://localhost:8080 confirms the setup.

## Lab 3: Debugging
- Disconnecting a container from the network prevents communication.
- `docker network disconnect mynet container1` isolates `container1` from `mynet`.