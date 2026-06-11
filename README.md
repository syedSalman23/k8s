# Kubernetes Nginx Project

This project deploys Nginx on Kubernetes using:

- Deployment
- ReplicaSet
- Pods
- Service (NodePort)

## Deploy

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml