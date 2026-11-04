# Example Cluster Lifecycle Management with ArgoCD

## Repo Structure

```
projects/                               # ArgoCD AppProjects
supervisors/                            # Supervisors
supervisors/<name>                      # Supervisor Instance
supervisors/<name>/applicationset.yaml  # Cluster Lifecycle ApplicationSet for Supervisor
supervisors/<name>/cluster-<name>.yaml  # Cluster Instance
```

## Usage

Create AppProject

```
kubectl apply -f projects/dev1-cap1.yaml
# Verify
kubectl get appproject/dev1-capi
```

Create ApplicationSet

```
kubectl apply -f supervisors/dev1/applicationset.yaml
# Verify
kubectl get applicationset/dev1-capi
```

