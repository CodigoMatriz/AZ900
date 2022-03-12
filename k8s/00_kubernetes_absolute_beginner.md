> KodeKloud  
> [Kubernetes for the Absolute Beginner](https://kodekloud.com/lessons/introduction-12/)

[TOC]

---

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

>  ### Nodes
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

API Server acts as the front-end for Kubernetes which users, management devices and CLI's communicate with to interact with clusters.

etcd is a distributed reliable Key-value store where Kubernetes stores all data used to manage the cluster. Responsible for implementing locks within the cluster to ensure there is no conflict between the masters.

Scheduler is responsible for distributing work / containers across multiple nodes by looking for newly created containers.

Controllers are the brains for orchestration, which are responsible for noticing and responding when nodes / containers/ endpoints go down.

Container Runtime is the underlying software used to run containers.

kubelet is the agent that runs on each node in the cluster making sure that the containers are running on the nodes as expected.

### Master vs Worker Nodes

Workers nodes (minions) is where the containers are hosted.

Master nodes have the kubelet agent resonsible for interacting with a master to provide health information on the worker nodes and carry out actions on them as well.

All information gathered on the master node is stored in a key-value store using etcd.

Also contains a controller and a scheduler.

# Setup Kubernetes

Can be setup locally directly on your host machine or a VM using solutions like **Minikube** (dev friendly) , **MicroK8s**, **Kubeadm** (production).

Can be setup on the cloud using **Google Cloud Platform**, **Amazon Web Services**, **Azure**.

MiniKube is developer friendly and good for testing purposes, as it bundles all the different components into a single image, providing a pre-configures single node Kubernetes cluster provided as an ISO image.

# Kubernetes Concepts

Kubernetes does not deploy containers directly on the worker nodes, instead are encapsulated into a Kubeneretes object known as a **Pod**.

> ### Pod  
> Single instance of an application, the smallest object than can be created in Kubernetes

Pods share a 1:1 relation with container images running the application. If you need to scale up, you add more pods and remove pods to scale down.

Pods can contain multiple images it doesn't have to just be one. For example like in the case of needing a helper container to go along with your application container.

```sh
# Creating a Pod // Image pulled from Dockerhub
kubectl run nginx --image nginx

# View Pods
kubectl get pods
```


# Kubernetes Concepts – PODs, ReplicaSets, Deployments

## Pods with YAML

Kubernetes uses YAML files as inputs for the creation of objects and follows the following structure for the four top level fields:

```yaml
# pod-definition.yaml
apiVersion: v1
kind: Pod
meadata:
	name: myapp-pod
	labels:
		app: myapp
		type: front-end
spec:
	containers:
		- name: nginx-container
			image: nginx
```

```sh
# Command to create object using YAML
kubectl create -f pod-definition.yaml
```



| Kind    | Version    |
|:--------|:----------|
| Pod  | v1         |
| Service  | v1         |
| ReplicaSet  | apps/v1         |
| Deployment  | apps/v1         |

---

### `apiVersion` 
*string*
Defines the api version of Kubernetes to use to create the object

---

### `kind`
*string*
Refers to the type of object to be created

---

### `metadata`
*dictionary*
Definition data of the object like name, labels, etc. To note, you can only specify properties that Kubernetes expects under `metadata` but for `labels`, it can be a user defined key-value pair.

---

### `spec`
*dictionary*
Defines the specification for the object kind to be created.

## Replication Controllers and ReplicaSets

Controllers are the brains behind Kubernetes, processes that monitor Kubernetes objects. 

Replication Controller / ReplicaSets helps us manage multiple instance of a single pod. Say you have an application in a pod and that goes ╮ (. ❛ ᴗ ❛.) ╭, you'd want to have another instance running so users don't lose access to the application.

Even if using one instance, the Replication Controller / ReplicaSets will ensure that if the single pod goes unhealthy, a new pod instance is brought up. It makes it so our application has high availability, which also helps with load balancing and scaling. If the load increases we can spin up additional instances or even expand to new nodes within the cluster if resources start become limited.

### ReplicationController 
Older technology which will be replaced by ReplicaSet


```yaml
# rc-definition.yaml
apiVersion: v1
kind: ReplicationController
metadata:
	name: myapp-rc
	labels:
		app: myapp
		type: front-end
spec:
	template:
		metadata:
			name: myapp-pod
			labels:
				app: myapp
				type: front-end
		spec:
			containers:
				- name: nginx-container
					image: nginx
	replicas: 3 
```

```sh
# Command to create the replication controller
kubectl create -f rc-definition.yaml

# Command to get replication controllers
kubectl get replicationcontroller

# Command to get pods
kubectl get po
```

### ReplicaSet 
The recommended way to setup replication

Aside from the `apiVersion` and the `kind` differing from the YAML construct of the ReplicaController, a property that must be defined is a `selector`. 

A `selector` defines what pods fall under the ReplicaSet. Though pods are defined in the `template` of the ReplicaSet, a ReplicaSet can manage pods *not* defined in the YAML configuration, like pods created prior to the ReplicaSet.

```yaml
# replicaset-definition.yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
	name: myapp-replicaset
	labels:
		app: myapp
		type: front-end
spec:
	template:
		metadata:
			name: myapp-pod
			labels:
				app: myapp
				type: front-end
		spec:
			containers:
				- name: nginx-container
					image: nginx
	replicas: 3 
	selector: 
		matchLabels:
			type: front-end
```

```sh
# Command to create the replica set
kubectl create -f replicaset-definition.yaml

# Command to get replica sets
kubectl get replicaset

# Command to get pods
kubectl get po
```

The `template` section is required in case of a pod failure; ReplicaSet needs to create a new one to keep with the `replicas` defined and to do so the ReplicaSet `template` section is required.

#### Scaling

There are three ways to scale a ReplicaSet if necessary:

1. Edit the definition file and edit the `replicas` property and run the `kubectl replace` command to update the ReplicaSet  
```sh
kubectl replace -f replicaset-definition.yaml
```

2. Running the `kubectl scale` command and referencing how many replicas and the definition file / replicaset name.
```sh
# Definition File
# Does not modify the original value in the file
kubectl scale --replicas 6 -f replicaset-definition.yaml

# ReplicaSet Name
kubectl scale --replicas 6 -f replicaset myapp-replicaset
```

3. Can be setup by load -- but that was too advanced to cover for this section ༼☯﹏☯༽

#### Labels and Selectors

It is the key to help in managing the many different resources that are available within Kubernetes. In this instance, we may have hundreds of pods deployed and if we wish to monitor them via a ReplicationController / ReplicaSet we can do so via the labels we define on the pods at creation.

## Deployments

