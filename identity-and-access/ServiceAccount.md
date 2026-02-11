# SServiceAccount

## General Notes
- service accounts are used by machines, user accounts are used by humans
- upon service account creation, a token is generated automatically _(stored as a secret object)_, and linked to the associated service account
- Service Account tokens can be mounted as a volume within a pod
- a default service account is created for every namespace, and associated token is automatically mounted as a volume to any associated pod created_(this can be disabled)_

<br>

## YAML Template

<br>

## Commands

### Create
```
kubectl create srviceaccount <service-account-name>
```

### View
```
kubectl get serviceaccount
kubectl describe serviceaccount <service-account-name>
```
<br>