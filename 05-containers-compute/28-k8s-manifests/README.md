<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Create Kubernetes Manifests

**Project Link:** [View Project](https://nextwork.ai/projects/ccc2aecf-ba9e-5ebe-98ec-e0c4aec9c4ea)

**Author:** Rabia Taha

---

## Introducing Today's Project!

In this project, I will create Kubernetes manifests to define how my containerized application should be deployed, exposed, and managed within the EKS cluster. This is because manifests allow me to declaratively configure Kubernetes resources and maintain a consistent, repeatable deployment process.

### ✍️ Don't forget to delete your resources!

Repeat this: 'Amazon EKS is not AWS Free Tier eligible. AWS charges $0.10 for every hour my EKS cluster is running. To minimise costs, I will delete all my resources today.'

### ✍️ What are we doing in this step?

In this step, I will launch and connect to an EC2 instance, install and configure eksctl, and set up AWS credentials because I need a properly configured environment with the necessary permissions to provision and manage an Amazon EKS cluster. I will then use eksctl to create the Kubernetes cluster that will host my containerized application.

### Tools and concepts

I used Amazon EKS, \`eksctl\`, Docker, Amazon ECR, and \`kubectl\` to provision a Kubernetes cluster, containerize a Flask backend application, and deploy it to AWS.

Key concepts include using Kubernetes manifests to declaratively define Deployments and Services, managing application Pods and replicas, exposing applications through NodePort Services, and using container registries to distribute images to Kubernetes worker nodes.

### Project reflection

I chose to do this project today because I wanted to strengthen my practical Kubernetes skills and understand how containerized applications are deployed and managed using Amazon EKS.

Something that would make learning with NextWork even better is including more real-world troubleshooting scenarios, especially around Kubernetes networking, IAM permissions, and workload scheduling, to help learners understand not just how to deploy applications but also how to debug them independently.

This project took me approximately 45 minutes. The most challenging part was creating and configuring the Kubernetes Deployment and Service manifests, particularly understanding how selectors, labels, ports, and container image references work together. My favourite part was defining the application's desired state through YAML manifests and seeing how Kubernetes uses them to manage and expose the backend application.

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

A Kubernetes Deployment manages the lifecycle of application Pods, ensuring that the desired number of replicas are running and replacing failed Pods when necessary.

The container image URL in my Deployment manifest tells Kubernetes where to find and pull the backend application's Docker image from Amazon ECR so that it can create and run the application containers.

### ✍️ What are we doing in this step?

In this step, I will create a Kubernetes Service manifest (YAML file) to define how my backend application is exposed and how network traffic is routed to its Pods. This is because a Service provides a stable network endpoint for accessing application Pods, even when individual Pods are replaced or their IP addresses change.

![Manifest files](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/ccc2aecf-ba9e-5ebe-98ec-e0c4aec9c4ea_b01876554)

## Service Manifest

A Kubernetes Service exposes an application running inside Pods through a stable network endpoint. You need a Service manifest to define how traffic reaches your application Pods, specify the ports used for communication, and ensure that traffic is routed to the correct Pods using label selectors.

In this project, I used the NodePort service type to expose the Flask backend through a port on each Kubernetes worker node.

My Service manifest sets up a Kubernetes NodePort Service named \`nextwork-flask-backend\`. It selects Pods using the \`app: nextwork-flask-backend\` label and routes incoming TCP traffic on port \`8080\` to port \`8080\` inside the application Pods, making the backend accessible through the Kubernetes worker nodes.

![Service Manifest](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/ccc2aecf-ba9e-5ebe-98ec-e0c4aec9c4ea_b01876555)
