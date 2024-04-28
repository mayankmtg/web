
---

## Step 1

Create a Dockerfile for the image

## Step 2

Point shell's docker daemon to minikube's daemon

```
eval $(minikube -p minikube docker-env)
```

## Step 3

Create an image

```
docker  build . -t <image_name>
```

Once we build in this step, it is going to register in minikube's docker registry

## Step 4

Create k8s config for starting the container inside a pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: <pod-name>
spec:
  containers:
  - name: <container-name>
    image: <container-image>
    imagePullPolicy: Never
```

## Step 5

Start pod using the config

```
kubectl create -f <pod-filename>.yml
```

---
