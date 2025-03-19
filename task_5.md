# Find out where the Kubernetes master and KubeDNS are running at?
## Find Kubernetes Master (Control Plane Nodes)
The Kubernetes master components (API Server, Controller Manager, Scheduler) typically run on control plane nodes.

```
kubectl get nodes -o wide
kubectl get nodes --selector=node-role.kubernetes.io/control-plane -o wide
```
## Find Where KubeDNS (or CoreDNS) Is Running
```
kubectl get pods -n kube-system -o wide | grep dns
```
> The --selector flag in kubectl is used to filter resources based on labels. It allows you to query specific Kubernetes objects by label selectors instead of fetching all resources.

## Use JSON path to get all the node names
We can use the following kubectl command with JSONPath to get all node names in a Kubernetes cluster:
```
kubectl get nodes -o jsonpath='{range .items[*]}{.metadata.name}{"\n"}{end}'
```