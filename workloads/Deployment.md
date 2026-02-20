# Deployments

## General Notes
- provides the capability to upgrade the underlying instances seemlessly
- Deployments automatically create a ReplicaSet

### Rolling Updates and Rollbacks
- enables update and undo functionality
- `Rolling Update` - creates a new ReplicaSet and gradually spins up the new pod version while simultaneously spinning down the old pod version in the existing ReplicaSet. This is the default
- `Recreate` - spins down all old pods in the existing ReplicaSet, and spins up new pods in the new ReplicaSet

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

### update a Deployment:
```
kubectl apply -f <deployment-definition.yaml>
```

### status / history of Deployments:
```
kubectl rollout status deployment <deployment-name>

kubectl rollout history deployment <deployment-name>
```

### scale a Deployment
```
kubectl scale deployment --replicas=<desired> <deployment-name>
```
<br>