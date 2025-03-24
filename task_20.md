# Create a pod and specify a CPU request and a CPU limit
## Manifest file
```
apiVersion: v1
kind: Pod
metadata:
  name: cpu-limited-pod
spec:
  containers:
  - name: my-container
    image: nginx
    resources:
      requests:
        cpu: "250m"
      limits:
        cpu: "500m"
```
## Apply Manifest file
```
kubectl apply -f cpu-range-limit.yaml
```

