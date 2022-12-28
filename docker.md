# Docker

## Add user to group docker

To prevent some *permission denied* message

`sudo usermod -aG docker $USER`

Apply the group changes to the current terminal session

`newgrp docker`

## Some helpfull basic commands

- `docker ps -a` to list all container running or not
- `docker rm <container_id>` to … remove it

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

`docker run -it --entrypoint zsh <container:default_tag_latest>`
`echo $0` to check current shell
