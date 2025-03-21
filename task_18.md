# Create a service from the pod and run a DNS lookup to check the service
### Pod Creation

Let's create a pod named nginx-pod that runs a simple Nginx container.
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
### Service creation 
```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-nginx # pod selection done
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
  type: ClusterIP
```
### Test Service
```
kubectl run dns-test --image=busybox:1.28 --restart=Never --rm -it -- nslookup my-service
Server:    10.96.0.10
Address 1: 10.96.0.10 kube-dns.kube-system.svc.cluster.local

Name:      my-service
Address 1: 10.96.198.100 my-service.default.svc.cluster.local
```
### Created a new deployment with same labels for pods
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment-1
#  namespace: nginx-namespace
  labels:
    app: my-app
spec:
  replicas: 2  # Number of replicas
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
### Checked the endpoints
```
% kubectl get endpoints my-service
NAME         ENDPOINTS                                      AGE
my-service   10.244.1.23:80,10.244.2.28:80,10.244.2.29:80   33m

```

