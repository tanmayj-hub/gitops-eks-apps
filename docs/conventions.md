# Conventions — gitops-eks-apps

## Principle
This repo stores the **desired state**. No manual `kubectl apply` in real workflows once Argo is live.

## Directory rules
- Cluster-scoped / bootstrap objects live under `clusters/ct-gitops-dev/`
- App manifests live under `apps/<app>/base` and `apps/<app>/overlays/dev`

## Naming
- Cluster folder: `clusters/ct-gitops-dev`
- Namespaces: `argocd`, `demo`
- Keep overlays environment-specific (`dev` now; stg/prod later)

## Kustomize
- `base/` must be environment-agnostic
- `overlays/dev` contains patches and env settings

## Argo CD (later)
- We will define Argo Applications (and optionally AppProjects) under:
  - `clusters/ct-gitops-dev/argocd/applications/`
  - `clusters/ct-gitops-dev/argocd/projects/`
