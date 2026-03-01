# CLusterRoleBinding

## General Notes
- cluster-scoped role bindings for RBAC

<br>

## YAML Template

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: CluserRoleBinding
metadata:
  name: cluster-admin-role-binding
subjects:
- kind: User
  name: username
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: role-name
  apiGroup: rbac.authorization.k8s.io
```
<br>

## Commands

### create ClusterRoleBinding
```
kubectl create -f cluster-role-binding-name.yaml
```
<br>