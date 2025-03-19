# List all the events sorted by the timestamp
To list all Kubernetes events sorted by timestamp, use the following command:
```
kubectl get events --all-namespaces --sort-by='.lastTimestamp'
```
> --sort-by='.lastTimestamp' → Sorts events based on the last occurrence time.
```
kubectl get events --all-namespaces --sort-by='.lastTimestamp' > events.log
```

