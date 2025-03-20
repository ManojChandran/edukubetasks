# Create a pod which runs a command and sleeps for 100 seconds

### Manifest file for the same
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: sleep-pod
spec:
  containers:
  - name: sleep-container
    image: busybox
    command: ["sh", "-c", "echo 'Sleeping for 100 seconds'; sleep 100"]
```
### check the logs
```
kubectl logs sleep-pod -c sleep-container
```