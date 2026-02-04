# Secrets

## General Notes
- secrets are stored as key/value pairs
- values are base64 encoded

<br>

## YAML Template
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
data:
  SECRET1: base64-encoded-secret1
  SECRET2: base64-encoded-secret2
```

<br>

## Commands
### Display secrets and data
```
kubectl get secrets
```
```
kubectl describe secrets
```

```
kubectl get secret <secret-name> -o yaml
```

### Imperative creation
```
kubectl create secret generic <secret-name> --from-literal=<key>=<value>
```
or
```
kubectl create secret generic <configmap-name> --from-file=<path-to-secret-file>
```

### Declarative creation
```
kubectl create -f secret.yaml
```

<br>