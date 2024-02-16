---
title: "RBAC in Kubernetes"
datePublished: Fri Feb 16 2024 19:55:41 GMT+0000 (Coordinated Universal Time)
cuid: clsp2kxsn00010ajm87jagcmn
slug: rbac-in-kubernetes
tags: rbac, kubernetes-role, kubernetes-rolebindings

---

RBAC stands for **Role Based Access Control**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708112132360/1b92f66c-07cb-440c-a002-4782f62f5f0f.png align="center")

Role: A role can be used to grant access to resources in a namespace

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: developer
  namespace: dev
rules:
- apiGroups: ["","Extensions", "apps"]  # "" indicates the core API group
  resources: ["*"]
  verbs: ["get", "list", "create", "delete", "watch"]
- apiGroups: ["batch"]
  resources:
  - job
  - cronjobs
  verbs: ["*"]
```

RoleBinding: A RoleBinding binds subjects\[users, groups\] with the roles.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metedata:
  name: dev-user-rolebinding
  namespace: dev
subjects: 
  kind: user
  name: dev
  apiGroup: rbac.authorization.k8s.io/v1
roleRef:
  kind: role
  name: developer
  apiGroup: rbac.authorization.k8s.io/v1
```

imperative command to create Roles and RoleBindings

```bash
kubectl create role developer --namespace=default --verb=list,create,delete --resource=pods
kubectl create rolebinding dev-user-binding --namespace=default --role=developer --user=dev-user

kubectl auth can-i list nodes --as dev # to check access 
```