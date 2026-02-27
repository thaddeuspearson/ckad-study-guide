# PersistentVolumeClaim

## General Notes
- k8s object that allows a Pod to use a persistent volume
- each PVC is bound to a single PV
- labels and selectors can be used to bind to specific PVs
- claims and volumes have a 1-to-1 relationship
- a claim without an available PV will remain in a `pending` state
<br>

## YAML Template

### PVC Definition
```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: claim-name
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 500Mi
```

### Mounting PVCto a Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
    - name: container-name
      image: nginx
      volumeMounts:
      - mountPath: "/var/www/html"
        name: volume-name
  volumes:
    - name: volume-name
      persistentVolumeClaim:
        claimName: myclaim
```

<br>

## Commands

### create PVC
```
kubectl create -f pvc-definition.yaml
```

### get PVC
```
kubectl get persistencVolumeClaim
```

### delete PVC
```
kuvectl delete persistentVolumeClaim claim-name
```
*note:* set `persistentVolumeClaimPolicy` on the PV in order to Retain, Delete, or Recycle _(Depricated)_ a PV upon PVC deletion
<br>