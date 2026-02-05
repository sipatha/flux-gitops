# GitOps using FluxCD

### Prerequisites
The latest version of the software components are required

* `flux` 
* Github PAT with rights to https://github.com/sipatha/flux-gitops

### Bootstraping

Run the command below to bootstrap FluxCD to the cluster.

```bash
# set the Github PAT
export GITHUB_TOKEN=github_pat_11AA...
# bootstrap fluxcd
flux bootstrap github --token-auth --owner=sipatha --repository=flux-gitops --branch=develop --path=clusters/cluster-001 --personal
# add infra kustomization
flux create kustomization flux-infrastructure-system --source=GitRepository/flux-system --path="./infrastructure/cluster-001" --prune=true --interval=10m0s
```

