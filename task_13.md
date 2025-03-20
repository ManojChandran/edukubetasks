# Create a pod that will only be scheduled on a node with a specific label
A label in Kubernetes is a key-value pair assigned to Kubernetes resources to organize, categorize, and select them efficiently. Labels are used for filtering and grouping resources without affecting their functionality.
|Resource |	Purpose of Labeling |
|------|---------|
|Pods	|Grouping similar applications (e.g., app=nginx)|
|Nodes	|Assigning workloads to specific nodes (e.g., region=us-east-1)|
|Deployments	|Identifying different versions of apps (e.g., version=v1)|
|Services	|Selecting Pods for traffic routing (e.g., service=backend)|
|ConfigMaps & Secrets	|Categorizing configurations (e.g., environment=staging)|
|Namespaces	|Organizing workloads (e.g., team=devops)|
|PersistentVolumes (PVs)	|Differentiating storage types (e.g., storage-class=ssd)|
|Ingress	|Mapping domains to services (e.g., ingress=public)|

## Label a node
```
kubectl label nodes kind-worker env=prod
```
## View a node label
```
kubectl get node kind-worker --show-labels 
```
## Create a Pod that will only be scheduled on nodes with the env=prod label
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-node-selected-pod
spec:
  containers:
    - name: nginx
      image: nginx
      ports:
      - containerPort: 80
  nodeSelector:
    env: prod
```

## kubernetes explain
Kubernetes provides a built-in way to inspect API resources.
```
kubectl explain pod.spec.containers
```