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

`docker run -it --entrypoint zsh zlskidmore/ubuntu-zsh`
`echo $0` to check current shell
