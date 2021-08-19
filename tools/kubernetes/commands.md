# Commands

### Commands Kubenetes

* minikube = mc
* minikube kubectl = mkc

```bash
# to list nodes
mkc get nodes

# start or stop mc
mc start|stop

# to get version
mkc version

# to get mc status
mc status

# to get pod
mkc get pod

# to get service
mkc get services

# to get help mkc
mkc create -h

# create deployment
kc create deployment nginx-depl #image=nginx

# create a replica set
kc get replicaset

# to conf file
kc edit deployment nginx-depl

# to use nano as editor for conf file, add this to .profile 
export KUBE_EDITOR=nano

# get logs 
kc logs [name of pod]

# interact with terminal of pod
kc exec -it [name of pod] bash

kubectl apply -f nginx-deployment.yaml

# init secrets
kc apply -f mongodb-dp-secret.yaml

# to get service
kc get service

# get namespaces
kc get namespaces

# create a new namespace
kc create namespace my-namespace
```

