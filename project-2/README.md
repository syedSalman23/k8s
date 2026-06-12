# Kubernetes ConfigMap and Secret Project

## Project Overview

This project demonstrates how to use Kubernetes ConfigMaps and Secrets to manage application configuration and sensitive data.

The application is deployed using a Kubernetes Deployment and reads values from both ConfigMap and Secret as environment variables.

---

## Project Architecture

```text
ConfigMap
    │
    ▼
Deployment
    │
    ▼
Pod
    ▲
    │
Secret
```

---

## Project Files

```text
project-2/
│
├── configmap.yaml
├── secret.yaml
├── deployment.yaml
└── README.md
```

---

## ConfigMap

ConfigMap stores non-sensitive application configuration.

### Values

```text
APP_NAME=Salman-App
APP_ENV=Development
COMPANY=Salman-Tech
```

### Apply ConfigMap

```bash
kubectl apply -f configmap.yaml
```

### Verify

```bash
kubectl get configmap
kubectl describe configmap app-config
```

---

## Secret

Secret stores sensitive information.

### Values

```text
DB_PASSWORD=password123
API_KEY=my-api-key
```

### Apply Secret

```bash
kubectl apply -f secret.yaml
```

### Verify

```bash
kubectl get secrets
kubectl describe secret app-secret
```

---

## Deployment

The Deployment creates Pods and injects values from ConfigMap and Secret as environment variables.

### Apply Deployment

```bash
kubectl apply -f deployment.yaml
```

### Verify

```bash
kubectl get deployments
kubectl get pods
```

---

## Verify Environment Variables

Get Pod Name:

```bash
kubectl get pods
```

Enter the Pod:

```bash
kubectl exec -it <pod-name> -- bash
```

Check ConfigMap Values:

```bash
env | grep APP
```

Expected Output:

```text
APP_ENV=Development
APP_NAME=Salman-App
```

Check Secret Values:

```bash
env | grep DB
```

Expected Output:

```text
DB_PASSWORD=password123
```

Check API Key:

```bash
env | grep API
```

Expected Output:

```text
API_KEY=my-api-key
```

---

## Useful Commands

View ConfigMaps:

```bash
kubectl get configmap
```

View Secrets:

```bash
kubectl get secrets
```

View Deployments:

```bash
kubectl get deployments
```

View Pods:

```bash
kubectl get pods
```

Access Pod Shell:

```bash
kubectl exec -it <pod-name> -- bash
```

Delete Resources:

```bash
kubectl delete -f deployment.yaml
kubectl delete -f configmap.yaml
kubectl delete -f secret.yaml
```

---

## Learning Outcomes

After completing this project, I learned:

- Kubernetes ConfigMap
- Kubernetes Secret
- Environment Variables
- Kubernetes Deployment
- Pod Management
- YAML-based Kubernetes Configuration
- Injecting Configuration into Containers

---

## Author

**Syed Salman N**

DevOps | Docker | Kubernetes | AWS