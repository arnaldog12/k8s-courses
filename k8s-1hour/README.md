# k8s in 1 hour

- 🌐 Link: https://youtu.be/s_o8dwzRlu4
- 🦊 Repo: https://gitlab.com/nanuchi/k8s-in-1-hour

## Setup

1. install minikube
2. run on terminal:

```sh
$ minikube start --driver docker
$ kubectl apply -f mongo-config.yaml
$ kubectl apply -f mongo-secret.yaml
$ kubectl apply -f mongo.yaml
$ kubectl apply -f webapp.yaml

# check if everything is running
$ kubectl get all

# open service locally
$ minikube ip 
# open browser at MINIKUBE_IP:30100 # a porta 30100 é a definida no webapp.yaml
$ minikube service webapp-service # macos only
```

## Other commands

```sh
$ kubectl get configmap
$ kubectl get secret
$ kubectl get pod

$ kubectl describe service webapp-service
$ kubectl describe pod webapp-deployment-ID
$ kubectl describe pod webapp-deployment-ID

$ kubectl logs webapp-deployment-ID # -f for continous logging
$ kubectl get svc 

$ kubectl get node -o wide # see ip of each node
$ kubectl get svc -o wide
$ kubectl get pode -o wide
```
