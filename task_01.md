# How to list all the control plane components and write them to a file
The Control Plane manages the cluster and ensures the desired state of applications. It consists of the following key components:

1️⃣ kube-apiserver

The entry point for all Kubernetes API requests.
Handles authentication, authorization, and validation.
Communicates with all other control plane components.

2️⃣ etcd

A distributed key-value store for storing all cluster data.
Acts as the single source of truth for the cluster state.
Highly available and consistent.

3️⃣ kube-scheduler

Assigns Pods to worker nodes based on resource availability and constraints.
Uses scheduling algorithms to optimize performance.

4️⃣ kube-controller-manager

Runs various controllers to maintain the desired state.
Examples:
Node Controller: Monitors node health.
Replication Controller: Ensures correct Pod count.
Endpoint Controller: Manages Service endpoints.

5️⃣ cloud-controller-manager (Optional, for cloud-based clusters)

Manages cloud-specific integrations (e.g., AWS, GCP, Azure).
Handles cloud-based networking, storage, and node management.

### List all the components in control-plane
```
kubectl get pods -n kube-system -o wide
```
### Write it to a file
```
kubectl get pods -n kube-system | grep -E 'kube-apiserver|kube-controller-manager|kube-scheduler|etcd' > control-plane.txt
```
### Check
```
cat control-plane.txt
```
### Print the pod names and start times to a file
```
kubectl get pods -A -o jsonpath='{range .items[*]}{.metadata.name}{"\t"}{.status.startTime}{"\n"}{end}' > pod_start_times.txt
```
