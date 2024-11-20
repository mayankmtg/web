
---

Pods can contain multiple containers.

If we wish to restart a single container from a pod (e.g a sidecar container), without affecting the remaining containers,
then there is no direct way using kubectl api.

But since pods monitor the containers they are running, killing a container would eventually force the pod to start it again.

## Solution

```bash
kubectl exec -it pods/<pod-name> -c <container-name> -- /bin/sh -c "kill 1"
```

When the container restarts, it can read the updated configmaps/secrets if any.

---
