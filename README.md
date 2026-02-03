# CKAD Study Guide

Study Guide to work through the CKAD study material found in the following course:

[Kubernetes Certified Application Developer (CKAD) with Tests](https://www.udemy.com/course/certified-kubernetes-application-developer/)

[Glossary](./glossary.md)


## Exam Tips

### Imperative Commands

`--dry-run=client` This will not create the resource but say if the command is correct and if the resource can be created

`-o yaml`: output the resource definition in YAML format on the screen

combine the two above with redirection to rapidly create templates:

```
kubectl create deployment redis --image=redis --dry-run=client -o yaml > redis-definition.yaml
```

### api-resources

use `kubectl api-resources` to retrieve a detailed list of kubernetes resources and applicable information:

```
NAME                        SHORTNAMES   APIVERSION          NAMESPACED   KIND
bindings                                 v1                  true         Binding
componentstatuses           cs           v1                  false        ComponentStatus
configmaps                  cm           v1                  true         ConfigMap
endpoints                   ep           v1                  true         Endpoints
events                      ev           v1                  true         Event
limitranges                 limits       v1                  true         LimitRange
namespaces                  ns           v1                  false        Namespace
...
```

### explain

use `kubectl explain <resource[.field]>` to list properties and subproperties of each field of the given resource. `kubectl explain <resource> --recursive` will output a list of all fields and subfields of the given resource:


ex: `kubectl explain pods.spec`
```
KIND:       Pod
VERSION:    v1

FIELD: spec <PodSpec>


DESCRIPTION:
    Specification of the desired behavior of the pod. More info:
    https://git.k8s.io/community/contributors/devel/sig-architecture/api-conventions.md#spec-and-status
    PodSpec is a description of a pod.
    
FIELDS:
  activeDeadlineSeconds <integer>
    Optional duration in seconds the pod may be active on the node relative to
    StartTime before the system will actively try to mark it failed and kill
    associated containers. Value must be a positive integer.
...
```

ex: `kubectl explain pods --recursive`
```
KIND:       Pod
VERSION:    v1

DESCRIPTION:
    Pod is a collection of containers that can run on a host. This resource is
    created by clients and scheduled onto hosts.
    
FIELDS:
  apiVersion    <string>
  kind  <string>
  metadata      <ObjectMeta>
    annotations <map[string]string>
    creationTimestamp   <string>
    deletionGracePeriodSeconds  <integer>
    deletionTimestamp   <string>
    finalizers  <[]string>
    generateName        <string>
    generation  <integer>
    labels      <map[string]string>
...
```

### Imperative Custom CMD args

use the `--command -- <arg1> <arg2> ... <argN>` to add custom CMD args

```
kubectl run example-pod --image=example-pod-image  -- example arg 
```

### Gotchas
CMD line args in Docker vs Kubernetes
| Docker Instruction | Kubenetes Field |
|---------------------|------------------|
|`ENTRYPOINT` | `command` |
|`CMD` | `args` |