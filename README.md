# ct-gitops (dev) — Apps (GitOps desired state)

This repo is the **GitOps source of truth** for what runs on the EKS cluster.

- **Project slug:** `ct-gitops`
- **Environment:** `dev`
- **Region:** `us-east-2`
- **Namespaces:** `argocd`, `demo`
- **Infra repo:** https://github.com/tanmayj-hub/gitops-eks-infra

> Builder Chat 0 scope: repo structure + conventions only. Argo CD is not installed yet.

## Layout
- `clusters/ct-gitops-dev/` — cluster entrypoint (namespaces + Argo applications later)
- `apps/` — app definitions (Kustomize base + overlays/dev)

## How Argo CD will use this repo (later)
We will use an "app-of-apps" style:
- A small set of Argo `Application` resources in `clusters/ct-gitops-dev/argocd/applications/`
- Each application points to an `apps/<name>/overlays/dev` path

## Local validation (no cluster needed)
Once you have kustomize installed:
- `kustomize build clusters/ct-gitops-dev`
- `kustomize build apps/demo/overlays/dev`

## PR workflow
Branch → PR → CI runs → 1 approval → squash merge.
`main` represents desired state for `dev`
