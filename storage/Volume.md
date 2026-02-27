# Volume

## General Notes
- provides a method of persisting data from a Pod
- backing storage can be created on the host, or a distributed storage solution (ex: AWS EBS)
- the volume is directly mounted to the pod

<br>

## YAML Template

### Base Pod template
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: random-number-generator
spec:
  containers:
  - image: alpine
    name: alpine
    command: ["/bin/sh", "-c"]
    args: ["shuf -i 0-100 -n 1 >> /opt/number.out;"]
    volumeMounts:
    - mountPath: /opt
      name: data-volume
  volumes:
  - name: data-volume
  hostPath:
    path: /data
    type: Directory
```

<br>

## Commands

<br>