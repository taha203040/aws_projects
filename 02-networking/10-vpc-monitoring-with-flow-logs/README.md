<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" />
  <img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" />
</picture>

# VPC Monitoring with Flow Logs

**Project Link:** [View Project](https://nextwork.ai/projects/6954a600-a89e-56b0-886b-7054da118a3b)

**Author:** Rabia Taha

![Screenshot](https://nextwork.ai/covers/screenshot_90b980e2cf0495b31fa8b3f8d8d22816.png)

---

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to do VPC monitoring with Flow Logs in order to complete the AWS VPC series.

### What is Amazon VPC?

Amazon VPC is **a logically isolated virtual network in AWS where I can deploy and control my cloud resources**.

It is useful because **it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.**

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC with CloudWatch to **monitor my network resources, analyze traffic patterns, and gain insights into their activity and performance.**

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was implementing the peering connection, along with extra editing of the route table to set up the routes from and to the two VPCs.

### This project took me...

This project took me 1 hour.

## In the First Part of My Project...

### Step 1 - Set Up VPCs

In this step, I will create two VPCs in order to set up the environment of this project. Each VPC will have its own unique, non-overlapping CIDR block, which I'll need later to establish a peering connection between them.

### Step 2 - Launch EC2 Instances

In this step, I will launch EC2 instances in each VPC so we can use them to test the VPC peering connection later. These instances will generate the network traffic that Flow Logs will capture.

### Step 3 - Set Up Logs

In this step, I will set up a log group that stores all inbound and outbound records of network traffic. This gives me a central place to view, search, and retain the flow log data.

### Step 4 - Set IAM Permissions for Logs

In this step, I will set up the permissions for Flow Logs to write logs and send them to CloudWatch, and finish the settings related to my subnet's flow log. This includes creating an IAM policy with the required permissions and an IAM role that Flow Logs can assume to deliver the data.

## Multi-VPC Architecture

I started my project by launching two VPCs in order to use them in this project.

The CIDR blocks for VPC-1 and VPC-2 are `10.1.0.0/16` and `10.2.0.0/16`, respectively. They must be unique and non-overlapping to avoid IP address conflicts and ensure proper routing when establishing a VPC peering connection.

### I Also Launched EC2 Instances in Each Subnet

My EC2 instances' security groups define firewalls against foreign requests, which protects them from bad behavior by hackers.

![Multi-VPC Architecture](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_e7fa8775)

## Logs

Logs are like a diary for your computer systems. They record everything that happens, from users logging in to errors popping up. It's the go-to place to understand what's going on with your systems, troubleshoot problems, and keep an eye on who's doing what.

Log groups are containers that organize and store related log streams, making it easier to set retention, permissions, and access to the logs in one place.

![Logs](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_e8398869)

### ✍️ What is a flow log?

VPC Flow Logs are a feature that captures information about IP traffic going to and from network interfaces in a VPC, allowing me to monitor network traffic, troubleshoot connectivity issues, and identify potential security threats.

## IAM Policy and Roles

I created an IAM policy because, in order to write and send the logs to CloudWatch, Flow Logs does not have permission by default, so we create an IAM policy to handle this problem.

I also created an IAM role because VPC Flow Logs need permissions to send log data to Amazon CloudWatch Logs securely. The role uses the policy I created and is assumed by the Flow Logs service when it delivers data.

A custom trust policy is a specific type of policy! They're different from IAM policies. While IAM policies help you define the actions a user or service can or cannot do, custom trust policies are used to narrowly define who can use a role.

![IAM Policy and Roles](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_4334d777)

## In the Second Part of My Project...

### Step 5 - Ping Testing and Troubleshooting

In this step, I will get Instance 1 to send test messages to Instance 2 in order to test the peering connection. I'll run a `ping` against the private IP and observe whether replies come back.

### Step 6 - Set Up a Peering Connection

In this step, I will create a peering connection and configure route tables in order to get a successful connection. This involves accepting the peering request and adding routes in both VPCs so private traffic flows directly between them.

### Step 7 - Analyze Flow Logs

In this step, I will analyze Flow Logs by reviewing the flow log records and analyzing the flow to get some insights. I'll look at source/destination IPs, ports, protocols, and whether traffic was accepted or rejected.

## Connectivity Troubleshooting

My first ping test between my EC2 instances had no replies, which means there is no connection between Instance 1 and Instance 2 (it blocks connections from foreign requests).

![Connectivity troubleshooting](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_99d4ba42)

I received ping replies when I used the other instance's public IP address, which indicates that ICMP traffic is allowed through the public IP path, while traffic through the private IP path is blocked.

## Connectivity Troubleshooting

Looking at VPC-1's route table, I identified that the ping test with Instance 2's private address failed because we didn't set up a direct connection between these resources. Instead, the ping test we ran travelled through the internet gateway and reached it through a public connection. For now, we need to set up a connection directly between them without relying on a public connection.

### To Solve This, I Set Up a Peering Connection Between My VPCs

I also updated both VPCs' route tables so that we create a direct route between them, so requests through the private IP go directly through the peering connection.

![Connectivity troubleshooting](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_7316a13d)

## Connectivity Troubleshooting

I received ping replies from Instance 2's private IP address! This means the peering connection is successfully done.

![Connectivity troubleshooting](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_4ec7821f)

## Analyzing Flow Logs

Flow Logs tell us about IP traffic flowing to and from network interfaces in a VPC, including source and destination IP addresses, ports, protocols, and whether traffic was accepted or rejected.

For example, the flow log I've captured tells us that 344 bytes of data were successfully transferred from `18.237.140.165` to `10.1.5.112` over TCP port 22 (SSH), using 4 packets. The traffic was allowed, as indicated by the "ACCEPT" action.
This confirms that EC2 Instance Connect established an SSH connection to Instance 1, since the source IP belongs to EC2 Instance Connect's IP range in the Oregon region (`18.237.140.160/29`).

![Analyzing flow logs](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_d116818e)

## Logs Insights

CloudWatch Logs Insights is a tool that allows me to interactively query, analyze, and visualize log data to troubleshoot issues, monitor network traffic, and identify potential security problems.

I ran the query `stats sum(bytes) as bytesTransferred by srcAddr, dstAddr` to analyze the total amount of data transferred between each source and destination IP address. The query sorts the results by the amount of data transferred in descending order and shows the top 10 connections from the last hour.

![Logs Insights](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_3e1e79a1)
