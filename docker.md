# Build

## Build an image from the Dockerfile in the current directory and tag the image
```
docker build -t myimage:1.0 .
```

## List all images that are locally stored with the Docker Engine
```
docker image ls
```

## Delete an image from the local image store

```
docker image rm alpine:3.4
```

# Share

## Pull an image from a registry
```
docker pull myimage:1.0
```

## Retag a local image with a new image name and tag
```
docker tag myimage:1.0 myrepo/myimage:2.0
```

## Push an image to a registry
```
docker push myrepo/myimage:2.0 
```

# Run 

## Run a container from the Alpine version 3.9 image, name the running container “web” and expose port 5000 externally, mapped to port 80 inside the container.
```
docker container run --name web -p 5000:80 alpine:3.9
```

## Stop a running container through SIGTERM 
```
docker container stop web 
```

## Stop a running container through SIGKILL
```
docker container kill web
```

## List the networks
```
docker network ls
```

## List the running containers (add --all to include stopped containers)
```
docker container ls
```

## Delete all running and stopped containers
```
docker container rm -f $(docker ps -aq)
```

## Print the last 100 lines of a container’s logs
```
docker container logs --tail 100 web
```

# What’s running?

## ps lists all the docker containers are running with container details.
```
docker ps
```

## List all the docker containers running/exited/stopped with container details.
```
docker ps -a
```

# exec

## Access the docker container and run commands inside the container. I am accessing the apache server container in this example.
```
docker exec -it 09ca6feb6efc bash
```

# Login into docker hub. 

```
docker login
```

