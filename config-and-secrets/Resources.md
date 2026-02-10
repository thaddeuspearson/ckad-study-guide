# Resources _(Requests/Limits)_

## General Notes
- can set requests and limits for container resources
- by default, containers may consume unlimited resources from a node unless a limit is specified
- if a pod tries to exceed its limits:
    - cpu: throttle
    - memory: terminate _(OOM Error)_
- Default settings are no limits on cpu or memory
- if no requests are set, but limits are set, then requests default to the limit
- most common scenario is setting requests and no limits
- use `LimitRanges` to set pod/container limits per namespace
- use `ResourceQuotas` to set hard limits on cpu and memory at the namespace level in aggregate

<br>

## YAML Template

### Resource Request
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
    - name: container-name
      image: container-image
      ports:
        - containerPort: 8080
    resources:
      requests:
        memory: "1Gi"
        cpu: 1
```

### Resource Limit
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
    - name: container-name
      image: container-image
      ports:
        - containerPort: 8080
    resources:
      limits:
        memory: "2Gi"
        cpu: 2
```

### LimitRanges _(cpu)_
```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-resource-constraint
spec:
  limits:
    - default:
        cpu: 500m
      defaultRequest: 
        cpu: 500m
      max: 
        cpu: "1"
      min:
        cpu: 100m
      type: container
```

### LimitRanges _(memory)_
```yaml
apiVersion: v1
kind: LimitRange
metadata:
  name: cpu-resource-constraint
spec:
  limits:
    - default:
        memory: 1Gi
      defaultRequest: 
        memory: 1Gi
      max: 
        memory: 1Gi
      min:
        memory: 500Mi
      type: container
```
*note:* LimitRanges are enforeced at Pod creation

###  ResourceQuota
```yaml
apiVersion: v1
kind: ResourceQuota
metadata:
  name: ns-resource-quota
spec:
  hard:
    requests.cpu: 4
    requests.memory: 4Gi
    limits.cpu: 10
    limits.memory: 10Gi
```
*note:* ResourceQuotas are namespace-scoped
<br>


## Commands

<br>