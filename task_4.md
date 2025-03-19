# Get all the objects in all the namespaces
Namespaces provide a logical separation of resources within a cluster. They are useful for:
* Multi-tenancy – Different teams/projects can use the same cluster without interference.
* Resource Management – Apply resource quotas and limits at the namespace level.
* Access Control – Assign RBAC policies per namespace.
* Organized Workloads – Avoid naming conflicts and keep resources structured.

```
kubectl create namespace my-namespace
```
```
kubectl get all --all-namespaces -o json
```

## Manifest file for creating namespace

```yaml
apiVersion: v1
kind: Namespace
metadata:
    name: nginx-namespace
    labels:
        env: dev
    annotations:
        created-by: "admin"
        purpose: "testing"
    finalizers:
        - kubernetes
```

## Apply the manifests
```
kubectl apply -f namepace-with-label.yaml
```

> When creating a namespace, you can define additional configurations such as labels, annotations, resource quotas, and limits.
