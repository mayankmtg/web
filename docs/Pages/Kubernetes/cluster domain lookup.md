
---

[Link](https://stackoverflow.com/questions/52940774/kubernetes-how-to-check-current-domain-set-by-cluster-domain-from-pod)

Use the following command to lookup cluster domain

```bash
kubectl run -it --image=ubuntu --restart=Never shell -- \
sh -c 'apt-get update > /dev/null && apt-get install -y dnsutils > /dev/null && \
nslookup kubernetes.default | grep Name | sed "s/Name:\skubernetes.default//"'
```

---
