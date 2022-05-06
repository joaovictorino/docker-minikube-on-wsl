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

Install Docker-Compose
```sh
sudo apt-get install -y docker-compose
```

## Install Minikube

Install systemd
```sh
git clone https://github.com/DamionGans/ubuntu-wsl2-systemd-script.git
cd ubuntu-wsl2-systemd-script/
bash ubuntu-wsl2-systemd-script.sh
```

Close Ubuntu terminal, open PowerShell on Windows and then restart WSL
```sh
wsl --shutdown
```

Open Ubuntu terminal again and install conntrack
```sh
sudo apt install -y conntrack
```

Download the latest Minikube
```sh
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

Make it executable
```sh
chmod +x ./minikube
```

Move it to your user's executable PATH
```sh
sudo mv ./minikube /usr/local/bin/
```

Set the driver version to Docker
```sh
minikube config set driver docker
```

Download kubectl
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Make it executable
```sh
chmod +x ./kubectl
```

Move it to your user's executable PATH
```sh
sudo mv ./kubectl /usr/local/bin/
```

Start minikube
```sh
minikube start
```

Set the context kubectl to minikube
```sh
kubectl config use-context minikube
```

## Install Helm
Download Helm
```sh
curl https://raw.githubusercontent.com/kubernetes/helm/master/scripts/get > get_helm.sh
```

Make it executable
```sh
chmod +x get_helm.sh
```

Install Helm
```sh
./get_helm.sh
```
