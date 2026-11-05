# Example VKS Cluster Lifecycle Management with ArgoCD

*Note:* 
This example uses hard-coded values from a lab environment, yours will be different.
Update namespaces, server urls, rbac group, etc accordingly.

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

Order of operations matters. Supervisor cluster must be registered with ArgoCD with a ManagedEntity prior to creating AppProjects, ApplicationSets, Applications, etc.

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

