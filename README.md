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