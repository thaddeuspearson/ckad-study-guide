# PersistentVolume

## General Notes
- A cluster-wide pool of storage
- backing storage can be created on the host, or a distributed storage solution (ex: AWS EBS)
- Pods make Persistent Volume Claims (PVC) on a PV
- accessModes
    - ReadOnlyMany
    - ReadWriteOnce
    - ReadWriteMany
<br>

## YAML Template

```yaml
apiVersion: v1
kind: PersistentVolume
metadata: 
  name: pv-vol1
spec:
  accessModes:
  - ReadWriteOnce
  capacity:
    storage: 1Gi
  hostPath:
    path: <path-to-storage-on-host>
```

*note*: AWS EBS example _(replaces hostPath above)_
```yaml
  awsElasticBlockStore:
    volumeID: <volume-id>
    fsType: ext4
```
<br>

## Commands

### Create PV
```
kubectl create -f pv-definition.yaml
```

### Get PV
```
kubectl get persistentvolume
```
<br>