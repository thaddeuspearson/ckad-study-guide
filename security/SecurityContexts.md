# Security Contexts

## General Notes
- can be set at pod level or container level
- if set at the pod level, security contexts are carried over to all containers in the pod
- if set at the container level, pod security contexts are overwritten

<br>

## YAML Template
### Pod Level Security Context:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  securityContext:
    runAsUser: 1000
  containers:
    - name: ubuntu
      image: ubuntu
```

### Container Level Security Context:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
    - name: ubuntu
      image: ubuntu
      securityContext:
        runAsUser: 1000
        capabilities:
            ["MAC_ADMIN"]
```
*note*: capabilites are only available at the container level
<br>

## Commands

<br>