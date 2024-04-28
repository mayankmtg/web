# Create helm packaged application

```bash
helm create packaged-app
```

This creates the default helm packaged application

## Default directory structure

```txt
packaged-app
├── Chart.yaml
├── charts
├── templates
│   ├── NOTES.txt
│   ├── _helpers.tpl
│   ├── deployment.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── service.yaml
│   ├── serviceaccount.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml
```

## Explanation of helm specific components

1. `values.yaml`
    - File contains constants to be referenced from inside the template/<component> files
    - File gives common place to change attribute values
    - File enables us to re-use values of some constants

2. `Chart.yml`
    - File defines the helm chart/package
    - File contains field `type` which can be
        - application
        - library
    - File can also contains `dependencies` field to specify the dependency of other charts on parent
    - Or `dependencies` can be a part of `charts/` directory

3. `charts/`
    - This directory contains the dependency helm charts that are needed by parent project
    - More details at: https://helm.sh/docs/topics/charts/#chart-dependencies
