## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to using VPC Endpoints in order to complete the last VPC series

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources.\
It is useful because it allows me to control networking, including IP addresses, subnets, routing, and access to my resources

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a seccure  connection between S3 and ec2 using VPC endpoint that result us to make a direct connection from EC2 to S3 bucket without our traffic goes throw the public internet

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was using Endpoint to make secure connection between VPC and S3

### This project took me...

This project took me 30 min

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will step a VPC and EC2 and S3 in order to setup the foundations fo this project

### Step 2 - Connect to EC2 instance

In this step, I will connect to my EC2 instance directly using AWS console , without complex method

### Step 3 - Set up access keys

In this step, I will create a access keys in order to give access to my EC2 instance to intract with S3 from it

### Step 4 - Interact with S3 bucket

In this step, I will connect the EC2 instance that lunch in VPCs to intract with the S3 that we created before

## Architecture set up

I started my project by launching VPC and EC2 instance and attach it into the VPC that we created , notice that we don't select Exist security group and just create simple one with name \`SG - NextWork VPC Project\`

I also set up S3 bucket and upload two files on it , in order to access to S3 bucket from EC2 instance , this help us to preform multiple actions and running CMD from EC2 !!

![Architecture set up](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_4334d777)

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured it by setup the Access Key ID and Secret Access ID and the Region name , we don't specify the format and leave as it is(the default is JSON)

Access keys are credentials for my applications and other servers to log into AWS and talk to your AWS services/resources.

A secret access key is similar to a password that is paired with an Access Key ID. Both are required to authenticate with the AWS API and access AWS services according to the permissions assigned to the associated IAM identity.

### Best practice

Although I'm using access keys in this project, a best-practice alternative is to use IAM roles or temporary credentials, which provide short-lived access without requiring long-term access keys to be stored or managed.

## Connecting to my S3 bucket

The command I ran was \`aws s3 ls \` when i run it  , it show that i need a required credentials in order to execute it correctly .This command is used to show the the list of S3 buckets in my account

When I ran the command \`aws s3 ls\` again, the terminal responded with  lines of  my S3 buckets This indicated that we successfully config the credentials in the EC2 instsance

![Connecting to my S3 bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_4334d778)

## Connecting to my S3 bucket

Another CLI command I ran was \`aws s3 ls s3://nextwork-vpc-project-ahmdrb-vwrl \` which returned the all the files that stored in the bucket

![Connecting to my S3 bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_4334d779)

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command \`sudo touch /tmp/test.txt\` This command creates a file in the directory test.txt

The second command I ran was aws \`s3 cp /tmp/test.txt s3://nextwork-vpc-project-\[uniquename\[ \`This command will upload the file into the S3 bucket

The third command I ran was\` aws s3 ls s3://nextwork-vpc-project-ahmdrb-vwrl \` which validated that our file is successfully upload it in the S3 bucket

![Uploading objects to S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_3e1e79a2)

## In the second part of my project...

### Step 5 - Set up a Gateway

In this step, I will setup a way for my VPC and S3 bucket to communicate direclty.

### Step 6 - Bucket policies

In this step , we are limit access to the S3 bucket , from our VPC , previously the traffic goes throw the public internet , but now we are creating a super secure bucket policy that ensure all the traffic to and from direct from S3 to VPC enpoint

### Step 7 - Update route tables

In this step, I will test my VPC endpoint setup and Troubleshoot a connectivity issue.

![In the second part of my project...](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_67081648)

### Step 8 - Validate endpoint conection

In this step, I will test the setup again after solving the problem and Restrict my VPC's acccess to my AWS environment.

## Setting up a Gateway

I set up an S3 Gateway, which is is a type of endpoint used specifically for Amazon S3 and DynamoDB (DynamoDB is an AWS database service).

Gateways work by simply adding a route to your VPC route table that directs traffic bound for S3 or DynamoDB to head straight for the Gateway instead of the internet.

### What are endpoints?

An endpoint is in AWS is a service that allows private connections between your VPC and other AWS services without needing the traffic to go over the internet , because some AWS services that's not created inside a VPC for Availability reasons so endpoints it's the solution

![Setting up a Gateway](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_09bcaa8a)

## Bucket policies

A bucket policy is a type of IAM policy designed for setting access permissions to an S3 bucket. Using bucket policies, you get to decide who can access the bucket and what actions they can perform with it.

My bucket policy will deny  all actions (s3:\*) on my S3 bucket and its objects to everyone (Principal: "\*")... unless the access is from the VPC endpoint with the ID defined in aws:sourceVpce.\
In other words, only traffic coming from my VPC endpoint can get any access to your my S3 bucket!

![Bucket policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_7316a13d)

## Bucket policies

Right after saving my bucket policy, my S3 bucket page showed 'denied access' warnings. This was because we set the policy to deny all actions unless they come from my  VPC endpoint. This means any attempt to access my bucket from other sources, including the AWS Management Console, is blocked!

I also had to update my route table because the traffic that goes to VPC endpoint must be updating the route table to route the traffic throw the VPC endpoint

![Bucket policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_4ec7821f)

## Route table updates

To update my route table, I had  to the nextWork-subent and  i check the route table for the vpc endpoint , after that i go to the VPC enpoint route table after that i create

After updating my public subnet's route table, my terminal could return the files that stored in the S3 bucket , this approach of limiting access to S3 is very helpfull to avoid connection with public internet

![Route table updates](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_d116818e)

## Endpoint policies

An endpoint policy is it's set of permissions that allowed or denied several connections to and from A VPC

I updated my endpoint's policy by go endpoint and navigate to policy editor and updated from \`from allow to deny\` I could see the effect of this right away, because when i run this cmd \`aws s3 ls s3://nextwork-devops-cicd-tahiop\` it reject the request because endpoint policy deny all the requests to our VPC

![Endpoint policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/749fab76-0a0b-5822-9b31-c7863050c9bd_3e1e79a3)
