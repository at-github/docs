# Docker

## Add user to group docker

To prevent some *permission denied* message

`sudo usermod -aG docker $USER`

Apply the group changes to the current terminal session

`newgrp docker`
