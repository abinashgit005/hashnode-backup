---
title: "Kubernetes manifests"
datePublished: Tue Jan 09 2024 08:29:55 GMT+0000 (Coordinated Universal Time)
cuid: clr63cnvr000c08l5d145d0wz
slug: kubernetes-manifests
tags: kubernetes-manifest

---

pod\_defination.yml

```yaml
apiVersion: v1 # String
kind: Pod # String
metadata: # Dictionary
  name: myapp1-pod
  labels: # Dictionary
    app: myapp1  # Key value paids
spec:
  containers: # List
    - name: myapp1
      image: myimage/kubenginx
      ports: 
        - containerPort: 80
```

load-balance\_service.yml

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
    - name: http
      port: 80 # service port
      targetPort: 80 #container port
```

replicaset.yml

```yaml
apiVersion: apps/v1
kind: ReplicaSet 
metadata: #Dictionary
  name: myapp1-rs
spec: # Dictionary
  replicas: 3
  selector:
    matchLabels:
      app: myapp1
  template:  
    metadata: # Dictionary
      name: myapp1-pod
      labels: # Dictionary
        app: myapp1  # Key value paids
    spec:
      containers: # List
        - name: myapp1-container
          image: myimage/kubenginx
          ports: 
            - containerPort: 80  
```

deployment.yml

Deployment object in k8s is a superset of ReplicaSet.  
In deployment manifest file, in the spec section we need to give the pod specification so that it will create the desired numbers of pods (as mentioned in replicas option).  
  
\* Make sure you have same labels in pod and deployment's selector &gt; matchLabels section

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