# Kubernetes Nginx Deployment Project

## Overview

This project demonstrates how to deploy an Nginx application on a Kubernetes cluster using Deployment and Service YAML manifests.

The project was deployed and tested on a Kubernetes cluster created using Kind (Kubernetes IN Docker).

## Project Architecture

```text
Kubernetes Cluster
        │
        ▼
Deployment (nginx-web)
        │
        ▼
ReplicaSet
        │
        ▼
3 Nginx Pods
        │
        ▼
Service (NodePort)
        │
        ▼
Browser
```

## Technologies Used

* Kubernetes
* Docker
* Kind
* kubectl
* Nginx
* Git
* GitHub

## Project Structure

```text
k8s-project/
│
├── deployment.yaml
├── service.yaml
└── README.md
```

## Kubernetes Concepts Covered

### Cluster

A Kubernetes Cluster is a collection of nodes that work together to run containerized applications.

### Node

A Node is a worker machine in Kubernetes. In this project, the Kind control-plane container acts as the Kubernetes node.

### Pod

A Pod is the smallest deployable unit in Kubernetes. Each Pod runs an Nginx container.

### Deployment

A Deployment manages Pods and ensures the desired number of replicas are running.

### ReplicaSet

A ReplicaSet maintains the required number of Pod replicas.

### Service

A Service provides a stable network endpoint and load-balances traffic to Pods.

## Deployment Configuration

The Deployment creates:

* 3 Nginx Pods
* Automatic self-healing
* Automatic Pod recreation
* Rolling update support

Deployment file:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-web
spec:
  replicas: 3
```

## Service Configuration

The Service:

* Exposes the application
* Provides load balancing
* Connects users to Pods

Service file:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-web-service
spec:
  type: NodePort
```

## Create Kubernetes Cluster

```bash
kind create cluster --name salman-cluster
```

Verify:

```bash
kubectl get nodes
```

## Deploy Application

Apply Deployment:

```bash
kubectl apply -f deployment.yaml
```

Apply Service:

```bash
kubectl apply -f service.yaml
```

Verify Resources:

```bash
kubectl get all
```

## Useful Commands

### View Deployments

```bash
kubectl get deployments
```

### View Pods

```bash
kubectl get pods
```

### View Services

```bash
kubectl get svc
```

### View ReplicaSets

```bash
kubectl get rs
```

### Describe Deployment

```bash
kubectl describe deployment nginx-web
```

### Describe Service

```bash
kubectl describe svc nginx-web-service
```

### View Logs

```bash
kubectl logs <pod-name>
```

### Access Pod Shell

```bash
kubectl exec -it <pod-name> -- sh
```

## Scaling Application

Scale to 5 Pods:

```bash
kubectl scale deployment nginx-web --replicas=5
```

Verify:

```bash
kubectl get pods
```

## Self-Healing Demonstration

Delete a Pod:

```bash
kubectl delete pod <pod-name>
```

Kubernetes automatically creates a replacement Pod.

## Access Application

Using Port Forward:

```bash
kubectl port-forward service/nginx-web-service 8080:80
```

Open browser:

```text
http://localhost:8080
```

Expected Output:

```text
Welcome to nginx!
```

## Learning Outcomes

After completing this project, you will understand:

* Kubernetes Architecture
* Cluster
* Node
* Pod
* Deployment
* ReplicaSet
* Service
* Scaling
* Self-Healing
* Port Forwarding
* YAML-based Kubernetes Deployments

## Author

Syed Salman

DevOps Enthusiast | AWS | Docker | Kubernetes
