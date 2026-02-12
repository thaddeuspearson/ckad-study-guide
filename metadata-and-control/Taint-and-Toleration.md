# Taint and Toleration

## General Notes
- Taints are applied to Nodes _(the bugspray)_
- Toleration are applied to Pods _(the bugs)_
- a tainted node can only run Pods that have toleration for the taint applied
- taint-effects:
    - NoSchedule - (no new intolerant pods)
    - PreferNoSchedule
    - NoExecute - (no schedule + evict any existing intolerant pods)

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
  tolerations:
    - key: "key"
      operator: "Equal"
      value: "value"
      effect: "NoSchedule"
```
<br>

## Commands

### Create a Taint
```
kubectl taint nodes <node-name> key=value:taint-effect
```
*note:* taint-effect is what happend when a taint is not tolerated
<br>