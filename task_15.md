# Taint a node to be unschedulable
To taint a node and make it unschedulable, you can use the kubectl taint command. Tainting a node means that Pods will not be scheduled on it unless they have a matching toleration.

## taint a node
```
kubectl taint nodes kind-worker dedicated=special:NoSchedule
```
## Check taint is aaplied on a Node or not
```
kubectl get node kind-worker -o json | jq '.spec.taints'     
[
  {
    "effect": "NoSchedule",
    "key": "dedicated",
    "value": "special"
  }
]
```
## To unTaint a node
```
kubectl taint nodes kind-worker dedicated=special:NoSchedule-
```
