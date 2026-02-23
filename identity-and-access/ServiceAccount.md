# SServiceAccount

## General Notes
- service accounts are used by machines, user accounts are used by humans
- upon service account creation, a token is generated automatically _(stored as a secret object)_, and linked to the associated service account
- Service Account tokens can be mounted as a volume within a pod
- a default service account is created for every namespace, and associated token is automatically mounted as a volume to any associated pod created _(this can be disabled)_
- as of v1.24, projected tokens are used instead:
    - short-lived
    - still mounted at `/var/run/secrets/kubernetes.io/serviceaccount/token`
    - no longer stored in etcd

<br>

## YAML Template

<br>

## Commands

### Create Service Account
```
kubectl create serviceaccount <service-account-name>
```

### View Service Account
```
kubectl get serviceaccount
kubectl describe serviceaccount <service-account-name>
```

### Create Token (via `TokenRequestAPI`)
```
kubectl create token
```
<br>