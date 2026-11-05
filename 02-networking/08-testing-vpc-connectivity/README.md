## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how  VPC Testing VPC Connectivity, we're going to level up by testing our VPC's connectivity

### ✍️ What are we doing in this step?

In this step, I will setup my VPC basics and dive straight into and start from where we left off in the last project

### ✍️ What are we doing in this step?

In this step, I will connect to my instance using servrel methods

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources\
It is useful because it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to test connectivity between resources in the same VPC and with my resources and the servers on the internet

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was not touching the ACLs of the subnets

### This project took me...

This project took me 45 mins

## Connecting to an EC2 Instance

Connectivity means  all about how well different parts of our network talk to each other and with external networks. It's essential because connectivity is how data flows smoothly across our network, powering everything from simple web hosting on the Internet to complex operations..etc

My first connectivity test was whether I could connect to the nextwork public instance and it failed due we setup a Key-Pair to secure connection

![Connecting to an EC2 Instance](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/da091986-ef01-5973-a070-b15e174f59d8_88727bef)

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is direct method in the AWS instance console which provide direct connection and easy one (just click connect and you are done)

My first attempt at getting direct access to my public server resulted in an error, because the  SSH connection type in the security group in the Inbound rules are not allowed

I fixed this error by adding SSH type to the security group of the inbound rules it solved and the connection success (there also configs about the ip address it's up to you to config it as u like)

### ✍️ What are we doing in this step?

In this step, I will Test connectivity between your EC2 instances

![EC2 Instance Connect](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/da091986-ef01-5973-a070-b15e174f59d8_1cbb1b88)

## Connectivity Between Servers

Ping is a common computer network tool used to check whether your computer can communicate with another computer or device on a network.  I used ping to test the connectivity between the private instance and the public instanse

The ping command I ran was ping "ip\_address" of the private instance that locate in the private subnet

The first ping returned a single line indicates that our  Public Server has sent out a ping message .This mean the Private Server is blocking the incoming requests

![Connectivity Between Servers](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/da091986-ef01-5973-a070-b15e174f59d8_defghijk)

## Troubleshooting Connectivity

I troubleshooted this by \
First : we go to the Network ACLs and allow the connections from All ICMP-IPv4 and setting the source 10.0.0.0/24 and Allow it ,(both on the inbound rules and the outbound)\
Second : we go to the security groups and Edit the Private Security group and edit it by adding the Type All-ICMP  and implement the Source to Nextworkpublicgroup (just in the inbound rules)\
Notice that we don't implement the Nextworkpublicgroup as a source in ACLs because NACLs typically have a broader scope since its settings would affect all resources in our subnet.

### ✍️ What are we doing in this step?

In this step, I will Test VPC connectivity with the internet by getting our Public Server to talk to the internet

![Troubleshooting Connectivity](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/da091986-ef01-5973-a070-b15e174f59d8_4a9e8014)

## Connectivity to the Internet

Curl is a tool to test connectivity in a network it's used to transfer data to or from a server.

I used curl to test the connectivity between my instance and a server (domain)

### Ping vs Curl

Ping and curl are different because they are used for different purposes. Ping is used to test network connectivity by checking whether one computer can reach another and measuring the round-trip time. Curl is used to transfer data to or from a server, commonly through protocols such as HTTP or HTTPS.

## Connectivity to the Internet

I ran the curl command curl example.com which returned a HTML content which a assign to the connectivity between my instance and the the server successed by transfer data

![Connectivity to the Internet](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/da091986-ef01-5973-a070-b15e174f59d8_8ee57662)
