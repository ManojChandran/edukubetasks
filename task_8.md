# Create a pod in a namespace
We can define namespace in the metadata.labels section of the Pod manifest.
```yaml
apiVersion: v1
kind: Pod
metadata:
    name: nginx-pod
    namespace: nginx-namespace
    labels:
        app: my-nginx
        env: dev
spec:
    containers:
    - name: my-nginx-app
      image: nginx
      ports:
        - containerPort: 80
```
## apply Pod manifest
```
kubectl apply -f pod-with-namespace.yaml
```
