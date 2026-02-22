# NetworkPolicy

## General Notes
- K8s object that allows rules to be placed on ingress and egress traffic to associated pods
- connect `NetworkPolicy` objects to Pods with labels and selectors
- NetworkPolicy traffic is stateful _(i.e. the response to allowed ingress/egress traffic is also allowed and does not require an additional NetworkPolicy object)_

<br>

## YAML Template
```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: <policy-name>
spec:
  policyTypes:
  - Ingress
  - Egress
  ingress:
  - from:
    - podSelector:
        matchLabels:
          name: <pod-label>
      namespaceSelector:
        matchLabels:
          kubernetes.io/metadata.name: <namespace-label>
    - ipBlock:
        cidr: <desired-cidr-block>
    ports:
    - protocol: <desired-protocol-to-allow>
      port: <desired-port-to-allow>
  egress:
  - to:
      - ipBlock: 
           cidr: <desired-cidr-block>
      ports:
      - protocol: <desired-protocol-to-allow>
        port: <desired-port-to-allow> 
```
*note:* each entry to the from clause is its own policy, wo if there are multiple policies in the same ingress/egress policy, it is an OR operation. If multiple policies are under the same ingress/egress policy, it is an AND operation
<br>

## Commands

### create NetworkPolicy:
```
kubectl create -f <network-policy-definition.yaml>
```
<br>