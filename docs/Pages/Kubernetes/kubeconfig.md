
---

Kubeconfig file is needed to access a cluster

## File format

`kubeconfig.yml`

```yml
apiVersion: v1
clusters:
- cluster:
    certificate-authority-data: <ca-data>
    server: <kubernetes-api-url>
  name: <service-name>
contexts:
- context:
    cluster: <service-name>
    user: <user-name>
  name: <user-name>@<service-name>
current-context: <user-name>@<service-name>
kind: Config
preferences: {}
users:
- name: <user-name>
  user:
    client-certificate-data: 
    client-key-data: 
```

Important considerations:

- `clusters`: This section defines the k8s cluster that we are referring to and want to access using kubectl
- `users`: This section defines the users that have access to the k8s cluster
- `contexts`: This defines the mapping between users and clusters. This is needed since a single kubeconfig can have many users in its configuration

## Using Kubeconfig

```bash
export KUBECONFIG=</absolute/path/to/kubeconfig.yml>
```

## Creating a KUBECONFIG from kubectl

```bash
# Point bash session to a KUBECONFIG file
export KUBECONFIG=</absolute/path/to/kubeconfig.yml>

# add cluster
kubectl config set-cluster <cluster-name> --server=<k8s-api-server> --certificate-authority=ca.crt --embed-certs=true

# add users
kubectl config set-credentials <user-name> --client-certificate=<client.crt> --client-key=<client.key> --embed-certs=true

# Note: embed: true adds the certificates to the kubeconfig file making it portable

# map created user with the cluster using context
kubect config set-context <context-name> --cluster=<already-created-cluster-name> --namespace=<cluster-namespace> --user=<already-created-user-name>

# Now if we want to use the create context
kubect config use-context dev
```

---
