# Kubernetes Zero to Hero

## What is Kubernetes?

Kubernetes (K8s) is an open-source container orchestration platform used
to deploy, manage, scale, and monitor containerized applications.

## Why Kubernetes?

-   Automatic Scaling
-   Self-Healing
-   Load Balancing
-   Rolling Updates
-   Service Discovery
-   High Availability

## Architecture

### Control Plane

-   API Server
-   etcd
-   Scheduler
-   Controller Manager

### Worker Node

-   kubelet
-   kube-proxy
-   Container Runtime

## Core Resources

-   Pod
-   ReplicaSet
-   Deployment
-   Service
-   Namespace
-   ConfigMap
-   Secret
-   Volume
-   Ingress

## Common kubectl Commands

``` bash
kubectl get nodes
kubectl get pods -A
kubectl get svc
kubectl get deployments
kubectl describe pod <pod>
kubectl logs <pod>
kubectl exec -it <pod> -- bash
kubectl apply -f deployment.yaml
kubectl delete -f deployment.yaml
kubectl rollout status deployment/nginx
kubectl rollout undo deployment/nginx
```

## Workflow

Developer -\> Docker Image -\> Registry -\> Deployment -\> Pods -\>
Service -\> Users

## Best Practices

-   Use Namespaces
-   Use Resource Limits
-   Use Secrets for sensitive data
-   Use ConfigMaps for configuration
-   Enable Health Probes
-   Prefer Rolling Updates

## Interview Questions

1.  What is Kubernetes?
2.  Pod vs Container?
3.  Deployment vs ReplicaSet?
4.  What is etcd?
5.  What is kubelet?
6.  What is Ingress?
7.  ConfigMap vs Secret?
8.  ClusterIP vs NodePort?
9.  Rolling Update?
10. StatefulSet vs Deployment?

## Learning Checklist

-   [ ] Pods
-   [ ] Deployments
-   [ ] Services
-   [ ] ConfigMaps
-   [ ] Secrets
-   [ ] Volumes
-   [ ] Ingress
-   [ ] Helm
-   [ ] Monitoring
