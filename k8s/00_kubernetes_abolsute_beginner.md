> KodeKloud  
> [Kubernetes for the Absolute Beginner](https://kodekloud.com/lessons/introduction-12/)

# Kubernetes Overview

Kubernetes (K8s) built by Google but is now an open-source project (CNCF).

## Containers Overview

Containers are not a new concept and they've been around for 10+ years. They exist in the other forms, like LXC (harder, low-level), but Docker has become the defacto standard due to the ease it brings at a higher level to create containers. 

Containers are completely isolated environments that can contain their own processes / network interaface / mounts but share the same OS kernel.

Sharing the same OS kernel means that Docker can run any OS as long as it shares the same type of kernel as the host operating system. An example would be Ubuntu, it has a linux kernel, so we can run any type of Linux OS in a container like Gentoo, Debian, Arch as they share a linux kernel. We could not for example, run a Windows container on a linux based host as that uses a linux kernel, we would need to run the containers on a Windows host.

## Container Orchestration

Container Orchestration is the process of automatically deploying and managing containers, as such, Kubernetes is an orchestration technology.

Advantages:

* Application is highly available, hardware failures don't bring application down
* Multiple instances of application across different nodes
* User traffic is load balanced across containers
* Low hardware resources, easily scale up/down

## Kubernetes Architecture

> ### Nodes
> 
> *A physical / virtual worker machine where K8s is installed and containers are launched*

If the node fails, what happens? Application is down! (╥﹏╥) 
Don't fear cause we have **clusters**.

> ### Cluster
> 
> *Set of nodes grouped together*

If one node fails the application keeps chugging about as it can be accessed from the other nodes. Having multiple nodes also helps in sharing load.

Cool, who's gonna manage all of this? (the cluster)

> ### Master
> 
> *A node with k8s installed in it configured as a master that watches over the nodes in the cluster*

Watches over the nodes in the cluster and is responsible for the orchestration of containers on the worker nodes.

### Components

When installing Kubernetes the following components are installed:

* API Server
* etcd
* kubelet
* Container Runtime
* Controller
* Scheduler
