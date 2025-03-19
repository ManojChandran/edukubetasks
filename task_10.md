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
kubectl logs --since=5m nginx-pod | grep "failed"
```