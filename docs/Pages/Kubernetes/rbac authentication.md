
---

RBAC (Role Based Access Control)

Roles need to be defined at the namespace level. This means that we can define which users have what access to which namespace

There are three components to consider here

1. Users
2. Roles
3. Role-bindings
4. ServiceAccount

## Users

Kubernetes does not have concept of users.

This means that we would have to user certificates and link users to certificates.

These certificates must be signed by the cluster keys and certs

### Create certificates

Follow to create [signed certificates](/knowledgebase/openssl/generate_signed_certificates.md)

### Create KUBECONFIG

Embed the certificates inside the KUBECONFIG file

Follow to create [KUBECONFIG](/knowledgebase/kubernetes/kubeconfig.md)

```bash
export KUEBCONFIG=/absolute/path/to/kubeconfig

kubect get pods
# 
# Note that this command should fail to access anything within this cluster since there are no roles defined yet
# 
```

### Create roles

Because of the problem mentioned in the above step, we need to create a role, which has permissions to do things
in the cluster

Follow to create a [role](/knowledgebase/kubernetes/components/rbac/role.yml)

### Create role bindings

Just creating the role is not enough. We need to bind the role to the user we created. For that we need rolebindings

This binds a `subject` to a `roleRef`

Follow to create a [rolebinding](/knowledgebase/kubernetes/components/rbac/rolebinding.yml)

Once rolebinding is complete, the user will have the required permissions to access the cluster

But that is not enough. We might need services/applications to interact with the cluster as well.

### Service Accounts

For services to access with certain roles, we need to create a service account

Service account creation is a combination of `serviceaccount.yml` and corresponding `pod.yml`

`serviceaccount.yml` contains nothing much but the service account name which needs to be referenced from that pod

Follow to create [serviceaccount](/knowledgebase/kubernetes/components/rbac/serviceaccount.yml) and [pod](/knowledgebase/kubernetes/components/rbac/pod-serviceaccount.yml)

This created pod will have a sercret token within the directory: `/var/run/secrets/kubernetes.io/serviceaccount`

This will have its own `secrets` and `tokens`

Now we need to define roles and bind them to this service account

Follow to create [serviceaccount roles](/knowledgebase/kubernetes/components/rbac/serviceaccount-role.yml) and [serviceaccount bindings](/knowledgebase/kubernetes/components/rbac/serviceaccount-rolebinding.yml)

## Cluster Roles and Rolebindings

These are similar to roles and rolebindings. It's just applied at the cluster level

---
