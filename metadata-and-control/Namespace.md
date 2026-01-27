# Namespaces

## General Notes
- namespaces automatically when kubernetes is first set up:
    - `default`
    - `kube-system`
    - `kube-public`
- primarilly used for isolation _ex: dev/prod_
- each namespace can have its own policies
- resource quotas can be assigned to each namespace
- connect to services within the same namespace with the resourcde name _ex: db-service_
- connect to services in other namespaces appending the namespace to the name _ex: db-service.dev.svc.cluster.local_

<br>

## YAML Template

### namespace-definition.yaml
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```
<br>

## Commands

### get resources in a specific namespace
```
kubectl get pods --namespace=dev
```

### set context for namespace
```
kubectl config set-context $(kubectl config current-context) --namespace=<desired-namespace>
```

### all namespaces
```
kubectl get pods --all-namespaces
```

### add namespace definition to resource YAML
```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  namespace: dev
  labels:
    app: myapp
spec:
  containers:
    - nginx-controller
      image: nginx
```

### namespace respource quotas
```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: compute-quota
  namespace: dev
spec:
  hard:
    pods: "10"
    requests.cpu: "4"
    requests.memory: 5Gi
    limits.cpu: "10"
    limits.memory: 10Gi
```

<br>