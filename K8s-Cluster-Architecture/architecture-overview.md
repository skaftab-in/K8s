# Kubernetes Cluster Architecture Overview

The Kubernetes cluster is composed of a **control plane** and **worker nodes**. This architecture is designed to manage containerized applications at scale.

## Control Plane Components

1. **API Server:** 
   - The core component of the control plane.
   -  Used to interact with the cluster. 
   - Exposes the Kubernetes API, which is used by users, components, and external components to communicate with the cluster.

2. **Etcd:**
   - A distributed key-value store that holds the configuration data and the current state of the cluster.
   - It is the central database of Kubernetes.

3. **Controller Manager:**
   - Runs controllers that regulate the state of the cluster, such as ensuring that the desired number of pods is running.
   - Magages scaleing up/down ,replicaset
4. **Scheduler:**
   - Assigns pods to nodes based on resource availability and other constraints.

## Worker Node Components

1. **Kubelet:**
   - An agent that runs on each worker node.
   - Ensures that the containers described in the pod specs are running and healthy.

2. **Kube-Proxy:**
   - Manages network rules on each node to allow communication between pods and across nodes.

3. **Container Runtime:**
   - Responsible for running containers (e.g., Docker, containerd).

## Cluster Communication

- **Pods** are the smallest deployable units in Kubernetes and run on worker nodes.
- **Services** expose pods to the network, making them accessible internally or externally.
- **Networking** ensures communication between the control plane, worker nodes, and external users.

![Kubernetes Cluster Architecture](kubernetes-Cluster-architecture.svg)

This architecture allows Kubernetes to efficiently manage, scale, and maintain containerized applications across multiple environments.

