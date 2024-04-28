
---

## Describe

`kubect describe pod <pod-name>`

## Details on pods

`kubect get pods -o wide`

Fields displayed

```
NAME
READY
STATUS
RESTARTS
AGE
IP
NODE
NOMINATED NODE
READINESS GATES
```

## Details from container

In case we need granular details on how the container failed to start

```bash
kubectl logs pod/<pod-name> <container name>
```

---
