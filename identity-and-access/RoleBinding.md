# RoleBinding

## General Notes
- the tying object that binds an RBAC role to a user/entity

<br>

## YAML Template

```yaml
apiVersion: rbac.autorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: binding-name
subjects:
- kind: User
  name: user-name
  apiGroup: rbac.authorization.k9s.io
roleRef:
  kind: Role
  name: developer
  apiGroup: rbac.authorization.k8s.io
```
*note:* rolebindings are namespace-scoped

<br>

## Commands

### get rolebindings
```
kubectl get rolebindings
```

### describe rolebindings
```
kubectl describe rolebinding <rolebinding>
```

<br>