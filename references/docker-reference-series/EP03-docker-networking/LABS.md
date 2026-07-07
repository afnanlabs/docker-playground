# Labs for EP3 - Docker Networking

## Lab 1: Create and Use a Custom Network
1. Create a network: `docker network create mynet`
2. Run two containers on the network:
   - `docker run -d --name container1 --network mynet alpine sleep 1000`
   - `docker run -d --name container2 --network mynet alpine sleep 1000`
3. Verify connectivity: `docker exec container1 ping container2`

## Lab 2: Publish Ports
1. Run a container with a published port: `docker run -d -p 8080:80 nginx`
2. Access the containerized Nginx at http://localhost:8080.

## Lab 3: Debugging
1. Disconnect a container from the network: `docker network disconnect mynet container1`
2. Attempt to ping container2 from container1 and observe the failure.