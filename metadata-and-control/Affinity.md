# Affinity

## General Notes

- ensure that pods are hosted on particular nodes
- enables advanced expressions _(In, NotIn...)_
- Node Affinity Types:
    - requiredDuringSchedulingIgnoredDuringExecution
    - preferredDuringSchedulingIgnoredDuringExecution
    - requiredDuringSchedulingRequiredDuringExecution
<br>

## YAML Template

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
  - name: container-name
    image: container-image
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: size
            operator: In
            values:
            - Large
```
<br>

## Commands

<br>