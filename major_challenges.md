## CICD
## AWS
## Terraform
## Ansible
## Jenkins
## Docker
## Kubernetes


Here’s how to answer the specific interview questions effectively:

1. ##Challenges Faced When an Application Failed in a K8s Cluster:
Response: "When an application failed in a Kubernetes cluster, I first checked logs and used kubectl describe to diagnose the issue, whether it was resource-related or due to configuration errors. I verified network connectivity and service endpoints. If needed, I rolled back to a stable version to minimize downtime while investigating the root cause."
2. ##Handling a Performance Issue in a Recent Deployment:
Response: "For a performance issue after a recent deployment, I would first consider rolling back if the impact was severe. I’d then monitor system metrics and logs to identify the bottleneck. I would compare the new deployment with the previous one, check resource configurations, and review recent code changes. After identifying the root cause, I’d implement the fix and redeploy, followed by close monitoring to ensure stability."
3. ##Performance Issue with the Recent Deployment
   – How to Tackle It:
Response: "If a recent deployment causes performance issues, my approach is to first roll back to mitigate impact. I’d analyze logs and metrics to identify any resource or configuration problems, review the code changes for inefficiencies, and then implement necessary optimizations. I’d redeploy the fixed version and continuously monitor performance to ensure the issue is resolved."

## When a Helm deployment fails, follow these steps to troubleshoot:

Check Release Status: Use helm status <release_name> to see the current state of the release.
Inspect Logs: Review logs with kubectl logs <pod_name> and Helm's output with helm get all <release_name>.
Review Events: Look at Kubernetes events using kubectl get events --namespace <namespace>.
Describe Pods: Get detailed information on the failing pods with kubectl describe pod <pod_name>.
Validate Chart: Run helm lint <chart_path> to check for chart errors.
Rollback if Needed: Revert to a previous version with helm rollback <release_name> <revision_number>.
These steps should help you identify and resolve the issue with the Helm deployment.

## Git/Github

