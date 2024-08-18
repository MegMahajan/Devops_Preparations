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
