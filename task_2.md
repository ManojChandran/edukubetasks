# Get all contexts and write it to a file
A Kubernetes context is a configuration in kubectl that allows users to switch between multiple clusters, user credentials, and namespaces.

A context includes:

* Cluster (Which Kubernetes cluster to connect to)
* User (The credentials used for authentication)
* Namespace (Default namespace for kubectl commands)

> Stored in the ~/.kube/config file.

### List All Contexts
```
kubectl config get-contexts
```
### Write to a file
```
kubectl config get-contexts > kube-contexts.txt
```
### Check
```
cat kube-contexts.txt
```
