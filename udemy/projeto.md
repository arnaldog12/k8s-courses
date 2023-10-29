# 1. inital setup
```sh
kubectl apply -f jupyter-ns
kubectl apply -f jupyter-dp
kubectl get pods -w -n jupyter
kubectl get deployments -n jupyter
```

# 1.1 change default namespace
```sh
# seta o namespace default para jupyter
# isso evita ficar colocando o `-n jupyter` em todo comando
k config set-context --current --namespace jupyter
```

# 1.2 checks
```sh
k get deployments # ok
k get replicasets # ok

# endpoints e slices são atrelados a services que ainda não foram criados
k get endpoints
k get endpointslice

k logs POD_NAME
```

# 1.3 exposing the app
```sh
kubectl port-forward jupyter-dp-fbd984b9f-hj2qh 8080:8888

# the command bellow avoid the port-forward
kubectl expose deployment jupyter-dp -n jupyter --type NodePort --name jupyter-svc
kubectl get svc

# use the commands bellow to get url and port of the service
minikube service jupyter-svc -n jupyter --url # url + port
kubectl get nodes -o yaml | grep address # url
kubectl get svc jupyter-svc -o yaml | grep nodePort # port
kubectl get svc -o wide # port
```

# 1.4 editing the service
```sh
kubectl edit service jupyter-svc
# edit nodePort to 30000
```

# 1.5 saving the service as yaml file
```sh
kubectl get svc jupyter-svc -o yaml > jupyter-svc.yaml
```

# 1.6 deleting the projetct
```sh
k delete deployments jupyter-dp # delete pods + deployment + replicasets.
k delete svc jupyter-svc # delete svc + endpoints + endpointslices
```