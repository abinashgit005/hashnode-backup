---
title: "ConfigMaps and secrets in K8s"
datePublished: Sat Jan 20 2024 14:22:07 GMT+0000 (Coordinated Universal Time)
cuid: clrm5ryrl000109l641ts7di5
slug: configmaps-and-secrets-in-k8s
tags: kubernetes-configmap, kubernetes-secrets

---

This article gives a brief idea on ConfigMaps and secrets in K8s.

ConfigMaps can be used to provide configuration data in the form of key value pairs.

**<mark>why we use ConfigMaps ?</mark>**  
when we have a lot of pod definition file, it is difficult to manage the environment data stored in it. we can place this information out of pod definition file and manage it centrally with configuration map.

**abiconfig.txt**

```yaml
parameter1 = value1
parameter2 = value2
```

**<mark>How can you use the ConfigMap ?</mark>**

There are three main ways to use a ConfigMap  
**Filesystem:** You can mount a ConfigMap into a Pod. A file is created for each entry based on the key name. The contents of that file are set to the value.  
**Environment variable**: A ConfigMap can be used to dynamically set the value of an environment variable.  
**Command-line argument:** Kubernetes supports dynamically creating the command line for a container based on ConfigMap values

```yaml
 kubectl create configmap abiconfig \
 --from-file=abiconfig.txt \
 --from-literal=extra-param=prod \ # This has highest priority
 --from-literal=another-param=k8s
```

The exact we can do with Declarative approach through an manifest file.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
   name: abiconfig
   namespace: default
data:
 another-param: k8s
 extra-param: prod
 my-config.txt: |
 # This is a sample config file that I might use to configure an application
    parameter1 = value1
    parameter2 = value2
```

commands for ConfigMap:

```yaml
kubectl get configmaps
kubectl describe configmaps
```

```yaml
apiVersion: v1 # String 
kind: Pod # String 
metadata: # Dictionary 
  name: myapp1-pod 
  labels: # Dictionary 
    app: myapp1 # Key value pairs 
spec: 
  containers: # List 
    - name: myapp1 
      image: myimage/kubenginx 
      ports: 
        - containerPort: 80
      env:
        - name: ANOTHER_PARAM
          valueFrom:
             configMapKeyRef:
               name: abiconfig
               key: another-param
        - name: EXTRA_PARAM
          valueFrom:
            configMapKeyRef:
              name: abiconfig
              key: extra-param
```

## Kubernetes secrets

A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key. Secrets are similar to ConfigMaps but are specifically intended to hold confidential data. Secrets hold one or more data elements as a collection of key/value pairs. By default, Kubernetes secrets are stored in plain text in the etcd storage for the cluster. anyone who has cluster administration rights in your cluster will be able to read all of the secrets in the cluster.

### key notes

In order to safely use Secrets, take at least the following steps:

1. Enable Encryption at Rest for Secrets.
    
2. Enable or configure RBAC rules with least-privilege access to Secrets.
    
3. Restrict Secret access to specific containers.
    
4. Consider using external Secret store providers.