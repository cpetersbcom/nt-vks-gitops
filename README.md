# Example VKS Cluster Lifecycle Management with ArgoCD

*Note:* 
This example uses hard-coded values from a lab environment, yours will be different.
Update namespaces, server urls, rbac group, etc accordingly.

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

# Verify creation and status
kubectl get appproject/dev1-capi -o yaml
```

Create ApplicationSet

```
kubectl apply -f supervisors/dev1/applicationset.yaml

# Verify creation and status
kubectl get applicationset/dev1-capi -o yaml
```


## Usage

### Create a new VKS guest cluster by adding new yaml manifest

Must follow the pattern of `cluster-<name>.yaml`


```
supervisors/dev1/cluster-newcluster.yaml
```

