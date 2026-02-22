# Runbook: Builder Chat 0 — Apps Repo Bootstrap

## Goal
Create an industry-aligned GitOps repo structure for `ct-gitops` (dev) without requiring a running cluster.

## Done
- Repo exists: `tanmayj-hub/gitops-eks-apps`
- `clusters/ct-gitops-dev` present with namespace manifests
- `apps/demo` present with base + overlays/dev
- Added README + conventions docs
- Normalized formatting + LF endings

## Validation
- `kustomize build clusters/ct-gitops-dev` succeeds (CI will enforce)
- `kustomize build apps/demo/overlays/dev` succeeds

## Next
Proceed to Builder Chat 1+: install/bootstrap Argo CD from infra repo and point it at this repo.
