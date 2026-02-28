# Role

## General Notes
- the defining object in RBAC
<br>

## YAML Template

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: role-name
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["list", "get", "create", "update", "delete"]
- apiGroups: [""]
  resources: ["ConfigMap"]
  verbs: ["create"]
```
*note:* roles are namespace-scoped

<br>

## Commands

### get role
```
kubectl get role
```

### describe rolebindings
```
kubectl describe role <role>
```
<br>