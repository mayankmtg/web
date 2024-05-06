# Kubernetes Cheatsheet

## Kubectl common commands

```bash
kubectl version
kubectl get nodes
kubectl get pod
kubectl get services
```

## Creating Deployments

```bash
kubectl create deployment <deployment_name> --image=<image_name>
kubectl get deployment
kubectl get replicaset
kubectl edit <deployment name>
```

## Debugging Pods

```bash
kubectl logs <pod name>
kubectl describe pod <pod name>
```

## Execing into pods

```bash
kubectl exec -it <pod name> -- command
```

## Delete Deployment/Pods

```bash
kubectl get deployment
kubectl get pod
kubectl delete deployment <deployment name>
```
