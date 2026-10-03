# discountord
Lamest chat server ever

# Update system repositories and install tools
- docker
- docker-compose
- docker-buildx
- visual-studio-code-bin
- git

# Setup docker
- sudo systemctl enable --now docker
- sudo usermod -aG docker $USER
- newgrp docker (or just reboot)
- docker buildx install

# Setup vscode
- Install Dev Containers extension
- Install the Container Tools extension

# How I created this
- Signed into github and created a new repo
- Cloned it locally
- Created a front-end and back-end folder
- Created a sample Angular app with: `docker run --rm -v "$(pwd)/front-end:/app" -w /app node:latest sh -c "npm install -g @angular/cli && ng new front-end --directory . --routing --style css --skip-git"`
- Created a sample back-end dotnet app with: `docker run --rm -u "$(id -u):$(id -g)" -v "$(pwd)/back-end:/app" -w /app mcr.microsoft.com/dotnet/sdk:10.0 sh -c "dotnet new webapi -n App --no-https && mv App/* . && rm -rf App"`
- Setup PostgreSQL to work with the back-end with:
```
docker run --rm -u "$(id -u):$(id -g)" \
  -v "$(pwd)/back-end:/app" \
  -w /app \
  mcr.microsoft.com/dotnet/sdk:10.0 \
  dotnet add package Npgsql.EntityFrameworkCore.PostgreSQL --version '10.*'
  ```
- Setup ssh keys with:
  - Created a key with `ssh-keygen -t ed25519 -C "tim.burch1@outlook.com"`
  - Started the ssh agent with `eval (ssh-agent -c)`
  - Adding with `ssh-add ~/.ssh/id_ed25519` followed by `ssh-add -l`
  - Signing into github and copy pasting the output from `cat ~/.ssh/id_ed25519.pub` into a new SSH key
  - Changing remote from https to ssh with `git remote set-url origin git@github.com:MechMinotaur/discountord.git`
  - Pushing with git push -u origin main

- setup a dev container using docker-compose.yml
- attached to it using vscode's extension with `Dev Containers: Reopen in Container`

