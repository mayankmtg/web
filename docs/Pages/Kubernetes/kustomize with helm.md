
---

### Using Kustomize to organize helm charts

[Link](https://cloud.google.com/anthos-config-management/docs/how-to/use-repo-kustomize-helm)

### Directory Structure

```bash
base
├── charts
│   ├── mysql-innodbcluster
│   ├── mysql-operator
│   └── proxysql-cluster
├── kustomization.yaml
└── namespace.yml

overlay
├── beta
│   ├── kustomization.yaml
└── corp
│   ├── kustomization.yaml
```

### Keeping helm charts in base directory

Local charts can be kept in `base/charts` directory

Remote charts can be fetched from repo and will be cloned inside the same `base/charts` directory.

We use the concept of [kustomize-overlays](./k8s_kustomize_overlays.md) to override the values after the helm charts have been rendered.

Note:

Another approach can be using the `helm template` command first to render the charts to valid k9s resource files and then use the concept of kustomize-overlays on the rendered charts. For such an implementation, `Makefiles` are generally used.

But since we are using overlays directly, we make use of kustomize patches directly on helm resources

### Base kustomization.yaml

Important types for using helm charts

#### Pull helm charts and use in base

[Example](./components/kustomize/helm/pull_and_use.yaml)

This pulls helm charts from remote using the specified version. There are no changes to values file made here.

#### Pull helm charts from remote and update values file

[Example](./components/kustomize/helm/pull_and_update.yaml)

This pulls helm charts from remote using the specified version. Values file is updated inline and then the charts are realised.

#### Use local charts

[Example](./components/kustomize/helm/local_and_use.yaml)

This uses charts inside `charts/` directory by referencing them by name.
Using the kustomize global variable declaration, we can change the base directory from `charts/` as well.

### Overlay kustomization.yaml

[Example](./components/kustomize/overlay.yaml)

Now that base helm charts are added, we can add overlays that can import the base and override them just like normal kustomize overlays.

---
