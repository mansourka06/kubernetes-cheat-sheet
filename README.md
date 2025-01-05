# Kubernetes Cheat Sheet

This repository provides a comprehensive guide to Kubernetes architecture, commonly used commands, and flags.

> Kubernetes, often abbreviated as K8s, is an open-source container orchestration engine for automating deployment, scaling, and management of containerized applications.

> For additional commands and information, refer to the [Kubernetes Cheat Sheet Official Documentation](https://kubernetes.io/docs/reference/kubectl/cheatsheet/).

---

## Kubernetes Architecture

Kubernetes architecture is built around key components that work together to ensure the reliable and efficient operation of containerized workloads. Below is an overview of its components:

### Control Plane (Master Node)

- **API Server**: The central control point for all interactions with the cluster, exposing the Kubernetes API.
- **Etcd**: A distributed key-value store for storing cluster configuration data.
- **Scheduler**: Places workloads onto nodes in the cluster based on resource availability and constraints.
- **Controller Manager**: Manages controllers that regulate the cluster's state (e.g., ensuring desired replicas).
- **Cloud Controller Manager (optional)**: Interfaces with cloud provider APIs for managing cloud-specific resources.

### Nodes (Worker Nodes)

- **Kubelet**: An agent on each node that communicates with the control plane to manage containers.
- **Kube Proxy**: Maintains network rules and handles network traffic between Pods.
- **Container Runtime**: Executes and manages container processes (e.g., Docker, CRI-O, or containerd).
- **Pod**: The smallest deployable unit, containing one or more tightly coupled containers.

### Architecture Overview

> Below is a high-level overview of the Kubernetes architecture.

![Kubernetes Architecture](k8s-archi.jpg)

---

## How Kubernetes Works

Kubernetes uses a declarative model to manage containerized applications. You define the desired state of your application, and Kubernetes ensures that the actual state matches it. Here's a simplified workflow:

1. Define your application's desired state using manifests (YAML files) for resources such as **Pods**, **Deployments**, and **Services**.
2. Submit these manifests to the Kubernetes **API Server**.
3. **The API Server** stores the desired state in Etcd.
4. **The Scheduler** assigns Pods to suitable nodes based on resource requirements and constraints.
5. **Kubelet** agents on the nodes ensure Pods are running as specified.
6. **Kube Proxy** manages network rules, enabling communication between Pods and external services.
7. **Controllers** continuously monitor and reconcile the actual state with the desired state.

Example YAML manifest for a Pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: example-pod
  namespace: default
spec:
  containers:
  - name: nginx
    image: nginx:1.21
    ports:
    - containerPort: 80
```

---

## Benefits of Kubernetes

- **High Availability**: Designed for resilience with no single point of failure in the control plane.
- **Scalability**: Easily scale applications up or down by adding or removing nodes.
- **Declarative Configuration**: Define what your application should look like, and Kubernetes ensures it matches.
- **Self-Healing**: Automatically replaces failed containers or nodes to maintain application health.
- **Portability**: Provides consistent application deployment across cloud providers or on-premises environments.

---

## Conclusion

Understanding Kubernetes architecture and how it works is essential for effectively deploying and managing containerized applications. Kubernetes simplifies complex orchestration tasks, making it a leading choice for modern application management.

- Check this repository: [Kubernetes Cheatsheet Commands](https://github.com/mansourka06/kubernetes-cheatsheet-commands) for comprehensive collection of commonly used Kubernetes commands for managing pods, nodes, deployments, services, and more. Organized for quick reference.

- For more in-depth documentation, visit the [official Kubernetes documentation](https://kubernetes.io/docs/).

---

## Author(s)

- [Mansour KA](https://github.com/mansourka06)
