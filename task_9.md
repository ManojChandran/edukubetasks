# Delete a pod without any delay
By default, Kubernetes waits for the pod to terminate gracefully. To delete a pod immediately without waiting for termination, use the --force and --grace-period=0 options.

## Force Delete a Pod Immediately
```
kubectl delete pod nginx-pod-cmd --grace-period=0 --force
```
## Force delete all the pods in a namespace
```
kubectl delete pod --all --grace-period=0 --force -n nginx-namespace
```
## Delete a Pod Stuck in Terminating State
If a pod remains in the "Terminating" state, we can forcefully remove it by manually deleting it from etcd:
```
kubectl get pod nginx-pod -o jsonpath='{.metadata.uid}'
kubectl delete pod <pod-name> --grace-period=0 --force --namespace=<namespace>
```
