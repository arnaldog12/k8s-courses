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
k config set-context --current --namespace
jupyter
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