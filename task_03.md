# List all the internal IP's of all the nodes in the cluster
Nodes get their IP addresses through:

* Cloud Provider (for managed clusters) – EKS, GKE, AKS assign private/public IPs dynamically.
* DHCP (for on-prem/self-managed clusters) – IPs are assigned from the network’s DHCP server.
* Static IP Configuration – Admins can manually assign IPs.
* CNI Plugin (like Calico, Flannel, Cilium) – Handles network communication and assigns internal IPs.
### List All Internal IPs of Nodes
```
 
```
### Extract only internalIP and save to a file
```
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="InternalIP")].address}' > node-internal-ips.txt
```
### Extract only externalIP and save to a file
```
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}' > node-public-ips.txt
```
### Check
```
cat node-internal-ips.txt
cat node-public-ips.txt
```

If EXTERNAL-IP Shows <none>
If you don’t see an external IP, possible reasons:
* Your cluster is private (e.g., internal VPC network).
* Nodes are behind a LoadBalancer (Check kubectl get svc).
* Cloud provider requires explicit Elastic IP allocation (AWS, GCP).