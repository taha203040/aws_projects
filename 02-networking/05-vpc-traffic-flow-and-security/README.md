## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to Create a route table Create a security group nad  Create a Network ACL (Network Access Control List).I'm doing this project to learn more about the AWS-network -security

### ✍️ What are we doing in this step?

In this step, I will to create a VPC and subnets and internet gateway for our projects

### ✍️ What are we doing in this step?

In this step, I will implement route table by creating it in order   to direct traffic from my resource to my internet gateway

### What is Amazon VPC?

Amazon VPC is a service that allows me to create and manage a logically isolated virtual network in AWS, and it is useful because it gives me control over networking, including subnets, route tables, and network security.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a virtual network, configure subnets, route tables, an Internet Gateway, security groups, and network ACLs.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how many networking components need to work together to allow resources to communicate securely.

### This project took me...

This project took me one and a half hours to complete it including the setup the previous project with today

## Route tables

Route tables are predefined routes inside our vpc that route the public internet traffic to our public resources inside our VPC (we consider a subnet is public when it have a bridge connection to internet gateway)

Routes tables are needed to make a subnet public because its the bridge between the internet gateway and the public subnet ( we consider a public subnet if had connection to internet gateway)

## Route destination and target

Routes are defined by their destination and target, which mean every public internet traffic are defined and shaped way to get a specific route inside our VPC resources without goes randomlly in our VPC so its good pracitse to secure our VPC

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of Internet Gateway (igw).

### ✍️ What are we doing in this step?

In this step, I will create and configure a security group to ensure that the resources have the appropriate network permissions and are protected from unauthorized or potentially malicious traffic.

![Route destination and target](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-security_0a07b191)

## Security groups

Security groups are virtual firewalls that control inbound and outbound network traffic for AWS resources.

### Inbound vs Outbound rules

Inbound rules are rules that control incoming traffic to a resource. I configured an inbound rule that allows the required traffic on the specified port from an authorized source.

Outbound rules are rules that control outgoing traffic from a resource. By default, my security group's outbound rule allows all outbound traffic to any destination (0.0.0.0/0).

### ✍️ What are we doing in this step?

In this step, I will create an ACL for our network

![Security groups](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-security_92b0b0b4)

## Network ACLs

Network ACLs are a security layer that controls inbound and outbound traffic at the subnet level using allow and deny rules.

### Security groups vs. network ACLs

The difference between a security group and a network ACL is that a security group operates at the instance/resource level and is stateful, while a network ACL operates at the subnet level and is stateless.

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all traffic.

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all traffic.

![Default vs Custom Network ACLs](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-security_4faeb056)
