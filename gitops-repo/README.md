# GitOps Repository

This repository contains the GitOps configuration for managing Kubernetes resources using Helm and ArgoCD.

## Structure

```
gitops-repo/
├── charts/
│   └── myapp/
│       ├── Chart.yaml
│       ├── templates/
│       │   ├── deployment.yaml
│       │   ├── service.yaml
│       │   ├── ingress.yaml
│       │   └── hpa.yaml
│       └── values.yaml        # defaults (safe, minimal)
│
├── values/
│   └── myapp/
│       ├── dev.yaml
│       ├── test.yaml
│       └── prod.yaml
│
├── platform/
│   ├── dev-test/
│   │   ├── ingress-controller/
│   │   ├── cert-manager/
│   │   │   └── cluster-issuer.yaml
│   │   └── metrics-server/
│   └── prod/
│       ├── ingress-controller/
│       ├── cert-manager/
│       │   └── cluster-issuer.yaml
│       └── metrics-server/
│
├── argocd/
│   ├── apps/
│   │   ├── myapp-dev.yaml
│   │   ├── myapp-test.yaml
│   │   └── myapp-prod.yaml
│   └── platform/
│       ├── dev-test/
│       │   ├── cert-manager.yaml
│       │   ├── ingress.yaml
│       │   └── metrics-server.yaml
│       └── prod/
│           ├── cert-manager.yaml
│           ├── ingress.yaml
│           └── metrics-server.yaml
│
└── README.md
```

## Usage

1. **Helm Charts**:
   - The `charts/` directory contains Helm charts for applications.
   - Use `values/` for environment-specific configurations.

2. **Platform Resources**:
   - The `platform/` directory contains cluster-wide resources for `dev-test` and `prod` environments.

3. **ArgoCD Applications**:
   - The `argocd/` directory contains ArgoCD application manifests for both applications and platform resources.

4. **Deployment**:
   - Use ArgoCD to sync the applications and platform resources to the respective environments.