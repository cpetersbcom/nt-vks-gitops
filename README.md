# Example VKS Cluster Lifecycle Management with ArgoCD

Example of managing the lifecycle of VKS guest clusters with GitOps.
This instance of ArgoCD lacks Kustomize which results in some duplication.

The overall flow:
- Register supervisor cluster with ArgoCD
- Create an ArgoCD AppProject with limited scopes
- Create an ApplicationSet for managing guest clusters

Note: Grep for 'cpeters' and replace accordingly


## Repo Structure

```
bootstrap/                                 # Supervisor Registration with ArgoCD
projects/                                  # ArgoCD AppProjects
supervisors/                               # VCF Supervisors
supervisors/<name>                         # Supervisor Instance
supervisors/<name>/applicationset.yaml     # Cluster Lifecycle ApplicationSet for VKS Guest Clusters
supervisors/<name>/clusters/<cluster>/     # VKS Guest Cluster Instance
```

## Deployment

### Register Supervisor Cluster with ArgoCD

```
kubectl apply -f bootstrap/dev1/managedentity-supervisor.yaml

# Verify creation and status
kubectl get managedentity/supervisor -o yaml
```

### Create AppProject

```
kubectl apply -f projects/dev1-cap1.yaml

# Verify creation and status
kubectl get appproject/dev1-capi -o yaml
```


### Create ApplicationSet

```
kubectl apply -f supervisors/dev1/applicationset.yaml

# Verify creation and status
kubectl get applicationset/dev1-capi -o yaml
```


## Usage

### Create a new VKS guest cluster by adding new dir under clusters/


```
supervisors/dev1/clusters/<my-new-cluster>
```

## Todo / Unimplemented

### Fine Grain RBAC

Currently the RBAC group is assigned to my user account with full admin permissions
Create vSphere User/Group with restricted permissions and adjust RBAC in AppProject
