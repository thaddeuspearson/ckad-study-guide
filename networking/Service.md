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
            3. NodePort: port on the Node (30000 - 32767)
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
                - name: myapp
                  desired-label: <desired-pod-label>
        ```
    - `ClusterIP`
        a virtualIP inside the cluster to enable communication between different services _(ex: front-end <> backend)_
    - `LoadBalancer`
        - distrubutes loads across pods

<br>

## YAML Template

<br>

## Commands

<br>