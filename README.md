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
Install Dev Containers extension

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
- Pushed to GitHub
