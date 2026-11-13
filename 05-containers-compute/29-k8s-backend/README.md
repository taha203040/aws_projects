<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Deploy Backend with Kubernetes

**Project Link:** [View Project](https://nextwork.ai/projects/090a4709-f1f4-5d95-ae4d-b8199bf808ed)

**Author:** Rabia Taha

---

## Introducing Today's Project!

In this project, I will deploy a containerized Flask backend application to an Amazon EKS cluster using Kubernetes because I want to gain practical experience with container orchestration, workload management, and application deployment. I will also explore how Kubernetes manages Pods, Deployments, and Services to keep applications running and accessible.

### ✍️ Don't forget to delete your resources!

Amazon EKS is not AWS Free Tier eligible. AWS charges $0.10 for every hour my EKS cluster is running. To minimise costs, I will the resources once i complete the project

### ✍️ What are we doing in this step?

In this step, I will launch and connect to an EC2 instance, install and configure eksctl, and set up AWS credentials because I need a properly configured environment with the necessary permissions to provision and manage an Amazon EKS cluster. I will then use eksctl to create the Kubernetes cluster that will host my containerized application.

### Tools and concepts

I used Kubernetes, Amazon EKS, Amazon ECR, Docker, kubectl, and eksctl to deploy a containerized Flask backend application to a managed Kubernetes cluster.

Key concepts include using Kubernetes manifests to declaratively define Deployments and Services, managing application Pods and replicas, configuring container images from ECR, and exposing applications through Kubernetes Services

### Project reflection

This project took me approximately 45 minutes.

The most challenging part was creating and configuring the Kubernetes manifests, particularly understanding how labels, selectors, ports, and container image references work together.

My favourite part was applying the manifests with kubectl and seeing Kubernetes create and manage the application resources.

I chose to do this project today because I wanted to gain hands-on experience with Kubernetes and understand how Amazon EKS orchestrates containerized applications.

Something that would make learning with NextWork even better is including more real-world troubleshooting scenarios, especially around Kubernetes networking, IAM permissions, and workload scheduling, so learners can develop stronger independent debugging skills.

## Project Set Up

### Kubernetes cluster

To set up today's project, I launched a Kubernetes cluster using Amazon EKS. Steps I took to do this included launching and connecting to an EC2 instance, installing and configuring \`eksctl\`, setting up AWS credentials and permissions, and using \`eksctl\` to provision the EKS cluster and its required infrastructure.

### ✍️ What are we doing in this step?

In this step, I will install Git and clone the backend application's source code from GitHub because I need a local copy of the application to inspect its structure, understand its dependencies, and prepare it for containerization and deployment to my Amazon EKS cluster.

### Backend code

I retrieved the backend that I plan to deploy. An application's backend is the server-side component responsible for processing requests, handling business logic, and managing data. I retrieved the backend source code by cloning the GitHub repository using the \`git clone\` command.

### ✍️ What are we doing in this step?

In this step, I will build a Docker container image for the backend application and troubleshoot four installation and configuration errors because I need a properly configured, portable, and reproducible image before deploying the application to my Amazon EKS cluster.

### Container image

Once I cloned the backend code, my next step is to build a container image of the backend. This is because containerization packages the application and its dependencies into a consistent, portable environment, ensuring it runs reliably across different environments and can be deployed and managed by Kubernetes on Amazon EKS.

### ✍️ What are we doing in this step?

In this step, I will push the Docker image of my backend application to Amazon Elastic Container Registry (ECR) because EKS needs access to a container image repository to pull the image and deploy it across Kubernetes worker nodes. ECR provides a secure, managed, and scalable registry for storing and managing container images.

I also pushed the container image to a container registry because Amazon EKS needs a centralized location from which worker nodes can pull the image and run the application.

To push the image to ECR, I created an ECR repository, authenticated Docker using the AWS CLI, tagged the local Docker image with the ECR repository URI, and pushed it using \`docker push\`.

### ✍️ What are we doing in this step?

In this step, I will create a Kubernetes Deployment manifest (YAML file) to define how my containerized backend application should run on the EKS cluster. This is because Kubernetes uses the manifest to manage application replicas, container images, resource configurations, and the desired state of the deployment.

## Manifest files

Kubernetes manifests are YAML or JSON configuration files that describe the desired state of Kubernetes resources, such as Deployments, Services, and Pods.

Manifests are helpful because they allow Kubernetes to automatically manage and maintain the desired state of applications, making deployments consistent, repeatable, and easier to update and scale.

A Deployment manifest manages the lifecycle of application Pods by defining the desired state, including the number of replicas, container configuration, and update strategy.\
The container image URL in my Deployment manifest tells Kubernetes where to retrieve the application's container image from (Amazon ECR) so that worker nodes can pull it and run the containers.\
It declaratively tells Kubernetes what should be running and how it should run. Kubernetes continuously works to maintain that desired state, replacing failed Pods and managing replicas and rolling updates.

A Service resource exposes an application running inside Kubernetes Pods through a stable network endpoint and routes incoming traffic to the appropriate Pods.

My Service manifest sets up a NodePort Service named \`nextwork-flask-backend\`, which uses label selectors to identify the backend Pods and routes TCP traffic from port \`8080\` to port \`8080\` inside the containers. This allows external clients to access the application through the worker nodes' IP addresses and assigned NodePort.

### ✍️ What are we doing in this step?

In this step, I will install and configure \`kubectl\` to communicate with my Amazon EKS cluster, then apply my Kubernetes Deployment and Service manifests to deploy the Flask backend. This is because \`kubectl\` allows me to manage Kubernetes resources, monitor application Pods, and verify that my application is running successfully.

![Manifest files](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_b01876554)

## Backend Deployment!

To deploy my backend application, I used \`kubectl apply -f\` to apply the Kubernetes Deployment and Service manifests to my Amazon EKS cluster. The Deployment and Service were successfully recognized, with both resources reporting \`unchanged\`, meaning they already existed and their configurations matched the manifests. This confirmed that Kubernetes accepted my configuration without requiring any updates.

### kubectl

\`kubectl\` is the official Kubernetes command-line tool used to communicate with and manage Kubernetes clusters.

I need this tool to create, update, inspect, and manage Kubernetes resources, such as Deployments, Services, and Pods.

I can't use \`eksctl\` for the same job because \`eksctl\` is primarily designed to provision and manage Amazon EKS clusters and their infrastructure, whereas \`kubectl\` manages Kubernetes resources and workloads running inside the cluster.

![Backend Deployment!](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_6cfb382f2)

## Verifying Deployment

My extension for this project is to use the Amazon EKS Console to inspect and monitor Kubernetes resources, including worker nodes, Pods, Deployments, and Services.

I had to set up IAM access policies because having access to the AWS account does not automatically grant permission to view Kubernetes resources through the EKS Console.

I set up access by creating an EKS Access Entry for my IAM user and associating \`AmazonEKSClusterAdminPolicy\` and \`AmazonEKSAdminViewPolicy\` with Cluster access scope. This allowed me to manage the cluster and access the additional read permissions needed to view its Kubernetes resources.

Once I gained access to my cluster's nodes, I discovered Pods running inside each node. Pods are the smallest deployable units in Kubernetes and represent one or more containers running together.

Containers in a Pod share the same network namespace (including an IP address and localhost communication), storage volumes attached to the Pod, and lifecycle. This allows closely related containers to communicate and share resources efficiently.

The EKS Console shows the events for each Pod, where I could see its scheduling, image-pulling, container creation, and startup activities, as well as any potential errors.

This validated that Kubernetes successfully scheduled my Pods, pulled the backend image from Amazon ECR, and started the application containers as expected.

![Verifying Deployment](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/090a4709-f1f4-5d95-ae4d-b8199bf808ed_3b391f873)
