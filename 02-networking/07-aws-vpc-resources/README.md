## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to lunch VPC resources

### ✍️ What are we doing in this step?

In this step, I will create private resources for our VPC

### ✍️ What are we doing in this step?

In this step, I will createand lunch  a new EC2 instances in the public subnet

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS, and it is useful because it allows me to control how my AWS resources communicate by configuring IP addresses, subnets, routing, and network access.

### How I used Amazon VPC in this project

I used Amazon VPC to create multiple envirement for our internal resources with multiple ways to save time

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was i can create VPCs  in 2  minite using the other option (create VPC and more) in the VPC creation page that provide single page to setup  every thing that need to lunch

### This project took me...

This project took me 45 mins

## Setting Up Direct VM Access

Directly accessing a virtual machine means logging into and managing the operating system or software of the machine as if you were using it in front of you, but over the internet

### SSH is a key method for directly accessing a VM

SSH traffic means network traffic used to establish a secure, encrypted connection to a remote computer, such as an EC2 instance.

### To enable direct access, I set up key pairs

Key pair are a set of two mathematically linked cryptographic keys used to encrypt data, decrypt data, and verify identities , we use it in our EC2 in order make a secure connection between the client and EC2 (in this case we don't use it here just simple connection)

A private key's file format means just like how documents can be saved in various file formats like PDF, DOCX, or TXT ,in private keys have its own format. My private key's file format was .pem

## Launching a public server

Start your response with 'I had to change my EC2 instance's networking settings by navigate to network setting and change the VPC to the VPC that we already create it and attach to it a public subnet and implement the security group that we created

### ✍️ What are we doing in this step?

In this step, I will create another EC2 instances in the private subent and make sure it's secure and setup a connection to other resources privatly

![Launching a public server](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8f49d756-9e51-58c0-856a-e71e54f064ab_88727bef)

## Launching a private server

My private server has its own dedicated security group because I want to control and restrict the traffic allowed to and from the private server independently from other resources.

My private server's security group's source is custom, which means I can specify exactly which IP address, IP range, or security group is allowed to send traffic to the server.

### ✍️ What are we doing in this step?

In this step, I will create a new VPC with another way much save time than this

![Launching a private server](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8f49d756-9e51-58c0-856a-e71e54f064ab_4a9e8014)

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I used the VPC creation wizard to automatically configure the VPC, subnets, route tables, and other networking components instead of setting them up individually. this save much time rather config each one separately

A VPC resource map is a visual representation of the resources and networking relationships within a VPC, such as subnets, route tables, gateways, and their connections.

My new VPC has a CIDR block of "10.0.0.0/16". It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because \*\*VPCs are isolated from each other by default, so their IP address ranges can overlap as long as they do not need to communicate directly with each other.

![Speeding up VPC creation](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8f49d756-9e51-58c0-856a-e71e54f064ab_1cbb1b88)

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: 1 or 2 public subnets\*\*. This was because \*\*the VPC setup wizard only provides those options for the selected configuration.

The setup page also offered to create NAT gateways, which are AWS networking components that allow resources in a private subnet to access the internet for outbound connections without allowing direct inbound connections from the internet.

![Speeding up VPC creation](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8f49d756-9e51-58c0-856a-e71e54f064ab_8ee57662)
