## Explan CICD pipeline flow in AWS
## How would you design a highly available and scalable architechture for the web application that is deployed on Ec2?
## How do you handle situation when user is saying application is Down? what will be your first step?
## Explain any complex project which u design?
## Explain your CICD flow you are working on?
## How do u manage zero downtime in your application.

To achieve zero downtime for your applications on AWS:

Blue/Green Deployment: Maintain two environments (Blue and Green) to switch traffic between the old and new versions.

Canary Releases: Gradually roll out the new version to a small subset of users before full deployment.

Rolling Updates: Incrementally update instances in your deployment group to ensure continuous availability.

Load Balancers: Use Elastic Load Balancers (ELB) to distribute traffic and ensure only healthy instances receive requests.

Auto Scaling: Automatically adjust the number of instances based on traffic and load.

Database Management: Use Multi-AZ deployments and read replicas for high availability and performance.

Monitoring and Alerting: Implement CloudWatch for monitoring and setting up alarms to detect and address issues proactively.

## How to do managing or optimize resource usage in k8s?
## How do you handle secrets in Harshi Crop?
## Which monitoring tool u have worked on?
## DO u know about VPA and HPA in K8s?
## Diff between SG & NACLS
## Diff between NAT & IGW 
## Diff between SES & SNS
## Route 53 Routing Policy
## Arcitect at the design using AWS service
## S3 storage classses
## Diff between s3 standard and Glacier
## Have u worked on AWSCODEPIPELINE? Please explain the Flow.
## How to do handle security in your CICD plan?
## How do you secure the sensitive info in aws?
## Have you worked on ACM?
## Types of Volumn in AWS 
## if i want to connect to my ec2 instance with s3 bucket which is there in another account , how we can do it ?

To access an S3 bucket in another AWS account from an EC2 instance:

1. Create an IAM Role in Account B (S3 bucket account) that grants the necessary S3 permissions.
2. Update the trust relationship in that role to allow Account A (EC2 instance account) to assume it.
3. Attach an IAM Role to the EC2 instance in Account A that allows the instance to assume the role in Account B.
4. Use AWS CLI on the EC2 instance to assume the role and access the S3 bucket.
5. This sets up secure cross-account access between the EC2 instance and the S3 bucket.

