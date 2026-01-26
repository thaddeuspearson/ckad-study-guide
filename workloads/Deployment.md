# Deployments

## General Notes
- provides the capability to upgrade the underlying instances seemlessly
- Deployments automatically create a ReplicaSetla

<br>

## YAML Template
### deployment-definition.yaml
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
    name: replicaset-name
    labels:
        app: app-name
        key: value
spec:
    template:
        metadata:
            name: pod-name
            labels:
                app: app-name
                key: value
        spec:
            containers:
                - name: container-name
                  image: container-image
    replicas: 3
    selector:
      matchLabels:
        key: value

```

<br>

## Commands

### create a Deployment from YAML:
```
kubectl create -f <deployment-definition.yaml>
```

### create a Deployment
```
kubectl create <deployment-name> --image=<image-name> --replicas=<num-of-replicas>
```
### get Deployments:
```
kubectl get deployments
```
<br>