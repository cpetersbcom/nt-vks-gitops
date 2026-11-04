# Example VKS Cluster Lifecycle Management with ArgoCD

## Repo Structure

```
projects/                                  # ArgoCD AppProjects
supervisors/                               # VCF Supervisors
supervisors/<name>                         # Supervisor Instance
supervisors/<name>/applicationset.yaml     # Cluster Lifecycle ApplicationSet for Supervisor
supervisors/<name>/cluster-<name>.yaml     # VKS Guest Cluster Instance
```

## Deployment

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


## Usage

### Create a new VKS guest cluster by adding new yaml manifest

Must follow the pattern of `cluster-<name>.yaml`


```
supervisors/dev1/cluster-newcluster.yaml
```

