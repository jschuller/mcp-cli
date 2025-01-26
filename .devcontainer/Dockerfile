FROM ghcr.io/astral-sh/uv:latest as uv

FROM mcr.microsoft.com/devcontainers/python:3.10

# Copy UV binary from official image
COPY --from=uv --chown=vscode:vscode /uv /usr/local/bin/uv
COPY --from=uv --chown=vscode:vscode /uvx /usr/local/bin/uvx

# Install additional dependencies
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
    curl \
    build-essential \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

USER vscode
WORKDIR /workspace