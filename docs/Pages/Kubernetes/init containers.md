
---

Any pod, deployment or statefulset; specifically a pod; can have multiple containers running.

There is another section called init-containers which are run before the containers section

- Init-container always runs to completion. This means that init-container must finish before the starting of the next container/init-container
- Init-containers are spawned iteratively. This means that once the first init-container finishes, then the next one starts. Once all init-containers are started and finished, the containers block runs

### [Usage](components/pod/pod_init-containers.yml)

### [Link](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/)

---
