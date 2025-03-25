# Create a pod and add the "runAsUser" and "fsGroup"

### runAsUser - Running Containers as a Non-Root User
`runAsUser` is a securityContext setting in Kubernetes that allows you to define the User ID (UID) under which a container's processes run.


### fsGroup - Managing File Permissions for Volumes
`fsGroup` is a securityContext setting in Kubernetes that controls group ownership of files inside a container. It ensures that a specified group ID (GID) owns all files in mounted volumes, allowing proper access control for shared storage.

### Manifest file 
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secure-pod
  labels:
    app: secure-app
spec:
  securityContext:
    fsGroup: 2000  # All files in the mounted volume will be owned by this group
  containers:
  - name: secure-container
    image: busybox
    command: [ "sleep", "3600" ]
    securityContext:
      runAsUser: 1000  # The container runs as this user instead of root
```
> runAsUser: 1000: Runs the container with UID 1000 instead of root (UID 0). This enhances security.
> fsGroup: 2000: All files in mounted volumes will be owned by group 2000.
### Apply the manifest file
```
kubectl apply -f pod-secure.yaml
```
### Check the pod security context
```
kubectl get pod secure-pod -o yaml | grep securityContext -A 5
```