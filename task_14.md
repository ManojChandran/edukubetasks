# Create a replicaset which has 3 replicas
A ReplicaSet in Kubernetes ensures a specified number of pod replicas are running at all times. It automatically creates new pods if they fail and removes excess pods if they exceed the defined count.
# Replicaset manifest file
```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-nginx-replicaset
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-nginx
  template:
    metadata:
      labels:
        app: my-nginx
    spec:
      containers:
      - name: my-container
        image: nginx
        ports:
        - containerPort: 80    
```