# Create a deployment with replicas
kubectl command to create the deployment replicas
```
kubectl create deployment my-app --image=nginx --replicas=3
```
## manifest file for deployment
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
  namespace: nginx-namespace
  labels:
    app: my-app
spec:
  replicas: 2  # Number of replicas
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
        - name: my-container
          image: nginx
          ports:
           - containerPort: 80
```
## Scale a deployment to 5 replicas
```
kubectl scale deployment my-deployment --replicas=5
```
## Manifest file for tetsing roling update
