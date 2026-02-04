# ConfigMaps

## General Notes

- used to pass configuration data in the form of key/value pairs
- injected into a Pod when it is created so the key/value pairs are available as environment variables

<br>

## YAML Template
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  ENV_VAR1: value1
  ENV_VAR2: value2
```
<br>

## Commands

### Display configmaps and data
```
kubectl get configmaps
```

```
kubectl describe configmaps
```
### Imperative creation
```
kubectl create configmap <configmap-name> --from-literal=<key>=<value>
```
or
```
kubectl create configmap <configmap-name> --from-file=<path-to-configmap-file>
```

### Declarative creation
```
kubectl create -f config-map.yaml
```
<br>