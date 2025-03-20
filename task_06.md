# Find the static pod path
A static pod is a pod managed directly by the kubelet on a node, without involving the Kubernetes API server. Static pods are commonly used for running control plane components like kube-apiserver, kube-controller-manager, and etcd in self-hosted clusters.

Static Pod Characteristics:
* Created and managed by the kubelet on a node.
* Not scheduled by the Kubernetes Scheduler.
* Does not appear in kubectl get deployments or kubectl get replicasets.
* Runs as long as the kubelet is running.

Static pods are defined as YAML files placed in a specific directory on the node. The default location is:
```
cat /var/lib/kubelet/config.yaml | grep staticPodPath
```

## Why static pod path was ointroduced?
Static pod paths were introduced in Kubernetes to enable node-level self-management of critical components, especially in scenarios where the Kubernetes control plane is not yet fully functional or needs to be bootstrapped.

## How Static Pod Path Works?
The kubelet monitors the static pod manifest directory (e.g., /etc/kubernetes/manifests/).
Any YAML file in this directory is automatically deployed as a pod.
If the file is deleted, the pod is also removed.
If the file is modified, the pod is automatically restarted with the new configuration.