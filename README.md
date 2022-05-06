# How to install Docker, Docker Compose, Minikube and Helm on WSL2 Ubuntu 20.04 without Docker Desktop

## Install Docker

Remove old versions of Docker
sudo apt-get remove docker docker-engine docker.io containerd runc

sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
