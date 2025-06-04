100gb stockage (25 not enough)
2 CPU
RAM max vert

[source](https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download)

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

## start minikube
```sh
minikube start
kubectl get po -A
```

## deploy applications
Create a sample deployment and expose it on port 8080:
```sh
kubectl create deployment hello-minikube --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube --type=NodePort --port=8080
```
It may take a moment, but your deployment will soon show up when you run:
```sh
kubectl get services hello-minikube
```
The easiest way to access this service is to let minikube launch a web browser for you:
```sh
minikube service hello-minikube
```
Alternatively, use kubectl to forward the port:
```sh
kubectl port-forward service/hello-minikube 7080:8080
```
Tada! Your application is now available at [http://localhost:7080/](http://localhost:7080/).

You should be able to see the request metadata in the application output. Try changing the path of the request and observe the changes. Similarly, you can do a POST request and observe the body show up in the output.
