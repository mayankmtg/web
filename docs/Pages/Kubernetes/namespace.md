
---

## Creating Namespace

```bash
kubectl create namespace <name of namespace>
kubectl get namespaces
```

## Namespace using config

Namespaces can be created using [config files](./components/namespace/namespace.yml)

```bash
kubectl create -f namespace.yml
```

## Using namespaces

```bash
kubectl apply -f service.yml --namespace=<namespace>
```

OR

Define within [config](./components/namespace/service_namespace.yml)

---
