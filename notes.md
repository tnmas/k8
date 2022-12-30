# Kubernetes
## What is Kubernetes?
- Manage containers by orchestrating containers
- Orchestration features:
  - High availability
  - Scalability
  - Disaster recovery
## Kubernetes Components
### Node
- Worker
- more than one pod can run inside a node
- those are the one which actually do the work
### Pod
- The Smallest unit of Kubernetes
- Abstraction over container
- A pod runs inside a node
- 1 application per pod
- Each pod gets its own IP address
- New IP address on re-creation
### Service and Ingress
- Permanent(persistent) IP address
- Communication between pods are enabled by services
- Attached to a pod
- lifecycle of pod and service not connected
- Internal and External services
  - External: to access the service from outside
  - **Ingress** comes instead of external services
### ConfigMap and Secrete
- **ConfigMap**: 
  - external configuration of your application
- **Secrete**:
  - Sensitive credentials are stored in it in a base64 encoded format
### Volumes
- to make data persistent
- by attaching a physical storage to the volume
- restarting the database won't affect the data
- it can be local or remote
### Deployment and StatefulSet
- blueprint for a pod
- abstraction of pods
- in practice, you work with deployment not with pods
- We can't replicate database using deployment because they will be accessing the same volume and that will need us to manage everything
- For databases we need **statefulSet**
- Deployment for stateless
- StatefulSet for stateful
- Databases are mostly hosted outside K8 clusters

## Kubelet
- interacts with both container and node
- starts the pod with a container inside
- It is located inside a node
- Gets the request from the scheduler

## Kube Proxy
- forwards the request to the right controller

## Container Runtime

## Master servers or nodes
- controller the cluster and nodes
- Master nodes have less resources than worker nodes
  
### API Server
- Requests goes to the API server, and it forwards the request to other processes running on the master server
- enables interaction to the cluster

### Scheduler
- API Server forwards the request to Scheduler 
- The scheduler decides where to put the pod, checks the resources on the pods

### Controller Manager
- Detect state changes
- Then it forwards the request to the scheduler

API Server -> Scheduler -> Kubelet
Controller Manager -> Scheduler -> Kubelet

###  etcd
- How does scheduler know how much resources are available inside a pod.
- All information are stored inside etcd
- But data isn't stored here
- This must be reliable

## MiniKube
- Test/local cluster setup
- creates virtual box inside your laptop
- Node runs in that virtual box

### Kubectl
- combination of UI, API and CLI clients of API Server 
