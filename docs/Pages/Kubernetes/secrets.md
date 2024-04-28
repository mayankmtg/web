
---

## Adding a secret key value pair to secret store

Secrets in kubernetes are stored with base64 encoding

```bash
echo -n "password1234" | base64 -i -
```

The value retrieved can be added to the secrets config and applied

Follow for [secrets config](/knowledgebase/kubernetes/components/secrets/secrets.yml)

## Reading a secret from kubernetes

Retrieve the value corresponding to a specific key

```bash
kubectl get secrets <secret-name> --template={{.data.<key-name>}} | base64 -D
```

Printing all secrets from a secrets file

```bash
kubectl get secrets

kubect get secrets/<secret-name> -o yaml
```

## Editing a secret

Get the value for new secret after base64 encoding

```bash
kubectl edit secrets/<secret-name>
```

And edit the value that needs to be updated

Note: Do not change metadata. K8s will handle that

---
