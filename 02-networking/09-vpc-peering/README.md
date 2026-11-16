<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" />
  <img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" />
</picture>

# VPC Peering

**Project Link:** [View Project](https://nextwork.ai/projects/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16)

**Author:** Rabia Taha

![Screenshot](https://nextwork.ai/covers/screenshot_7d2b21910b55fb0252bc24215fdbf173.png)

---

![VPC Peering](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_88727bef)

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate VPC peering.

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources. It is useful because it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to manage a peering connection between two VPCs, with amazing steps for connecting two resources from different VPCs.

### One thing I didn't expect in this project was...

Using the Elastic IP as a way to create a static public address for the instance.

### This project took me...

This project took me 45 minutes.

## In the First Part of My Project...

### Step 1 - Set Up My VPC

In this step, I will create VPCs in a simple way using the "VPC and more" option.

### Step 2 - Create a Peering Connection

In this step, I will create a peering connection between two VPCs or more.

### Step 3 - Update Route Tables

In this step, I will update route tables by setting up the routes for traffic coming from VPC-1 to reach VPC-2 or vice versa.

### Step 4 - Launch EC2 Instances

In this step, I will launch EC2 instances for each VPC so we can test the peering connection.

## Multi-VPC Architecture

I started my project by launching two VPCs using the "Create a VPC and more" option. This option helped me configure them with less time than creating them separately.

The CIDR blocks for VPCs 1 and 2 are `10.1.0.0/16` for VPC-1 and `10.2.0.0/16` for VPC-2. They have to be unique because overlapping IP address ranges can cause routing conflicts and prevent the VPCs from communicating with each other correctly.

### I Also Launched 2 EC2 Instances

I didn't set up key pairs for these EC2 instances as a security login, as we don't need them at this time because AWS already sets it up for us when we click Connect from the AWS EC2 console.

![Multi-VPC Architecture](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_11111111)

## VPC Peering

A VPC peering connection is a networking connection that allows two VPCs to communicate privately with each other using private IP addresses, as if they were part of the same network.

VPCs would use peering connections to communicate privately and securely with resources in another VPC without routing traffic through the public internet.

The difference between a Requester and an Accepter in a peering connection is that the Requester initiates the VPC peering connection, while the Accepter is the VPC that receives and accepts the peering request.

![VPC Peering](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_1cbb1b88)

## Updating Route Tables

After accepting a peering connection, my VPCs' route tables need to be updated because even if our peering connection has been accepted, traffic in VPC-1 won't know how to get to resources in VPC-2 without a route in our route table. So we need to set up a route that directs traffic bound for VPC-2 to the peering connection you've set up.

My VPCs' new routes have the CIDR block of the other VPC as their destination. The routes use the VPC peering connection as their target, which allows traffic to be routed between VPC-1 and VPC-2 through the peering connection.

![Updating route tables](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_4a9e8014)

## In the Second Part of My Project...

### Step 5 - Use EC2 Instance Connect

In this step, I will use EC2 Instance Connect to connect to your first EC2 instance.

### Step 6 - Connect to EC2 Instance 1

In this step, I will connect to Instance 1, and if there is a problem, we'll fix it.

### Step 7 - Test VPC Peering

In this step, I will test VPC peering between my VPCs.

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect because it's a simple way to connect to our instances since AWS handles the connection configuration behind the scenes.

I was stopped from using EC2 Instance Connect because the instance does not have a public IP.

![Troubleshooting Instance Connect](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_7685490c)

## Elastic IP Addresses

To resolve this error, I set up Elastic IP addresses. Elastic IP addresses are static IP addresses that we can allocate to our resources to avoid changing the DNS connections that take time to update over the internet. Using Elastic IP ensures that changes do not happen when our resources are rebooted or replaced.

Associating an Elastic IP address resolved the error because we didn't previously assign a public IP to our instance. By associating an Elastic IP to our instance, it resolves the problem of not having a public IP.

![Elastic IP addresses](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_45663498)

## Troubleshooting Ping Issues

To test VPC peering, I ran the command `ping privateIP` and it worked — the multiple new lines appearing in our terminal are a sign of successful communication.

A successful ping test would validate my VPC peering connection because it confirms that resources in the two VPCs can communicate with each other over their private IP addresses through the peering connection.

I had to update my second EC2 instance's security group because the inbound rules denied requests that used ICMP, so I added a new rule that allows ICMP connections, saved it, and it worked — the ping requests appeared in Instance 1.

![Troubleshooting ping issues](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/fd75209e-d2a1-5bdd-90e8-bdb9ee49de16_7a29d352)
