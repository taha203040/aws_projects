## Introducing Today's Project!

In this project, I will demonstrate how to create and configure a Virtual Private Cloud (VPC) on AWS. I'm doing this project to learn how to design and build cloud networking infrastructure properly, including configuring subnets, route tables, internet gateways, and network security. My goal is to understand how these components work together to create a secure and reliable network environment.

## Virtual Private Clouds (VPCs)

### What I did in this step

In this step, I will create a VPC because it provides an isolated and logically defined network environment where I can deploy and manage AWS resources. It also allows me to control IP addressing, network segmentation, routing, and access to my resources.

### How VPCs work

A Virtual Private Cloud (VPC) is an isolated virtual network within the AWS Cloud. It allows me to launch resources such as EC2 instances and databases within a defined IP address range . VPCs provide control over network configurations, including subnets, route tables, and gateways, helping me organize and secure communication between resources.

### Why there is a default VPC in AWS accounts

There was already a default VPC in my AWS account when it was created. AWS provides a default VPC so that I can launch resources such as EC2 instances without having to configure an entire network from scratch.

The default VPC comes with preconfigured networking components, including subnets in Availability Zones, an Internet Gateway, and route tables. This makes it easier to get started with AWS services.

![Virtual Private Clouds (VPCs)](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-vpc_2facf927)

### Defining IPv4 CIDR blocks

To configure my VPC, I had to define an IPv4 CIDR block. A CIDR block represents the range of IP addresses available within my VPC.This address range determines how many private IP addresses can be allocated to resources deployed inside the VPC. Choosing an appropriate CIDR block is important to avoid overlapping IP ranges, especially when connecting multiple networks.

## Subnets

### What I did in this step

In this step, I will create a subnet because a subnet divides the VPC into smaller network segments, allowing me to organize and control where resources such as EC2 instances are deployed.

### Creating and configuring subnets

Subnets are smaller network segments within a VPC, similar to how neighborhoods are smaller sections of a city . Each subnet belongs to a single Availability Zone. When configuring my VPC, I can create multiple subnets across different Availability Zones to distribute resources and improve fault tolerance.

### Public vs private subnets

The main difference between public and private subnets is their routing configuration. A public subnet has a route in its associated route table pointing to an Internet Gateway (IGW), allowing resources with public IP addresses to communicate with the internet. A private subnet does not have a direct route to an Internet Gateway. However, it can still access the internet through a NAT Gateway if one is configured. This separation helps protect internal resources, such as databases, while allowing public-facing resources to communicate with external users.

![Subnets](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-vpc_157c4219)

### Auto-assigning public IPv4 addresses

"Once I created my subnet, I enabled Auto-assign Public IPv4 Address. This setting ensures that any EC2 instance launched in the subnet automatically receives a public IPv4 address, eliminating the need to assign one manually."

## Internet gateways

### What I did in this step

In this step, I will create an Internet Gateway because my VPC needs a gateway and appropriate routing configuration to enable communication with the public internet.

### Setting up internet gateways

An Internet Gateway (IGW) is an AWS-managed component that enables communication between resources in a VPC and the public internet. After creating an Internet Gateway, I must attach it to my VPC and configure the appropriate route table with a route pointing to the gateway. For example, a route with destination `0.0.0.0/0` and the Internet Gateway as its target allows IPv4 traffic destined for external networks to use that gateway. It is important to attach the Internet Gateway to the VPC I created, rather than accidentally attaching it to the default VPC. Without an attached Internet Gateway and a suitable route, resources in my public subnet cannot establish direct internet connectivity through it.

![Internet gateways](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-vpc_4ae90410)

## Using the AWS CLI

### What I'm doing in this extension

In this project extension, I will use AWS CloudShell to execute AWS CLI commands and manage my VPC resources. I'm exploring this approach because using commands can save time when creating and configuring multiple networking resources compared to navigating through the AWS Management Console.

### Exploring CloudShell and CLI

AWS CloudShell is a browser-based shell environment that allows me to interact with AWS services directly through the command line. It comes with the AWS CLI preinstalled, allowing me to execute commands to create, inspect, and manage AWS resources. CLI stands for Command Line Interface. Instead of manually navigating through the AWS Console, I can use commands to automate operations and perform multiple configurations efficiently.

### Debugging my setup

While configuring my VPC and subnets through the AWS CLI, I learned that commands require the correct resource identifiers and configuration values.

For example, when creating a subnet, I need to provide the VPC ID and the CIDR block that will be assigned to that subnet.

I also need to ensure that the subnet's CIDR block belongs to the VPC's address range and does not overlap with existing subnets.

Understanding these requirements helped me troubleshoot configuration errors and become more comfortable managing AWS networking resources through the CLI.

![Using the AWS CLI](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-vpc_9b2465411)

### Comparing CloudShell vs AWS Console

Both AWS CloudShell and the AWS Management Console provide ways to manage cloud resources, but they offer different advantages.

One advantage of AWS CLI is that it allows me to execute commands quickly, automate repetitive tasks, and create multiple resources without navigating through several pages.

On the other hand, the AWS Console provides a graphical interface that makes it easier to inspect resource configurations, monitor their status, and understand how different components are connected.

Overall, I preferred using AWS CLI for creating and configuring multiple resources because of its speed and flexibility, while using the AWS Console to verify configurations and monitor the results.
