# Create a pod with labels
We can define labels in the metadata.labels section of the Pod manifest.

### manifest file 
```yaml
apiVersion: v1
kind: Pod
metadata:
    name: nginx-pod
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
### apply Pod manifest
```
kubectl apply -f pod-with-labels.yaml
```
### Command to create Pod
```
kubectl run nginx-pod-cmd --image=nginx --labels="app=my-app,env=production"
```

### Get the IP address of a pod
```
kubectl get pod nginx-pod-cmd -o wide
```
### Find out which pods are available with the label in the cluster
```
kubectl get pods -l app=my-nginx
kubectl get pods -n nginx-namepace -l app=my-nginx
```