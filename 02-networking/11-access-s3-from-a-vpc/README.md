<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" />
  <img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" />
</picture>

# Access S3 from a VPC

**Project Link:** [View Project](https://nextwork.ai/projects/36d7dc8f-3a9f-51ff-91ae-662077ea9920)

**Author:** Rabia Taha

![Screenshot](https://nextwork.ai/covers/screenshot_340dbb143e9c459a1addc6694a0bfba5.png)

![Screenshot](https://nextwork.ai/covers/screenshot_c03cfeda2a8e0874a3f28540ca07c7e8.png)

---

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate how to access S3 from a VPC. I'm doing this project to learn more about the VPC world.

### What is Amazon VPC?

Amazon VPC is a logically isolated virtual network in AWS where I can deploy and control my cloud resources.
It is useful because it allows me to control networking, including IP addresses, subnets, routing, and access to my resources.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create an EC2 instance and an S3 bucket, then used the EC2 instance to upload data and get access into S3 from within the VPC.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was using EC2 to upload files from it.

### This project took me...

This project took me 30 minutes.

## In the First Part of My Project...

### Step 1 - Architecture Set Up

In this step, I will set up a VPC and an EC2 instance in order to set up the foundations for this project. This gives me an isolated network and a compute resource inside it to work from.

### Step 2 - Connect to My EC2 Instance

In this step, I will connect to my EC2 instance directly using the AWS console, without a complex method. This uses EC2 Instance Connect, so AWS handles the connection configuration behind the scenes.

### Step 3 - Set Up Access Keys

In this step, I will create access keys in order to give my EC2 instance access to interact with S3. These credentials let the AWS CLI running on the instance authenticate to AWS.

## Architecture Set Up

I started my project by launching a VPC and an EC2 instance and attaching it to the VPC that we created. Notice that we don't select an existing security group and just create a simple one with the name `SG - NextWork VPC Project`.

I also set up an S3 bucket and uploaded two files into it.

![Architecture set up](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_4334d777)

## Running CLI Commands

AWS CLI, or AWS Command Line Interface, allows me to run commands directly from the terminal to interact with AWS resources, making it faster and easier to automate tasks. I have access to the AWS CLI because I want to access S3 from the EC2 instance.

The second command I ran was `aws configure`. This command is used to configure the AWS Access Key ID in order to get access to our resources from the EC2 instance.

![Running CLI commands](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_e7fa8776)

## Access Keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured it by setting up the Access Key ID, Secret Access Key, and Region name. We don't specify the output format and leave it as it is (the default is JSON).

Access keys are credentials for my applications and other servers to log into AWS and talk to your AWS services and resources.

A secret access key is similar to a password that is paired with an Access Key ID. Both are required to authenticate with the AWS API and access AWS services according to the permissions assigned to the associated IAM identity.

### Best Practice

Although I'm using access keys in this project, a best-practice alternative is to use IAM roles or temporary credentials, which provide short-lived access without requiring long-term access keys to be stored or managed.

## In the Second Part of My Project...

### Step 4 - Set Up an S3 Bucket

In this step, I will launch an S3 bucket for our project. This gives me a storage location that the EC2 instance will later read from and write to.

### Step 5 - Connect to My S3 Bucket

In this step, I will connect the EC2 instance that was launched in the VPC to interact with the S3 bucket that we created before. This tests that the credentials and network path are set up correctly.

## Connecting to My S3 Bucket

The first command I ran was `aws s3 ls`. When I ran it, it showed that I need required credentials in order to run it correctly. This command is used to show the list of S3 buckets in my account.

When I ran the command `aws s3 ls` again, the terminal responded with lines of my S3 buckets. This indicated that we successfully configured the credentials in the EC2 instance.

![Connecting to my S3 bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_4334d778)

## Connecting to My S3 Bucket

Another CLI command I ran was `aws s3 ls s3://nextwork-vpc-project-[your unique id]`, which returned all the files stored in the bucket.

![Connecting to my S3 bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_4334d779)

## Uploading Objects to S3

To upload a new file to my bucket, I first ran the command `sudo touch /tmp/test.txt`. This command creates a file named `test.txt` in the `/tmp` directory.

The second command I ran was `aws s3 cp /tmp/test.txt s3://nextwork-vpc-project-[uniquename]`. This command uploads the file into the S3 bucket.

The third command I ran was `aws s3 ls s3://nextwork-vpc-project-ahmdrb-vwrl`, which validated that our file was successfully uploaded to the S3 bucket.

![Uploading objects to S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/36d7dc8f-3a9f-51ff-91ae-662077ea9920_3e1e79a2)
