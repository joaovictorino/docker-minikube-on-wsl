# How to install Docker, Docker Compose, Minikube and Helm on WSL2 Ubuntu 20.04 without Docker Desktop

## Install Docker

Remove older versions of Docker
```sh
sudo apt-get remove docker docker-engine docker.io containerd runc
```

Update repositories and install Docker prerequisites
```sh
sudo apt-get update

sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

Download official Docker GPG Key
```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Add the stable channel
```sh
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

Update package list
```sh
sudo apt-get update
```

Install Docker
```sh
sudo apt-get install -y docker-ce
```

Run docker without sudo permission
```sh
sudo usermod -aG docker $USER && newgrp docker
```

## Install Docker-compose

## Install Minikube

## Install Helm
