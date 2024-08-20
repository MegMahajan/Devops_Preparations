In Kubernetes, an Admission Controller is a critical component that intercepts requests to the Kubernetes API server before any object is persisted. It is responsible for validating, mutating, or even rejecting requests based on custom rules or policies. Admission controllers help enforce policies, enhance security, and ensure that the Kubernetes environment is consistent and compliant with organizational or operational requirements.

How Admission Controllers Work:
Intercepting API Requests:

When a request is made to create, update, or delete a Kubernetes resource (like Pods, Services, or ConfigMaps), the request first goes through various stages within the API server.
After authentication and authorization, but before the object is persisted in etcd (Kubernetes' data store), the request is sent to the admission controllers.
Types of Admission Controllers:

Validating Admission Controllers: These controllers check if the resource meets certain criteria. For example, they can validate that a container image comes from a trusted registry or ensure that resource limits are set on pods.
Mutating Admission Controllers: These controllers can modify the resource specifications before they are saved. For example, they might add default labels, inject sidecar containers, or enforce security policies.
Common Use Cases:

Pod Security Policies: Ensuring that all pods meet certain security standards.
Resource Quotas: Enforcing limits on resource usage within namespaces.
Network Policies: Automatically applying network policies to ensure proper network segmentation.
Default Configuration: Automatically adding default settings or labels to resources that are created without them.
Webhook Admission Controllers:

Kubernetes also supports Dynamic Admission Controllers through webhooks, which allow for more flexible and customizable policies.
MutatingAdmissionWebhook: Modifies the object in the admission phase.
ValidatingAdmissionWebhook: Validates the object and can reject it if it doesn't meet certain criteria.
These webhooks call an external HTTP service that applies custom logic to either approve, reject, or modify the requests.
Examples of Built-in Admission Controllers:

NamespaceLifecycle: Prevents deletion of system-critical namespaces.
LimitRanger: Ensures that resource limits are set and respected.
ServiceAccount: Automatically assigns service accounts to pods.
PodSecurityPolicy: Ensures pods comply with specified security policies.
Workflow Example:
When you create a pod in Kubernetes, the request goes through the following steps:

User submits a request to create a pod.
API Server authenticates the user and checks permissions (authorization).
Admission Controllers intercept the request:
Mutating Admission Controllers might add default values or inject sidecars.
Validating Admission Controllers might ensure that the pod adheres to security policies.
If the request passes the admission controllers, it is persisted in etcd.
The pod is then scheduled to run on a node.
Summary:
Admission controllers are essential for enforcing policies, automating configurations, and enhancing the security and stability of Kubernetes clusters. By intercepting API requests, they allow Kubernetes administrators to enforce rules and maintain consistency across the cluster.
