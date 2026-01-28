# Service

## General Notes
- Helps connect applications together with other applications or users
- enable loose coupling between microservices
- Many types of services:
    - `NodePort`
        - makes an internal port accessible on a port on the Node
        - 3 ports:
            1. Target Port: port on the Pod
            2. Port: port on the Service
            3. nodePort: port on the Node (30000 - 32767)
        - use `selector` property to specify what pods to associate with the service. This automatically loadbalances across multiple instances of the same pod
        - if pods are distributed across Nodes, NodePort Service spans across all Nodes in the cluster, and maps the targetPort on each pod to the desired nodePort on the associated Node
        ```yaml
        apiVersion: v1
        kind: Service
        metadata:
            name: <app-name>-service
        spec:
            type: NodePort
            ports:
                - targetPort: 80
                  port: 80
                  nodePort: 30008
            selector:
                  desired-label: <desired-pod-label>
        ```
    - `ClusterIP` (default type)
        - a virtual IP inside the cluster to enable communication between different services _(ex: front-end <> backend <> database)_
        - each ClusterIP gets a name and and IP which should be used by the pods
        ```yaml
        apiVersion: v1
        kind: Service
        metadata:
            name: <servicename>
        spec:
            type: ClusterIP
            ports:
                - targetPort: <desired-targetPort>
                  port: <desired-service-port>
            selector:
                desired-label: <desired-pod-label>
        ```
    - `LoadBalancer`
        - distrubutes loads across pods

<br>

## Commands
### get services
```
kubectl get services
```

### describe service
```
kubectl describe service <service>
```

### create a service
```
kubectl create -f service-definition.yaml
```
<br>
