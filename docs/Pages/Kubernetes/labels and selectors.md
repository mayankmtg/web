
---

`Labels` can be thought of as any key-value pair assigned to kubernetes components

Any component can have many labels.

Labels are basically used to filter out the components

E.g we want to delete all nodes which have labels (type:calculation, method:maths)

We can specify using kubectl command to only use these labels

`Selectors` are the tools that k8s uses to select and filter these labels

## Show all pods with labels

```bash
kubectl get pods --show-labels
```

## Filter pods

```bash
kubectl get pods -l <label-name>=<label-value>
```

## Types of selectors that can be used on these labels

1. Equality based selectors
    - =
    - ==
    - !=
2. Set based selectors
    - in
    - notin
    - \<exists\>
    - \<does not exists\>

We can combine selectors with AND operation (using , separator)

```bash
kubectl get pods --show-labels
```

Get the value associated with a single label for the k8s components

```bash
kubectl get pods -L=<label-key-name>
```

This is going to print all the pods with a column with all values corresponding to the <label-key-name>

```bash
kubectl get pods -L=<label-key-1>,<label-key-2>
kubectl get pods -L=<label-key-1> -L=<label-key-2>
```

## Using these labels to filter list

```bash
kubectl get pods -l='<label-key-1>=<label-value-1>'
```

To get back to our example, deleting pods with labels (type:calculation, method:maths)

```bash
kubectl delete pods -l='type=calculation,method=maths'
```

## Selectors can also be a part of config files

If we create a service, we can use selectors to define which components do we want to connect to

[Example service](./components/service/service_selectors.yml)

---
