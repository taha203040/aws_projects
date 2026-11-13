<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Launch a Kubernetes Cluster

**Project Link:** [View Project](https://nextwork.ai/projects/aa8525df-82a0-5697-8721-a03b2db2c635)

**Author:** Rabia Taha

---

## Introducing Today's Project!

In this project, I will launch a Kubernetes cluster using Amazon Elastic Kubernetes Service (EKS).

### ✍️ Don't forget to delete your resources!

Amazon EKS is not covered by the AWS Free Tier. AWS charges $0.10 per hour for each running EKS cluster, regardless of the underlying compute costs. To avoid unnecessary charges, I will delete all associated AWS resources today.

### ✍️ What are we doing in this step and why?

In this step, I will provision a Kubernetes cluster using Amazon EKS to deploy, manage, and scale containerized applications. This will help me understand how Kubernetes integrates with AWS infrastructure and how to operate a managed Kubernetes environment.

### ✍️ How would you improve your security group settings?

I kept the default security group for my development instance because I wanted to avoid unnecessary configuration complexity at this stage. However, in future projects, I will strengthen its security by defining more restrictive inbound and outbound rules, following the principle of least privilege to control and limit network access.

### ✍️ What are we doing in this step and why?

In this step, I will Lunch the EKS cluster and we implement some error fixes in order to complete lunch it correctly

## What is Kubernetes?

Kubernetes is an open-source container orchestration platform. Companies and developers use Kubernetes to automate the deployment, scaling, and management of containerized applications across clusters of machines, improving application availability, scalability, and resource utilization.

I used \`eksctl\` to create an Amazon EKS cluster. The create cluster command I ran defined the cluster name (\`nextwork-eks-cluster\`), the managed node group name (\`nextwork-nodegroup\`), the EC2 instance type (\`t3.micro\`), and the desired number of worker nodes (3), with a minimum of 1 and a maximum of 3 nodes. I also specified Kubernetes version \`1.33\` and the AWS region \`eu-north-1\` (Stockholm).

I initially ran into two errors while using \`eksctl\`. The first one was caused by \`eksctl\` not being installed or properly configured in my EC2 instance. The second one was related to insufficient IAM permissions, as the EC2 instance's IAM role did not have the necessary policies to create and manage EKS resources. I resolved these issues by installing and configuring \`eksctl\` and updating the IAM role with the required permissions.

### ✍️ What are we doing in this step and why?

In this step, I will use AWS CloudFormation to monitor the creation of my EKS cluster because \`eksctl\` uses CloudFormation stacks to provision and manage the underlying AWS resources. This will help me track the deployment progress, inspect resource creation events, and troubleshoot any errors that occur during the process.

![What is Kubernetes?](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aa8525df-82a0-5697-8721-a03b2db2c635_ff9bfc221)

### ✍️ What are we doing in this step and why?

In this step, I will configure an IAM role for my EC2 instance and use \`eksctl\` to create an Amazon EKS cluster. This will allow the EC2 instance to interact with AWS services securely and provide a Kubernetes environment for deploying and managing containerized applications. I will also troubleshoot any errors encountered during cluster creation to better understand the EKS setup process.

### ✍️ What error do you think you'll see next?

In this step, I will troubleshoot the IAM permission error by reviewing and configuring the IAM role attached to my EC2 instance. The goal is to grant it the necessary permissions to create and manage an EKS cluster using \`eksctl\`, while following the principle of least privilege.

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because \`eksctl\` uses it to provision and manage the AWS resources required by the cluster. It also allowed me to monitor the creation process and track the status of each resource.

It created VPC resources because Kubernetes clusters require a properly configured network environment for communication between the control plane, worker nodes, and other AWS resources. Although I could use the default VPC, \`eksctl\` creates a dedicated VPC with the necessary networking components and configurations, providing a clean and isolated environment for the cluster.

There was also a second CloudFormation stack specifically for the \*\*node group\*\*, which manages the EC2 worker instances that run my containerized applications.

The difference between a cluster and a node group is that the \*\*EKS cluster\*\* provides the Kubernetes control plane responsible for managing and orchestrating workloads, while the \*\*node group\*\* provides the worker nodes where containers actually run.

CloudFormation separates these two stacks to make resource management and troubleshooting easier, allowing the cluster infrastructure and worker nodes to be managed independently.

### ✍️ What are we doing in this step and why?

In this step, I will configure the necessary IAM permissions to access and interact with my EKS cluster because AWS requires authorized IAM identities to manage cluster resources and perform Kubernetes operations securely.

![eksctl and CloudFormation](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aa8525df-82a0-5697-8721-a03b2db2c635_w3e4r5t6)

## The EKS console

I created an IAM access entry to gain permission to see and control the nodes inside my EKS cluster, since AWS \`AdministratorAccess\` doesn't automatically carry over to Kubernetes, which manages access through its own RBAC system; an IAM access entry acts as a handshake connecting AWS IAM with Kubernetes RBAC by mapping my IAM role to an RBAC role. I opened the EKS console, selected my \`nextwork-eks-cluster\`, and clicked \*\*Create access entry\*\* (from the blue banner or via the \*\*Access\*\* tab → \*\*IAM access entries\*\*), then selected my IAM user's ARN under \*\*IAM Principal\*\*, kept the \*\*Type\*\* as \*\*Standard\*\* since I'm adding a human, chose the \*\*AmazonEKSClusterAdminPolicy\*\* for full administrative rights over the cluster and all nodes, left \*\*Access scope\*\* as \*\*Cluster\*\*, clicked \*\*Add policy\*\*, reviewed the details, and clicked \*\*Create\*\*. The blue banner had warned that a node group existed but I might lack permission to see the nodes inside—reinforcing the key lesson that AWS permissions and Kubernetes permissions are separate and you need both to fully access a cluster.

It took \*\*about 10–15 minutes\*\* to create my cluster. Since I'll create this cluster again in the next project of this series, maybe this process could be sped up if I \*\*saved a reusable configuration\*\*—for example, by using an \*\*EKS cluster creation template\*\* (such as \`eksctl\` config files, Terraform, or CloudFormation) so I don't have to manually repeat every setting, and by \*\*pre-creating the IAM roles and node group configuration\*\* ahead of time so the cluster spins up faster and consistently.

![The EKS console](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aa8525df-82a0-5697-8721-a03b2db2c635_e5f6g7h8)
