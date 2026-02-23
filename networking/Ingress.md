# Ingress

## General Notes
- abstraction to handle inbound network traffic, url routing, application load balancing, and TLS, using k8s primitives
- consists of 2 main parts: `Ingress Controller` and `Ingress Resources`
- a k8s cluster does not come wth in Ingress Controller by default

<br>

## YAML Template

### Ingress Controller:
#### Deployment:
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-ingress-controller
spec:
  replicas: 1
  selector:
    matchLabels:
      name: nginx-ingress
  template:
    metadata:
      labels:
        name: nginx-ingress
    spec:
    - containers:
      - name: nginx-ingress-controller
        image: quay/io/kubernetes-ingress-controller/nginx-ingress-controller:0.21.0
        args:
          - /nginx-ingress-controller
          - --configmap=$(POD_NAMESAPCE)/nginx-configuration
        env:
          - name: POD_NAME
            valueFrom:
              fieldRef:
                fieldPath: metadata.name
          - name: POD_NAMESAPCE
            valueFrom:
              fieldRef:
                fieldPath: metadata.namespace
        ports:
          - name: http
            containerPort: 80
          - name: https
            containerPort: 443
```

#### ConfigMap:
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: nginx-configuration
```
*note: a `ConfigMap` can be used initially to abstract configuration data from the Controller (nginx in this case) to make is easier to change configuration settings. A blank one can be used for an initial setup*

#### Service:
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-ingress
spec:
  type: NodePort
  ports:
  - port: 80
    targetPort: 80
    protocol: TCP
    name: http
  - port: 443
    targetPort: 443
    protocol: TCP
    name: https
selector:
  name: nginx-ingress
```

#### ServiceAccount:
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: nginx-ingress-serviceaccount
...
```
*note: must be coinfigured with the necessary `Roles`, `ClusterRoles`, and `RoleBindings` in order to enable the Ingress Controllers additional intelligence to monitor the k8s cluster for ingress resources*

<br>

### Ingress Resources:
```yaml
apiVersion: v1
kind: Ingress
metadata:
  name: ingress-name
spec:
  defaultBackend:
    service:
      name: backend-app-service-name
      port: 80
  rules:
  - http:
      paths:
      - path: /path-name-1
        pathType: Prefix
        backend:
          service:
            name: backend-app-service-name
            port: 80
  - host: "host.name.app.com"
    http:
      paths:
      - path: /path-name-2
        pathType: Prefix
        backend:
          service:
            name: backend-app-service-name
            port: 80
```

<br>


## Commands

### create Ingress Resource
```
kubectl create -f ingress-name
```

### get Ingress Resource
```
kubectl get ingress
```
<br>