100gb stockage (25 not enough)
2 CPU
RAM max vert

## update
```sh
sudo apt update && sudo apt upgrade
```

## install docker
```sh
sudo apt install docker-compose
sudo groupadd docker
sudo usermod -aG docker $USER
sudo reboot
docker run hello-world
```

## install minikube
```sh
curl -LO https://github.com/kubernetes/minikube/releases/latest/download/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
minikube start
```

## install kubectl
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check

# check if output is:
kubectl: OK
# and not something like:
kubectl: FAILED
sha256sum: WARNING: 1 computed checksum did NOT match

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

```


