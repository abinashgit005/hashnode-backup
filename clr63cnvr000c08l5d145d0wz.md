---
title: "Kubernetes manifests"
datePublished: Tue Jan 09 2024 08:29:55 GMT+0000 (Coordinated Universal Time)
cuid: clr63cnvr000c08l5d145d0wz
slug: kubernetes-manifests
tags: kubernetes-manifest

---

load balance manifest

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp1-loadbalancer
  labels: 
    app: myapp1
spec:
  type: LoadBalancer 
  selector:
    app: myapp1
  ports: 
    - port: 80
      targetPort: 80
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp1-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: myapp1
  template: 
    metadata: # Dictionary
      name: myapp1-pod
      labels: # Dictionary 
        app: myapp1       
    spec:
      containers: # List
        - name: myapp1-container
          image: myimage/kubenginx
          ports:
            - containerPort: 80
```