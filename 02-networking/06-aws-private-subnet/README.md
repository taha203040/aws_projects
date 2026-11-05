## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to create a private subnets and tableroutes nd ACL , I'm doing this project to learn more VPC and master it

### ✍️ What are we doing in this step?

In this step, I will implement the previous VPC setups to use it in this project

### ✍️ What are we doing in this step?

In this step, I will create a private for extra security for internal resources in our VPC

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources.\
It is useful because  it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.

### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC to \*\*create a secure network environment with public and private subnets, configure routing, and control access to my resources using security groups and network ACLs.\*\*

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is \*\*how many networking components, such as route tables, security groups, and network ACLs, work together to secure and control access to resources within a VPC.\*\*

### This project took me...

This project took me nearly 45 mins

## Private vs Public Subnets

The difference between public and private subnets is that public subnet 's route table is connected with the internet gateway and the private not

Having private subnets are useful to implement extra layer to our internal resources inside VPC , some resources like databases to insure its not available access in public side we create private subnets

My private and public subnets cannot have the same ip CIDR block adresss because each of them allocate a diffrenet one

### ✍️ What are we doing in this step?

In this step, I will setup a private route table to associated with a  subnets

![Private vs Public Subnets](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-private_afe1fdbd)

## A dedicated route table

By default, my private subnet is associated with the VPC’s main route table.

I had to set up a new route table because I wanted to control the routing of my private subnet separately from the public subnet.

My private subnet's dedicated route table only has a local route for traffic within the VPC, allowing resources in the subnet to communicate with other resources in the VPC.

### ✍️ What are we doing in this step?

In this step, I will setup network ACL for my private subnet

![A dedicated route table](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-networks-private_b4b904b5)

## A new network ACL

By default, my private subnet is associated with the VPC's main route table and attach it to the private route table

I set up a dedicated network ACL for my private subnet to restrict and control traffic to and from the resources within the subnet.

My new network ACL has two simple rules — \*\*one inbound rule and one outbound rule, both denying all traffic from \`0.0.0.0/0\`.

![A new network ACL](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/4e96e29d-98b8-551e-ae93-da39c36e30fd_1ed2cb07)
