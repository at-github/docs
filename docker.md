# Docker

## Some clarifications

| Term        | Explaination       |
| ----------- | ------------------ |
| Image       | Describe stack     |
| Volume      | Data space storage |
| Container   | Running stack      |

## Add user to group docker

To prevent some *permission denied* message

`sudo usermod -aG docker $USER`

Apply the group changes to the current terminal session

`newgrp docker`

## Some helpfull basic commands

- `docker ps -a` to list all container running or not
- `docker rm <container_id>` to … remove it
- `docker rm $(docker ps --filter status=exited -q)` remove all exited containers

## Just run an ubuntu with zsh to test my configuration

### Create custom image
```dockerfile
# Dockerfile
FROM ubuntu:22.10
RUN apt update
RUN apt install -y git zsh
```

### Build custom image
`docker build -t author/project:tag <path folder with Dockerfile>`

`docker run -it <container:default_tag_latest> zsh`

`echo $0` to check current shell

## How to clean

[Source](https://docs.docker.com/config/pruning/)

The docker system prune command is a shortcut that prunes images, containers, and networks.
Volumes are not pruned by default, and you must specify the `--volumes` flag for docker system prune to prune volumes.

```shell
docker system prune
```

```shell
docker volume prune
```

```shell
docker container prune
```

```shell
docker image prune
```
