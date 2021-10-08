# Kubernetes

### Node and Pod

### Node

* 3 processes must run on every node
  * container runtime
  * kubelet
  * kube proxy
* worker nodes do all the main work of serving the app

#### Pod

* smallest unit of K8, abstraction over container
* Usually only one application per pod
* Each pod get its own IP address
* they should be easily replaceable
* they are Ephemeral, temporary
* new IP address gets assigned to new resource, so you have to adust IP address everyone

#### Service

* permament IP address
* lifecycle of Pod and Service are NOT connected
* two types of services :
  * external services
  * internal services
* also works as internal load balancer

#### Ingress

* Ingress : request first goes to ingress and ingress forwards it to the respective services

#### ConfigMap & Secret

* external configuration of your application
* secret : used to store secret data, in base64 encoded format

#### Volumes

* volume is used to store permament data like database etc ..,
* could be remote, inside the VM or outside the k8 cluster

#### Deployment and stateful set

* deployment is the backend app running, it can be easily created or destroyed
* stateful set are those that needs to persists data, like database or object store

### Master Node

* All managing service run on master node
  * API server : handles
    * incoming request to ALTER nodes
    * forwards them to required services
  * Scheduler : handles
    * receives request from API server
    * deciding where to deploy the thing
    * pass the request to kubelet
  * Controller Manager : handles
    * detects state changes
    * makes request to scheduler for actions to be taken
  * etcd : stores the state of cluster
* There shoulde be 2 master nodes

MiniKube : 1 node k8 cluster for testing purposes

## Namespaces

* able to organize resources in namespaces
* virtual cluster inside a k8 cluster
* kube-system : 
  * includes system process
  * master/main kubectl process
* kube-public
  * heartbeats of nodes
  * each node has associated lease object in namespaces
  * determines the availability of node
* default
  * resources you create are located here

## Commands Kubenetes

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

