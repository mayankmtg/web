
---

## Force delete resources

```bash
kubectl delete <resource-name> --force --grace-period=0
```

## Resources deployed through operators

Resources deployed through operators, usually have a finalizer section within their configuration, which tells the resource which resource to wait for before deletion.

In case resources are stuck in `TERMINATING` state, we need to delete this section and do a manual cleanup

```bash
kubectl edit <resource-name>
```

Delete the section after `finalizers`. Save this file and proceed

Deleting resources using this can cause issues since the deletion was not clean and it did not wait for the processes it was supposed to wait for.

Important resources that could be remaining could be corresponding PVC/PV.

## List any resource that is remaining in the namespace

Delete any resources in this section if there are any remaining and have to go

[Follow for cleanup](/knowledgebase/kubernetes/list_all_namespace_resources.md)

---
