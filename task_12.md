# Create an init container in a pod
An Init Container in Kubernetes is a special type of container that runs before the main application containers in a Pod. It is used for tasks like setup, configuration, or waiting for dependencies to be ready. Init containers must complete successfully before the main containers start.

## Manifest file
```yaml
apiVersion: v1
kind: Pod
metadata:
    name: init-container-demo
spec:
    containers:
        - name: my-nginx-container
          image: nginx
          ports:
            - containerPort: 80
    initContainers:
        - name: my-nginx-init
          image: busybox
          command: ["sh", "-c", "echo 'Initializing...'; sleep 10"]
```
## apply manifest file
```
kubectl apply -f init-nginx-container.yaml
```
## Check logs from init conatiner
```
kubectl logs init-container-demo -c my-nginx-init
```