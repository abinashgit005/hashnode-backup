---
title: "ConfigMap and secrets in K8s"
datePublished: Sat Jan 20 2024 14:22:07 GMT+0000 (Coordinated Universal Time)
cuid: clrm5ryrl000109l641ts7di5
slug: configmap-and-secrets-in-k8s
tags: kubernetes-configmap

---

This article gives a brief idea on ConfigMap and secrets in K8s.

Config map is used to provide configuration data in the form of key value pairs.

**why we use config map ?**  
when we have a lot of pod definition file, it is difficult to manage the environment data stored in it. we can place this information out of pod definition file and manage it centrally with configuration map.

**abiconfig.txt**

```yaml
parameter1 = value1
parameter2 = value2
```

we can create config map in imperative approach by the below command

```yaml
 kubectl create configmap aviconfig \
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
 another-param: another-value
 extra-param: extra-value
 my-config.txt: |
 # This is a sample config file that I might use to configure an application
    parameter1 = value1
    parameter2 = value2
```

```yaml
kubectl get configmaps
kubectl describe configmaps
```

How can you use the ConfigMap ?