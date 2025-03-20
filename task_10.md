# Show the logs from the container
## logs from Pod
```
kubectl logs nginx-pod
```
## logs from container
```
kubectl logs nginx-pod -c my-nginx-app

```
## logs with filter
```
kubectl logs --since=5m nginx-pod | grep "start"
```
## get logs from the recently deleted Pod
```
kubectl get events --field-selector involvedObject.kind=Pod -o json | jq -r '.items[] | select(.reason=="Deleted") | .involvedObject.name'
```