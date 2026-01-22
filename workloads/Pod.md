# Pod

## General Notes
- single instance of an application
- smallest object that can be created in k8s
- usually have a 1-1 relationship to containers in an application
    - scale up -> add new pod
    - scale down -> delete existing pod
    - containers are not scaled within a pod
- multi-container pods
    - a pod can have multiple containers _(rare use case)_
    - usually not multiple containers of the same kind
    - helper containers _(processing data, file uploads etc)_
    - share the same network space (can use `localhost` to communicate) and storage space

<br>

## YAML Template

### pod-definition.yaml
```yaml
apiVersion: v1
kind: pod
metadata:
    name: pod-name
    labels:
        app: app-name
        key: value
spec:
    containers:
        - name: container-name
          image: image-name
```

<br>

## Commands

### run a pod:
```
kubectl run <pod-name> --image <image-name>
```

### create a YAML with dry-run:
```
kubectl run <pod-name> --image <image-name> --dry-run=client -o yaml
```

### create a pod from YAML:
```
kubectl create -f <pod-definition.yaml>
```
### get pods:
```
kubectl get pods
```

### describe a pod:
```
kubectl describe pod <pod-name>
```

### output an existing pod to YAML:
```
kubectl get pod <pod-name> -o yaml > pod-definition.yaml
```

<br>
