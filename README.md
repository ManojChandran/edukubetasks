# edukubetasks
set of simple Kubenetes tasks

### Tasks
* Create a deployment with replicas
* Create a pod with labels
* Create a pod in a namespace
* Create a pod and expose it
* Upgrade a deployment by using rolling update
* Create a pod with a command
* Taint a node to be unschedulable
* Create a new service account, clusterrole and clusterrolebinding
* Create a NetworkPolicy that allows all pods in the namespace to use one port
* List all the internal IP's of all the nodes in the cluster
* Create a multipod with two containers and add a command
* Create a new user and grant him access to the cluster
* Create a service from the pod and run a DNS lookup to check the service
* Create a secret and mount it to the pod
* List all the the persistent volumes sorted by capacity
* Use JSON path to get all the node names
* Show the logs from the container
* Create a new ingress resource and expose the service on a path
* Overwrite the label of the pod with a value
* Upgrade the image in the deployment, check the history and roll back
* Find out which pods are available with the label in the cluster
* Find out why a pod is failing and fix the issue
* Create a pod that will only be scheduled on a node with a specific label
* Create a pod which uses a persistent volume for storage
* Remove the taint added to the node
* Take a backup and restore ETCD
* Schedule a pod on the node by using tolerations
* Apply autoscaling to the deployment
* Check how many nodes are in ready state
* Create a pod and set the environment variable
* Create a configmap and add it to the pod
* List all the events sorted by the timestamp
* Create a pod with a non-persistent volume
* Investigate the node and bring it back to ready state
* Make the node unavailable and reschedule all the pods on it
* Create a pod which echo's a sentence, exists and is deleted automatically
* Annotate an existing pod and use a value
* Get a list of all the pods in all the namespaces
* Update the password in the existing configmap
* Troubleshoot a pod which is not scheduling on the node and fix the issue
* Create a network policy and allow traffic from a pod to two services
* Create a pod and set "SYS_TIME", and let it sleep for one hour
* Create a clusterrole and a clusterrolebinding
* Get the IP address of a pod
* Find out the version of the cluster
* Change the mountpath of a container in a statefulset
* Create a cronjob which prints the date and "Running" every minute
* Create a pod with container port 80
* Monitor the logs of a pod
* Rollback a deployment to revision 1
* List a pod with custom columns
* For a pod, set the CPU memory requests and limits
* Create a pod with a non-persistent storage
* Troubleshoot a failed pod and make it running again
* Expose a pod internally and create a test-pod for look-up
* Create a DaemonSet
* Get all the objects in all the namespaces
* Create a pod and assign it to the node
* Find all the pods with a specific label
* Create a taint on the node
* Create a pod and set tolerations
* Check the image version of a pod without using the describe command
* Find out where the Kubernetes master and KubeDNS are running at
* Print the pod names and start times to a file
* Create a pod which runs a command and sleeps for 100 seconds
* Create a pod and specify a CPU request and a CPU limit
* Scale a deployment to 5 replicas
* List all the secrets and configmaps in the cluster in all namespaces
* Create a NetworkPolicy which denies all the ingress traffic
* Create an init container in a pod
* List the logs of the pod and search for the pattern "start"
* Expose the deployment
* Create two pods with different labels
* Create a clusterrole, service account and rolebinding
* Find the static pod path
* Delete a pod without any delay
* Grep the current context and write it to a file
* Get a list of all the pods which were recently deleted
* Troubleshoot the pod and fix the issue
* Create a pod with a storage which lasts as long as the lifetime of the pod
* Create a pod and add the "runAsUser" and "fsGroup"
* Troubleshoot and fix the kubeconfig file
* Create a pod and set "NET_ADMIN"
* Delete all the pods with a specific label
* Create a multipod with 3 containers
* Replace a pod with an existing yaml file and verify after
* Change the requested storage size of the PersistentVolumeClaim
* Edit an existing pod and add a command
* Add a readiness probe to an existing deployment
* Get all contexts and write it to a file
* Create a replicaset which has 3 replicas
* List all the control plane components and write them to a file
* Upgrade the cluster

## Kind clusters

To create and destroy a Kind (Kubernetes in Docker) cluster with 3 nodes (1 control-plane, 2 worker nodes), follow these steps:

### Prerequisites
Ensure you have:

* Docker installed and running.
* Kind installed (kind version to verify).
* Kubectl installed (kubectl version to verify).

### Create a YAML config file (kind-cluster.yaml):
```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
  - role: worker
```
* Run the following command to create the cluster:
```
kind create cluster --name my-cluster --config kind-cluster.yaml
```
This creates:
* Control Plane Node
* Worker Nodes

### Verify Cluster
Check if the cluster is running:
```
kubectl get nodes
NAME                     STATUS   ROLES           AGE   VERSION
my-cluster-control-plane Ready    control-plane   1m    v1.28.0
my-cluster-worker        Ready    <none>          1m    v1.28.0
my-cluster-worker2       Ready    <none>          1m    v1.28.0
```
### Destroy (Delete) the Kind Cluster
To delete the cluster:

```
kind delete cluster --name my-cluster
```
This removes all resources and stops all nodes.

