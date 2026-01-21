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

## Commands

run a pod
```
kubectl run pod --image image-name
```
retrieve pods
```
kubectl get pods
```