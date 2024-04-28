
---

## [Link](https://stackoverflow.com/questions/52369247/namespace-stucked-as-terminating-how-i-removed-it)

List all the resources present in a particular namespace.
Can be used to identify which resource is blocking termination.

```bash
kubectl api-resources --verbs=list --namespaced -o name \
  | xargs -n 1 kubectl get --show-kind --ignore-not-found -n <namespace>
```

---
