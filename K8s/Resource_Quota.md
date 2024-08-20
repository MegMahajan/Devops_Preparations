
Resource Quotas in Kubernetes
Resource Quotas are a mechanism in Kubernetes that allows administrators to control resource usage at the namespace level. They help ensure that resources such as CPU, memory, storage, and object counts (like the number of pods or services) are allocated fairly among different teams or applications within a cluster, preventing any single namespace from consuming more than its share of resources.

Key Concepts:
Namespace Scope:

Resource Quotas are applied per namespace. Each namespace can have its own Resource Quota configuration, limiting the resources that can be consumed by the workloads running within that namespace.
Types of Resources Managed:

Compute Resources: CPU and memory usage.
Storage Resources: Limits on persistent volume claims (PVCs).
Object Counts: Maximum number of objects like pods, services, configmaps, persistent volume claims, etc.
Quota Specifications:

Resource Quotas are defined in a ResourceQuota object, which includes specifications for hard limits (maximum) on various resource types.
Example configuration:
yaml
Copy code
apiVersion: v1
kind: ResourceQuota
metadata:
  name: example-quota
  namespace: example-namespace
spec:
  hard:
    pods: "10"
    requests.cpu: "4"
    requests.memory: "8Gi"
    limits.cpu: "10"
    limits.memory: "16Gi"
In this example, the namespace example-namespace can have a maximum of 10 pods, with a total CPU request of 4 cores, memory request of 8GiB, and limits on CPU and memory usage.
Quota Enforcement:

Kubernetes enforces Resource Quotas during the creation or update of resources in a namespace. If the requested resources exceed the quota, the operation is denied, ensuring that the total usage stays within the defined limits.
Requests and Limits:

Requests: The minimum amount of resource that a container is guaranteed.
Limits: The maximum amount of resource that a container can consume.
Resource Quotas can set maximums on both requests and limits for CPU and memory, controlling how much a namespace can use overall.
Usage Tracking:

Kubernetes automatically tracks the resource usage within each namespace and compares it to the Resource Quota. This tracking ensures that resources are allocated fairly and prevents any namespace from exceeding its allotted resources.
Impact of Exceeding Quota:

If a namespace reaches its quota for a specific resource, further creation or expansion of resources that require that particular resource will be blocked until usage falls below the quota.
Use Cases:
Multi-Tenancy:

In multi-tenant environments, where multiple teams or applications share the same Kubernetes cluster, Resource Quotas ensure that each team gets its fair share of resources, preventing resource contention.
Cost Management:

Resource Quotas help control costs by limiting the maximum resources that can be consumed, ensuring that teams don't accidentally or intentionally use more than their allocated resources.
Resource Planning:

Administrators can use Resource Quotas to plan and allocate resources across different teams, ensuring that critical applications have the resources they need without being affected by other workloads.
Summary:
Resource Quotas are an essential feature in Kubernetes for managing and controlling resource usage at the namespace level. By setting limits on the amount of CPU, memory, storage, and the number of objects that can be used, Resource Quotas help ensure fair distribution of resources across different namespaces, support multi-tenancy, and enable effective resource management and cost control.

In Kubernetes, requests and limits define the resource allocation for containers in a pod, particularly for CPU and memory.

1. Requests:
Request is the minimum amount of CPU or memory that a container is guaranteed to get.
If a node has enough resources available, the scheduler will place the pod on that node.
If resources are tight, the scheduler uses the requests to prioritize pods based on the requested resources.
CPU request is measured in cores (or millicores), while memory request is measured in bytes (e.g., MiB, GiB).
2. Limits:
Limit is the maximum amount of CPU or memory that a container is allowed to use.
If a container tries to exceed its CPU limit, it may be throttled (i.e., slowed down).
If a container exceeds its memory limit, it will be killed by the system (OOMKilled), but it may be restarted if the pod's restart policy allows it.
Example:
yaml
Copy code
resources:
  requests:
    memory: "256Mi"
    cpu: "500m"
  limits:
    memory: "512Mi"
    cpu: "1"
In this case, the container requests 256MiB of memory and 500m (0.5 cores) of CPU.
It will not consume more than 512MiB of memory or 1 full CPU core, as these are the set limits.



Key Points:
Requests are used for scheduling decisions.
Limits control the maximum usage to prevent overconsumption of resources.


Req->Min
Limit->Max
