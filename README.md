# Kubernetes Cheat Sheet

This repository provides a comprehensive guide to Kubernetes architecture, commonly used commands, and flags.

---

## Table of Contents

- [Introduction](#introduction)
- [Kubernetes Architecture](#kubernetes-architecture)
- [How Kubernetes Works](#how-kubernetes-works)
- [Benefits of Kubernetes](#benefits-of-kubernetes)
- [Kubernetes commonly used commands](#kubernetes-commonly-used-commands)
- [Conclusion](#conclusion)

---

## Introduction

Kubernetes, often abbreviated as K8s, is an open-source container orchestration engine for automating deployment, scaling, and management of containerized applications.

For additional commands and information, refer to the [Kubernetes Cheat Sheet Official Documentation](https://kubernetes.io/docs/reference/kubectl/cheatsheet/).

## Kubernetes Architecture

Kubernetes architecture is built around key components that work together to ensure the reliable and efficient operation of containerized workloads. Below is an overview of its components:

### Architecture Overview

> Below is a high-level overview of the Kubernetes architecture.

![Kubernetes Architecture](k8s-archi.jpg)

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

## Kubernetes commonly used commands

### Pod Commands

```bash
kubectl get pod                # Get pod
kubectl get pod -o wide         # Get pod wide information
kubectl get pod -w              # Get pod with watch
kubectl get pod -o yaml         # Get pod in YAML format
kubectl edit pod <pod_name>     # Edit pod
kubectl describe pod <pod_name> # Describe pod
kubectl delete pod <pod_name>   # Delete pod
kubectl logs pod <pod_name>     # Logs of the pod
kubectl exec -it pod <pod_name> /bin/bash # Execute into pod
```

### Node Commands

```bash
kubectl describe node <node_name> # Describe node
kubectl get node <node_name>      # Get node
kubectl get node <node_name> -o yaml # Get node in YAML format
kubectl drain node <node_name>    # Drain node
kubectl cordon node <node_name>   # Cordon node
kubectl uncordon node <node_name> # Uncordon node
```

### Creating Objects

```bash
kubectl apply -f <file_name>.yaml                  # Create resource from a file
kubectl apply -f ./<directory_name>               # Create resources from a directory
kubectl apply -f https://<url>                    # Create resource from URL
kubectl run <pod_name> --image=<image_name>       # Create pod
kubectl create deployment <deployment_name> --image=<image_name> # Create Deployment
kubectl create configmap <configmap_name> --from-literal=<key>=<value> # Create ConfigMap
kubectl create secret generic <secret_name> --from-literal=<key>=<value> # Create Secret
```

### Monitoring Usage Commands

```bash
kubectl top node <node_name>  # Get node CPU and memory utilization
kubectl top pods <pod_name>   # Get pod CPU and memory utilization
```

## Deployment Commands

```bash
kubectl get deployment <deployment_name>        # Get Deployment
kubectl describe deployment <deployment_name>   # Describe Deployment
kubectl scale deployment <deployment_name> --replicas=<replicas> # Scale Deployment
```

### Service Commands

```bash
kubectl get service <service>                  # Get Service
kubectl describe service <service>             # Describe Service
kubectl delete service <service>               # Delete Service
```

### Ingress Commands

```bash
kubectl get ingress                             # Get Ingress
kubectl describe ingress <ingress_name>        # Describe Ingress
kubectl delete ingress <ingress_name>          # Delete Ingress
```

### Endpoints Commands

```bash
kubectl get endpoints <endpoints_name>         # Get Endpoints
```

### DaemonSet Commands

```bash
kubectl get daemonset <daemonset_name>         # Get DaemonSet
kubectl describe daemonset <daemonset_name>    # Describe DaemonSet
kubectl delete daemonset <daemonset_name>      # Delete DaemonSet
```

### Job Commands

```bash
kubectl get job <job_name>                     # Get Job
kubectl describe job <job_name>                # Describe Job
kubectl delete job <job_name>                  # Delete Job
```

### Rollout Commands

```bash
kubectl rollout restart deployment <deployment_name>          # Restart Deployment
kubectl rollout undo deployment <deployment_name>             # Undo Deployment to latest revision
kubectl rollout history deployment <deployment_name>          # Get rollout history
```

### Secret Commands

```bash
kubectl get secret <secret_name>               # Get Secret
kubectl describe secret <secret_name>          # Describe Secret
kubectl delete secret <secret_name>            # Delete Secret
```

---

## Conclusion

Understanding Kubernetes architecture and how it works is essential for effectively deploying and managing containerized applications. Kubernetes simplifies complex orchestration tasks, making it a leading choice for modern application management.

For more in-depth documentation, visit the [official Kubernetes documentation](https://kubernetes.io/docs/).

---

## Author(s)

- [Mansour KA](https://github.com/mansourka06)
