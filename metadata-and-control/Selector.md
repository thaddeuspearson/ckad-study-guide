# Selector

## General Notes

- used to specify the nodes on which a pod may run
- leverages node labels _(key:value pairs)_ in order to in order to associate valid node/pod pairings
- used in simple cases _(no boolean logic, use affinity for this instead)_
<br>

## YAML Template

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
  - image: container-image
    name: container-name
  nodeSelector:
    size: Large
```
*note: requires labels to have already been set on the corresponding node*

<br>

## Commands

<br>