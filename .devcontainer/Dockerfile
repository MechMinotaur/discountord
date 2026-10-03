FROM mcr.microsoft.com/dotnet/sdk:10.0

# Install Node.js 22
RUN apt-get update \
    && apt-get install -y curl \
    && curl -fsSL https://deb.nodesource.com/setup_22.x | bash - \
    && apt-get install -y nodejs \
    && rm -rf /var/lib/apt/lists/*

# Install Angular CLI
RUN npm install -g @angular/cli

WORKDIR /workspace
