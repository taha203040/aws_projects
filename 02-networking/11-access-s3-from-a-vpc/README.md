## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to access into the VPC with S3 I'm doing this project to learn about more VPC world

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources.\
It is useful because it allows me to control networking, including IP addresses, subnets, routing, and access to my resources

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a EC2 and S3 and use EC2 to upload data from it and get access into S3 using the EC2 instance

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was using EC2 to upload files from it

### This project took me...

This project took me 30 mins

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will step a VPC and EC2 in order to setup the foundations fo this project

### Step 2 - Connect to my EC2 instance

In this step, I will connect to my EC2 instance directly using AWS console , without complex method

### Step 3 - Set up access keys

In this step, I will create a access keys in order to give access to my EC2 instance to intract with S3

## Architecture set up

I started my project by launching VPC and EC2 instance and attach it into the VPC that we created , notice that we don't select Exist security group and just create simple one with name \`SG - NextWork VPC Project\`

I also set up S3 bucket and i upload two files in it

![Architecture set up](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_4334d777)

## Running CLI commands

AWS CLI, or AWS Command Line Interface allows me to run commands directly from the terminal to interact with AWS resources, making it faster and easier to automate tasks. I have access to the AWS CLI because  i want to access to s3 from EC2 instance

The second command I ran was \` aws configure\` This command is used to config the AWS Access key ID in order to get access to our resources from EC2 instance

![Running CLI commands](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_e7fa8776)

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured it by setup the Access Key ID and Secret Access ID and the Region name , we don't specify the format and leave as it is(the default is JSON)

Access keys are credentials for my applications and other servers to log into AWS and talk to your AWS services/resources.

A secret access key is similar to a password that is paired with an Access Key ID. Both are required to authenticate with the AWS API and access AWS services according to the permissions assigned to the associated IAM identity.

### Best practice

Although I'm using access keys in this project, a best-practice alternative is to use IAM roles or temporary credentials, which provide short-lived access without requiring long-term access keys to be stored or managed.

## In the second part of my project...

### Step 4 - Set up an S3 bucket

In this step, I will lunch a S3 bucket for our project

### Step 5 - Connecting to my S3 bucket

In this step, I will connect the EC2 instance that lunch in VPCs to intract with the S3 that we created before

## Connecting to my S3 bucket

The first command I ran was \`aws s3 ls \` when i run it  , it show that i need a required credentials in order to run it correctly .This command is used to show the the list of S3 buckets in my account

When I ran the command \`aws s3 ls\` again, the terminal responded with  lines of  my S3 buckets This indicated that we successfully config the credentials in the EC2 instsance

![Connecting to my S3 bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_4334d778)

## Connecting to my S3 bucket

Another CLI command I ran was \`aws s3 ls s3://nextwork-vpc-project-\[your unique id\]\` which returned the all the files that stored in the bucket

![Connecting to my S3 bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_4334d779)

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command \`sudo touch /tmp/test.txt\` This command creates a file in the directory test.txt

The second command I ran was aws \`s3 cp /tmp/test.txt s3://nextwork-vpc-project-\[uniquename\[ \`This command will upload the file into the S3 bucket

The third command I ran was\` aws s3 ls s3://nextwork-vpc-project-ahmdrb-vwrl \` which validated that our file is successfully upload it in the S3 bucket

![Uploading objects to S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_3e1e79a2)
