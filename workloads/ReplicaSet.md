# ReplicaSet

## General Notes
- ReplicaSet is the updated version of ReplicaController
- ReplicaSet YAMLs require a `selector` definition in the spec:
    - identifies what pods fall under the ReplicaSet
    - they can manage pods that are not created by the ReplicaSet, these pods would be taken into consideration when managing the replicas

<br>

## YAML Template

### replicaset-definition.yaml
```yaml
apiVersion: apps/v1
kind: ReplicaSet
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
      matchLabel:
        key: value

```

<br>

## Commands

### create a ReplicaSet from YAML:
```
kubectl create -f <replicaset-definition.yaml>
```
### get ReplicaSets:
```
kubectl get replicaset
```

### delete ReplicaSet:
```
kubectl delete replicaset <replicaset-name>
```

### output an existing ReplicaSet to YAML:
```
kubectl get replicaset <replicaset-name> -o yaml > replicaset-definition.yaml
```

### update a ReplicaSet with YAML:
```
kubectl apply -f replicset-definition.yaml
```

### directly scale a ReplicaSet:
```
kubectl scale --replicas=<desired-num-of-replicas> replicaset <replicaset-name>
```

<br>
