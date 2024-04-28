# Helm download charts from remote repos

## Procedure

```bash
helm repo add <repo-name> <repo-remote-url>
helm update

helm pull <repo-name>/<chart-name>
```

This downloads the tar file for helm charts

```bash
tar -zxvf <tar-filename>
```
