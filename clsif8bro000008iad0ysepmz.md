---
title: "AKS review"
datePublished: Mon Feb 12 2024 04:15:25 GMT+0000 (Coordinated Universal Time)
cuid: clsif8bro000008iad0ysepmz
slug: aks-review
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1726333717334/51deea6b-05eb-49f6-8eb7-2703983f1c64.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1708360201695/d94bc8ad-00eb-407f-8c38-c7e262e40a31.png
tags: aks

---

AKS

By default when you create a AKS cluster it creates a system node pool. AKS control plane is free. EKS $2.5 per day  
In the system node pool minimum required components will be running. (whatever the nodes we will run we have to pay)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706815380438/bf9d6637-066f-46e4-bced-98e42098258f.png align="center")

### Node pools:

1. system node pool
    
2. user node pool (Linux/Windows)
    
3. virtual node
    

### Authentication:

1. system assigned managed identity
    
2. Kubernetes RBAC
    
3. AKS managed Azure AD
    

### Networking:

1. Azure CNI
    
2. standard Load balancer
    
3. Public/private cluster
    

### Integration:

1. Container Registry
    
2. monitor
    
3. Azure log analytics
    

### Basic:

1. versions
    
2. zones
    

```yaml
kubectl create --name pod1 --image nginx:latest
kubectl get pods
kubectl get po
kubectl get pods -o wide # to get more informations about the pod
kubectl describe pod pod1
kubectl get pod pod1 -o yaml # Get pod definition YAML output
```

services:  
Through service we can access the container externally from internet.

```yaml
kubectl expose pod pod1  --type=LoadBalancer --port=80 --name=pod1-service
kubectl get service 
kubectl get svc
kubectl describe service pod1-service
kubectl get service pod1-service -o yaml   # Get service definition YAML output
```

  
**How do you implement network isolation in AKS, explain briefly ?**  
We can implement network isolation in AKS in 2 ways: Network Policies and Azure Private Link.  
Network Policies: –  
Use Kubernetes-native constructs (e.g., pod labels, namespaces)  
– Define ingress/egress rules for traffic control  
– Advantages: Fine-grained control, easy integration with existing Kubernetes resources  
– Limitations: Requires additional management overhead, limited to cluster-level isolation

Azure Private Link:  
– Expose AKS API server over a private IP within the virtual network  
– Traffic remains within the Azure backbone network  
– Advantages: Enhanced security, reduced exposure to public internet, simplified network architecture  
– Limitations: Additional cost, increased complexity during setup, limited to control plane isolation