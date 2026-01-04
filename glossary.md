# Glossary

<details>
  <summary><b>Cluster</b></summary>
  
    a group of nodes, managed by control plane components, where a desired state is maintained and workloads are run.
</details>

<details>
  <summary><b>Control Plane</b></summary>
  
    runs the API server, scheduler, controller manager, etcd. These components maintain cluster state, schedule workloads, and ensure cluster resources match the desired state.
</details>

<details>
  <summary><b>Control Plane Node</b></summary>
  
    a configured Node responsible for observing and maintaining the desired state of the resources of a cluster.
</details>

<details>
  <summary><b>Pod</b></summary>
  
   the smallest deployable unit in Kubernetes, consisting of one or more containers that share networking, storage, and a lifecycle.
</details>

<details>
  <summary><b>Node</b></summary>
  
    a Node is a physical or virtual machine registered with a Kubernetes cluster that runs the kubelet, container runtime (if the node runs pods) and other node components.
</details>

<details>
  <summary><b>Worker Node</b></summary>
  
    a node that runs the kubelet, the container runtime, and is responsible for running application Pods which have been scheduled by the control plane.
</details>

