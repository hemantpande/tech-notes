## Search images

docker search redis

## Run docker image from Docker-hub in background

docker run -d redis

## Find running containers - also displays the friendly name and ID

docker ps

## Find details of an image

docker inspect <friendly-name|container-id>

## Image logs

docker logs <friendly-name|container-id>

## Create an image with friendly name and port *Best Practice* - extremely useful if you want to avoid looking up for auto-generated friendly name and default port.

docker run -d --name <name> -p <port no>:<port no> <image name>:<version>
For ex.
docker run -d --name redisHostPort -p 6379:6379 redis:latest

#### By default, the port on the host is mapped to 0.0.0.0, which means all IP addresses. You can specify a particular IP address when you define the port mapping, for example, -p 127.0.0.1:6379:6379

## Containers are by default STATELESS. Binding directories (also known as volumes) is done using the option -v <host-dir>:<container-dir>. When a directory is mounted, the files which exist in that directory on the host can be accessed by the container and any data changed/written to the directory inside the container will be stored on the host. This allows you to upgrade or change containers without losing your data.

For ex.
docker run -d --name redisMapped -v /opt/docker/data/redis:/data redis
docker run -d --name redisMapped -v "$PWD/data":/data redis

## Launch a container in fore-ground (For ex. Below command launches an Ubuntu container and executes the command ps to view all the processes running in a container.)
docker run ubuntu ps

## Interact with the container (for example, to access a bash shell)
docker run -it ubuntu bash