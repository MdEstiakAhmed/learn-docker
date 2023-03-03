# virtual machine vs container:

| virtual machine                                  | container                                      |
| ------------------------------------------------ | ---------------------------------------------- |
| virtual machine is a full-blown operating system | container is a lightweight virtual environment |
| it's own full OS system                          | it's share the host OS system                  |

# docker image:

- a blueprint of a container
- run time environment
  -any dependencies
- application code
- configuration files

#docker container:

- a running instance of an image
- it's a process
- it's isolated from the host and other containers
- it has its own file system, its own networking, and its own isolated process tree

# docker and container demo:

| docker      | container                       |
| ----------- | ------------------------------- |
| node 17     | running instance of node 17     |
| source code | running instance of source code |

# docker hub:

> docker hub is a cloud-based registry service which stores # docker images
> link to docker hub: https://hub.docker.com/
> from docker hub, we can pull images to our local machine
> for example, we need to pull node image to our local machine. just search node in docker hub and copy the command to pull the image.

```bash
docker pull node
```

pull specific version of node image:

```bash
docker pull node:16
```

# run docker image:

> we can build our own docker image
> for example, we want to build a docker image for our node app
> we need to create a docker file and add the following content to the docker file:

```bash
FROM node:16
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]
```

> then we need to build the docker image:

```bash
docker build -t mern-app:v1 .
# -t is the tag name
# the tag name is mern-app
# :v1 is the version
# . is the current directory
```

> then we can run the docker image:

```bash
docker run --name mymernapp -p 4000:4000 -d mern-app
docker run --name mymernapp -p 4000:4000 --rm mern-app
# --name is the name of our docker container
# -p is the port
# 4000 is the port of our local machine
# 4000 is the port of our docker container
# -d is the daemon mode
# --rm is the remove the container after it stops
# mern-app is the tag name of our docker image
```

# check docker image:

> we can check the docker image by running the following command:

```bash
docker images
```

# remove docker image:

> we can remove the docker image by running the following command:

```bash
# general remove docker image
docker rmi mern-app

# remove docker image with force
docker rmi -f mern-app
```

# check docker container:

> we can check the docker container by running the following command:

```bash
# check active docker container
docker ps

# check all docker container
docker ps -a
```

# start docker container:

> we can start a existing docker container by running the following command:

```bash
docker start mymernapp
```

# stop docker container:

> we can stop the docker container by running the following command:

```bash
docker stop mymernapp
```

# remove docker container:

> we can remove the docker container by running the following command:

```bash
docker container rm mymernapp
```

# remove all containers and images:

> we can remove all containers and images by running the following command:

```bash
docker system prune -a
```

# docker compose:

> docker compose is a tool for defining and running multi-container docker applications
> docker compose is a tool for defining and running multi-container docker applications
> docker compose is a tool for defining and running multi-container docker applications
> docker compose is a tool for defining and running multi-container docker applications

# run docker compose:

> we can run docker compose by running the following command:

```bash
docker-compose up
```

# stop docker compose:

> we can stop docker compose by running the following command:

```bash
# not remove the container and image
docker-compose down

# remove the container and image and volume
docker-compose down --rmi all -v
```
```

