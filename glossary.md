# Glossary

<br>

<details>
  <summary><u><b>API Server</b></u>: <i>the front door of the cluster</i></summary>
    
    the control plane component that exposes the Kubernetes API, validates and processes requests, and serves the authoritative cluster state to all components.
</details>

<br>

<details>
  <summary><u><b>Cluster</b></u>: <i>desired state + control plane + nodes</i></summary>
  
    a group of nodes, managed by control plane components, where a desired state is maintained and workloads are run.
</details>

<br>

<details>
  <summary><u><b>ConfigMap</b></u>: <i>non-secret application configuration</i></summary>
    
    a resource used to store and inject configuration data into Pods as environment variables or files.
</details>

<br>

<details>
  <summary><u><b>Control Plane</b></u>: <i>the brains of the cluster</i></summary>
  
    runs the API server, scheduler, controller manager, etcd. These components maintain cluster state, schedule workloads, and ensure cluster resources match the desired state.
</details>

<br>

<details>
  <summary><u><b>Control Plane Node</b></u>: <i>runs control plane components that decide what should happen</i></summary>
  
    a configured Node responsible for observing and maintaining the desired state of the resources of a cluster.
</details>

<br>

<details>
  <summary><u><b>Controller Manager</b></u>: <i>keeps desired state and actual state aligned</i></summary>
    
    the control plane component that runs controllers which continuously reconcile cluster resources to match their declared desired state.
</details>

<br>

<details>
  <summary><u><b>Deployment</b></u>: <i>manages pod rollouts</i></summary>
    
    a higher-level controller that manages ReplicaSets and provides declarative updates, scaling, and rollback of application versions.
</details>

<br>

<details>
  <summary><u><b>ETCD</b></u>: <i>source of truth for the cluster</i></summary>
    
    a distributed key-value store that persistently stores all cluster state and configuration for the Kubernetes control plane.
</details>

<br>

<details>
  <summary><u><b>Ingress</b></u>: <i>HTTP entry point to the cluster</i></summary>
    
    aresource that defines HTTP and HTTPS routing rules to expose Services outside the cluster.
</details>

<br>

<details>
  <summary><u><b>Job</b></u>: <i>executes one-off tasks</i></summary>
    
    a controller that creates and manages Pods to reliably execute a task, retrying failures until the specified completion criteria are met.
</details>

<br>

<details>
  <summary><u><b>Kubelet</b></u>: <i>local node agent that runs / monitors pods</i></summary>
    
    a per-node agent that runs and monitors assigned Pods, reconciling their state with PodSpecs received via streams from the API server.
</details>

<br>

<details>
  <summary><u><b>Namespace</b></u>: <i>the logical boundary for cluster resources</i></summary>
    
    a Kubernetes resource that provides a scope for names, access control, and resource isolation within a cluster.
</details>

<br>

<details>
  <summary><u><b>Node</b></u>:<i> a physical or virtual machine registered with the cluster</i></summary>
  
    a Node is a physical or virtual machine registered with a Kubernetes cluster that runs the kubelet, container runtime (if the node runs pods) and other node components.
</details>

<br>

<details>
  <summary><u><b>PersistentVolume</b></u>: <i>cluster storage resource</i></summary>
    
    a allotment of storage provisioned for the cluster and managed independently of Pod lifecycles.
</details>

<br>

<details>
  <summary><u><b>Pod</b></u>: <i>the atomic unit Kubernetes schedules</i></summary>
    
    the smallest deployable unit in Kubernetes, consisting of one or more containers that share networking, storage, and a lifecycle.
</details>

<br>

<details>
  <summary><u><b>ReplicaSet</b></u>: <i>maintains pod count</i></summary>
    
    a controller that ensures a specified number of identical Pods are running at all times, creating or deleting Pods to match the desired replica count.
</details>

<br>

<details>
  <summary><u><b>Scheduler</b></u>: <i>decides where pods run in the cluster</i></summary>
    
    the control plane component that assigns newly created Pods to Nodes based on resource availability, constraints, and scheduling policies.
</details>

<br>

<details>
  <summary><u><b>Secret</b></u>: <i>sensitive configuration data</i></summary>
    
    a resource used to store and provide sensitive data such as passwords, tokens, and keys to Pods.
</details>

<br>

<details>
  <summary><u><b>Service</b></u>: <i>stable access to a set of pods</i></summary>
    
    a Kubernetes abstraction that provides a stable virtual IP and DNS name to access a dynamic set of Pods.
</details>

<br>

<details>
  <summary><u><b>Volume</b></u>: <i>pod-level storage</i></summary>
    
    a directory mounted into a Pod that provides storage shared by its containers.
</details>

<br>

<details>
  <summary><u><b>Worker Node</b></u>: <i>executes what the control plane decides</i></summary>
  
    a node that runs the kubelet, the container runtime, and is responsible for running application Pods which have been scheduled by the control plane.
</details>

