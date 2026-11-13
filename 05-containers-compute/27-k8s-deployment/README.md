<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Set Up Kubernetes Deployment

**Project Link:** [View Project](https://nextwork.ai/projects/ca1e2f05-dd07-5e77-b83c-1e6a6516944c)

**Author:** Rabia Taha

---

## Introducing Today's Project!

In this project, I will set up a Kubernetes Deployment to manage and run my containerized Flask backend application on Amazon EKS. This will allow Kubernetes to maintain the desired number of application replicas, manage container restarts, and support scaling and rolling updates.

### ✍️ Don't forget to delete your resources!

Repeat this: 'Amazon EKS is not AWS Free Tier eligible. AWS charges $0.10 for every hour my EKS cluster is running. To minimise costs, I will delete all my resources today.'

### ✍️ What are we doing in this step?

In this step, I will launch and connect to an EC2 instance, install and configure eksctl, and set up AWS credentials because I need a properly configured environment with the necessary permissions to provision and manage an Amazon EKS cluster. I will then use eksctl to create the Kubernetes cluster that will host my containerized application.

### Tools and concepts

I used Amazon EKS, Git, Docker, Amazon ECR, and eksctl to containerize and prepare a Flask backend application for deployment on Kubernetes.

Key steps include:\
1\. Cloning the backend source code from GitHub using Git.\
2\. Building a Docker image and resolving permission and configuration issues.\
3\. Pushing the container image to Amazon ECR.\
4\. Launching an EC2 instance and configuring AWS credentials.\
5\. Installing and configuring eksctl.\
6\. Provisioning a Kubernetes cluster using Amazon EKS.

### Project reflection

This project took me approximately 45 minutes. The most challenging part was troubleshooting Docker permission issues and configuring the AWS environment to work correctly with Amazon EKS. My favourite part was building and pushing the Docker image to Amazon ECR and understanding how container registries integrate with Kubernetes deployments.

Something new that I learnt from this experience was how Amazon EKS integrates with Docker, Amazon ECR, and eksctl to create a managed Kubernetes environment. I also learned how to troubleshoot Docker permissions, configure AWS credentials, and prepare containerized applications for Kubernetes deployment.

### ❤️ Thanks for doing this project!

I chose to do this project today because I wanted to gain hands-on experience with Kubernetes and understand how Amazon EKS simplifies container orchestration on AWS.

Something that would make learning with NextWork even better is providing more troubleshooting scenarios and practical challenges that encourage learners to solve real-world infrastructure problems independently.

## What I'm deploying

To set up today's project, I launched a Kubernetes cluster using Amazon EKS. Steps I took to do this included launching and connecting to an EC2 instance, installing and configuring \`eksctl\`, setting up AWS credentials and permissions, and using \`eksctl\` to provision the EKS cluster and its required infrastructure.

### ✍️ What are we doing in this step?

In this step, I will install Git and clone the backend application's source code from GitHub because I need a local copy of the application to inspect its structure, understand its dependencies, and prepare it for containerization and deployment to my Amazon EKS cluster.

### I'm deploying an app's backend

Next, I retrieved the backend that I plan to deploy. An application's backend is the server-side component responsible for processing requests, handling business logic, and managing data. I retrieved the backend source code by cloning the GitHub repository using the \`git clone\` command.

![What I'm deploying](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/ca1e2f05-dd07-5e77-b83c-1e6a6516944c_1ebb86c71)

### ✍️ What are we doing in this step?

In this step, I will build a Docker container image for the backend application and troubleshoot four installation and configuration errors because I need a properly configured, portable, and reproducible image before deploying the application to my Amazon EKS cluster.

## Building a container image

Once I cloned the backend code, my next step is to build a container image of the backend. This is because containerization packages the application and its dependencies into a consistent, portable environment, ensuring it runs reliably across different environments and can be deployed and managed by Kubernetes on Amazon EKS.

When I tried to build a Docker image of the backend, I ran into a permissions error because the \`ec2-user\` did not have sufficient permissions to access the Docker daemon socket (\`/var/run/docker.sock\`). Docker requires appropriate user permissions to communicate with its daemon and execute container-related commands.

To solve the permissions error, I added the \`ec2-user\` to the Docker group using \`sudo usermod -a -G docker ec2-user\`.

The Docker group is a Linux user group that grants its members permission to communicate with the Docker daemon and execute Docker commands without requiring \`sudo\`.

Note: I need to log out and log back in (or run \`newgrp docker\`) for the new group membership to take effect.

![Building a container image](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/ca1e2f05-dd07-5e77-b83c-1e6a6516944c_45e6c3de5)

### ✍️ What are we doing in this step?

In this step, I will push the Docker image of my backend application to Amazon Elastic Container Registry (ECR) because EKS needs access to a container image repository to pull the image and deploy it across Kubernetes worker nodes. ECR provides a secure, managed, and scalable registry for storing and managing container images.

## Container Registry

I'm using Amazon ECR in this project to store and manage the Docker image of my Flask backend application so that my Amazon EKS cluster can securely pull the image during deployment.

ECR is a good choice for this job because it is a fully managed container registry that integrates natively with AWS services, particularly EKS, simplifying image storage, access control, and deployment workflows.

Container registries like Amazon ECR are great for Kubernetes deployment because they provide a centralized and secure place to store container images, allowing Kubernetes clusters to pull the required images whenever they deploy or scale application workloads. They also simplify image management and integrate seamlessly with AWS services like Amazon EKS.

![Container Registry](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/ca1e2f05-dd07-5e77-b83c-1e6a6516944c_l2m3n4o5)
