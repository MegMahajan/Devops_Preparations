# Kubernetes_Concepts
My imp notes
Master Node and Worker Node: The Basics
Kubernetes operates on a master-worker node concept. These nodes can be either bare metal machines or Virtual Machines (VMs) on any cloud instance. Let's delve into the components and see how they interconnect.

The API Server: The Central Brain of Kubernetes
The API server is the central brain of Kubernetes, handling requests such as creating a pod. A user initiates this process by running `kubectl`, a command-line tool, followed by the pod name and the image. This request is then sent to the API server, where it undergoes three stages: authentication, authorization, and admission.

Kubelet: The Worker Node's Main Component
On the worker node side, the main component is kubelet. It continually communicates with the API server, asking if there's any workload to run. 
When the scheduler identifies a workload for a node, the API server informs kubelet, which then fetches images using the container runtime, 
such as Containerd or Docker. It then runs the pod with the defined configurations.

Kube-proxy: Managing Network Communication
Kube-proxy, another component in worker nodes, is the core network component of Kubernetes. It manages all networking and communication across the cluster, handling port-to-port communications and network rules.

Controller Manager: The Control Plane Component
The controller manager, a component in the master node, runs on the control plane. It is a set of controllers, such as the replication controller and DaemonSet controller, that manage the Kubernetes cluster and its state.

ETCD: The Key-Value Database
ETCD is a highly available key-value database for Kubernetes that stores all the information of all the resources and objects running in the cluster. The API server is responsible for storing all this information in ETCD.

In conclusion, the Kubernetes architecture is a complex yet efficient system. The API server, scheduler, controller manager, kubelet, Kube-proxy, and ETCD all play vital roles in ensuring the smooth operation of your Kubernetes cluster. Understanding these components and how they interact will help you better manage your workloads on Kubernetes.

