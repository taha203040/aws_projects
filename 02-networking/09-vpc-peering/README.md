![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_88727bef)

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate the VPC peering

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources\
It is useful because it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to manage peering Connection between two VPCs with amazing steps for connecting two resources from diffrenet VPCs

### One thing I didn't expect in this project was...

using the Elastic IP as way to create static public address for the instance

### This project took me...

This project took me 45mins

## In the first part of my project...

### Step 1 - Set up my VPC

In this step, I will create VPCs in simple way using the VPC and more option

### Step 2 - Create a Peering Connection

In this step, I will Create a Peering Connection between two VPCs or more !!

### Step 3 - Update Route Tables

In this step, I will Update Route Tables by setting up the ways for the traffics that comming from VPC1 to get VPC2 or the or vice versa.

### Step 4 - Launch EC2 Instances

In this step, I will lunch EC2 instanses for each VPC so we can test peering Connection

## Multi-VPC Architecture

I started my project by launching two VPCs using the "Create a VPC and more" this option help me to config them with less time than creating sepreatly

The CIDR blocks for VPCs 1 and 2 are 10.1.0.0/16 for VPC-1 and 10.2.0.0/16 for VPC-2. They have to be unique because overlapping IP address ranges can cause routing conflicts and prevent the VPCs from communicating with each other correctly.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as security login , as we don't need them at this time because AWS already set it for us when click on the connect from AWS EC2 console

![Multi-VPC Architecture](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_11111111)

## VPC Peering

A VPC peering connection is a networking connection that allows two VPCs to communicate privately with each other using private IP addresses, as if they were part of the same network.

VPCs would use peering connections to communicate privately and securely with resources in another VPC without routing traffic through the public internet.

The difference between a Requester and an Accepter in a peering connection is that the Requester initiates the VPC peering connection, while the Accepter is the VPC that receives and accepts the peering request.

![VPC Peering](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_1cbb1b88)

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because Even if our peering connection has been accepted, traffic in VPC 1 won't know how to get to resources in VPC 2 without a route in our route table! So we need to set up a route that directs traffic bound for VPC 2 to the peering connection you've set up.

My VPCs' new routes have the CIDR block of the other VPC as their destination. The routes use the VPC peering connection as their target, which allows traffic to be routed between VPC-1 and VPC-2 through the peering connection.

![Updating route tables](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_4a9e8014)

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step, I will use EC2 Instance Connect to connect to your first EC2 instance

### Step 6 - Connect to EC2 Instance 1

In this step, I will connect to the Instance 1 , and if there a problem we fix it

### Step 7 - Test VPC Peering

In this step, I will Test VPC Peering between my VPCs

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect because it's simple way to connect to our instances because AWS handle the connection config behind the scene

I was stopped from using EC2 Instance Connect as the instance does not have public IP ,

![Troubleshooting Instance Connect](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_7685490c)

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static IP address that we can allocate it to our resources to avoid the changing the DNS connections that take time to update over the internet by using Elastic IP ensure that changing does not happend when our resources are rebooted or replaced

Associating an Elastic IP address resolved the error because we don't previously assign a public IP to our instance , by associating and Elastic IP to our instance it resolve the problem of public IP

![Elastic IP addresses](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_45663498)

## Troubleshooting ping issues

To test VPC peering, I ran the command \`ping privateIP'\
and it workds by showing  multiple new lines appearing in our terminal are a sign of successful communication

A successful ping test would validate my VPC peering connection because it confirms that resources in the two VPCs can communicate with each other over their private IP addresses through the peering connection.

I had to update my second EC2 instance's security group because the inbound rules deny the requests that used ICMP so  I added a new rule that allow ICMP connection and save it and it works and the Ping requests appear in the instance-1

![Troubleshooting ping issues](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_7a29d352)
