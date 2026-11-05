## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to do VPC Monitoring with Flow Logs in order to complete the AWS VPC series

### What is Amazon VPC?

Amazon VPC is \*\*a logically isolated virtual network in AWS where I can deploy and control my cloud resources\*\*.

It is useful because \*\*it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.\*\*

### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC with CloudWatch to \*\*monitor my network resources, analyze traffic patterns, and gain insights into their activity and performance.\*\*

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was implementing the peering connection with extra editing the route table to implement the reouts from and to two VPCs

### This project took me...

This project took me 1 hour

## In the first part of my project...

### Step 1 - Set up VPCs

In this step, I will create two VPC in order to setup the envirement of this project !

### Step 2 - Launch EC2 instances

In this step, I will lunch EC2 instaces so we can use them to test VPC peering connection later.

### Step 3 - Set up Logs

In this step, I will setup a space that stores all of inbound and outbounds records of network Traffic

### Step 4 - Set IAM permissions for Logs

In this step, I will setup the permission for Flow Logs to write logs and send them to CloudWatch , and finnishing the setting related to my subnet's flow log

## Multi-VPC Architecture

I started my project by launching 2 VPC in order to use them on this project

The CIDR blocks for VPC-1 and VPC-2 are \`10.1.0.0/16\` and \`10.2.0.0/16\`, respectively. They must be unique and non-overlapping to avoid IP address conflicts and ensure proper routing when establishing a VPC peering connection.

### I also launched EC2 instances in each subnet

My EC2 instances' security groups allow define firewalls againts forgain requests that secure from bad behaviors from hackers

![Multi-VPC Architecture](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_e7fa8775)

## Logs

Logs are like a diary for your computer systems. They record everything that happens, from users logging in to errors popping up. It's the go-to place to understand what's going on with your systems, troubleshoot problems, and keep an eye on who’s doing what.

Log groups are

![Logs](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_e8398869)

### ✍️ What is a flow log?

VPC Flow Logs are a feature that captures information about IP traffic going to and from network interfaces in a VPC, allowing me to monitor network traffic, troubleshoot connectivity issues, and identify potential security threats.

## IAM Policy and Roles

I created an IAM policy because in order to write and send the logs to CloudWatch Flow logs does not have the permission for that so we create  IAM policy to handle this problem

I also created an IAM role because VPC Flow Logs need permissions to send log data to Amazon CloudWatch Logs securely

A custom trust policy is a is specific type of policy! They're different from IAM policies. While IAM policies help you define the actions a user/service can or cannot do, custom trust policies are used to very narrowly define who can use a role.

![IAM Policy and Roles](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_4334d777)

## In the second part of my project...

### Step 5 - Ping testing and troubleshooting

In this step, I will get instand 1 to send test messages to instance 2 in order to test Peering test

### Step 6 - Set up a peering connection

In this step, I will Create a Peering Connection and Configure Route Tables in order to get successfull connection

### Step 7 - Analyze flow logs

In this step, I will Analyze Flow Logs by reviewing the flow logs records and analyse th flow to get some inightes

## Connectivity troubleshooting

My first ping test between my EC2 instances had no replies, which means there is no connection between the instance-1 and instance-2 (it's blocks the connections from forgain requests)

![Connectivity troubleshooting](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_99d4ba42)

I received ping replies when I used the other instance's public IP address, which indicates that ICMP traffic is allowed through the public IP path, while traffic through the private IP path it blocks it

## Connectivity troubleshooting

Looking at VPC 1's route table, I identified that the ping test with Instance 2's private address failed because we don't setup direct connection between these resources instand the ping test that we do it it travel throw the internet gateway and reach it throw a public connection for now we need to setup a connection directly between them without rely on public connection

### To solve this, I set up a peering connection between my VPCs

I also updated both VPCs' route tables so that we create a direct route between them so the requests throw the private IP goes direct throw the peering connection

![Connectivity troubleshooting](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_7316a13d)

## Connectivity troubleshooting

I received ping replies from Instance 2's private IP address! This means the peering connection is successfully done

![Connectivity troubleshooting](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_4ec7821f)

## Analyzing flow logs

low Logs tell us about IP traffic flowing to and from network interfaces in a VPC, including source and destination IP addresses, ports, protocols, and whether traffic was accepted or rejected.

For example, the flow log I've captured tells us that 344 bytes of data were successfully transferred from 18.237.140.165 to 10.1.5.112 over TCP port 22 (SSH), using 4 packets. The traffic was allowed, as indicated by the "ACCEPT" action.\
This confirms that EC2 Instance Connect established an SSH connection to Instance 1, since the source IP belongs to EC2 Instance Connect's IP range in the Oregon region (\`18.237.140.160/29\`).

![Analyzing flow logs](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_d116818e)

## Logs Insights

CloudWatch Logs Insights is a tool that allows me to interactively query, analyze, and visualize log data to troubleshoot issues, monitor network traffic, and identify potential security problems.

I ran the query \`stats sum(bytes) as bytesTransferred by srcAddr, dstAddr\` to analyze the total amount of data transferred between each source and destination IP address. The query sorts the results by the amount of data transferred in descending order and shows the top 10 connections from the last hour.

![Logs Insights](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/6954a600-a89e-56b0-886b-7054da118a3b_3e1e79a1)
