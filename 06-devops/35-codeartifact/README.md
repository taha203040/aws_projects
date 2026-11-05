## Introducing Today's Project!

In this project, I will demonstrate how to use CodeArtifact I'm doing this project to learn the devops skills with learing another service in AWS

### ✍️ What are we doing in this step and why?

To set up for this project, I am launching an EC2 instance because it provide us the compute resources we need to host our application and build our CI/CD pipeline.

### ✍️ What are you doing in this step and why?

In this step, I will Use the terminal to connect to your EC2 instance via SSH. and install Java and Maven on the EC2 instance also to generate a basic Java web app.\
Connect VS Code to your EC2 instance using the Remote - SSH extension in order to create a full CI/CD pipeline

### ✍️ What are yu doing in this step and why?

In this step, I will install Git on my EC2 instance, set up a GitHub repository, and connect my local web app to the GitHub repository because I want to manage my code with Git and store it on GitHub for version control and collaboration.

### ✍️ Why are you setting up CodeArtifact repository in this project?

In this step, I will setup CodeArtifact repo because CodeArtifact  improves the availability and seurity of our web app! its'used to store dependecies

### Key tools and concepts

Services I used were IAM (setting the policies and role for EC2 instance) and CodeArtifact that manage the dependency and stored them .Key concepts I learnt include authentication between EC2 and CodeArtifact using the IAM policies to shape the roles for EC2 t o use

### Project reflection

This project took me approximately 2 hours (skipping the setup EC2 instances and github and git setup).The most challenging part was config CodeArtifact and setup auth for EC2 with CodeArtifact to connecting each other correctly. It was most rewarding to learn this conspets it very good push into devops field

### ✅ Why did you do this project today?

I did this project today because i want improve the devops skills and complete the 6 days journey

This project is part three of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project on the day 4 and i will proud m self if i finnish this challenge

## CodeArtifact Repository

CodeArtifact is an AWS service that stores and manages software packages and dependencies.\
Engineering teams use artifact repositories because they provide a secure, central place to store, share, and manage software packages and versions.

A domain is like a folder that holds together multiple repos under the same project or under the same organization and they're helpful for setting up permission settings for multiple CodeArtifact repos in one go . Our domain is called nextwork-daily

A CodeArtifact repository can have an upstream repository, which means. a public source of packages that Maven can visit if they can't find it in our local CodeArtifact repo.Our repository's upstream repository is Maven Central Repo , shich is the largest Java repo  (and its extremely helpful  when building a Java web app).

![CodeArtifact Repository](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codeartifact-updated_n4o5p6q7)

### ✍️ What are we doing in this step?

In this step, We will try to connect to Maven and CodeArtifact . This is because Maven is our web app's package manager , and CodeArtifact is the repo that stores the packages that Maven is looking for . We're about to run into some permission errors becuase right now our EC2 instance  does not have  access to CodeArtifact

## CodeArtifact Security

### Issue

To access CodeArtifact, we need an authentication token that allows our EC2 instance to access CodeArtifact repo for 12 hours . We ran into an error when retrieving a token because our EC2 instance does not have the permission to access our AWS recources by default . This follows the principales of least priviledge.

### Resolution

To resolve the error with my security token, we setup on IAM Policy that grants access to CodeArtifact and then an IAM role that we can attach to our EC2 instance .This resolved the error because our EC2 instance now have access to request an authorization !

### ✍️ What are you doing in this step and why?

In this step, we will setup connection between CodeArtifact and our web app (Mavan) .To do this , we need to setup a setting.xml file - this file gives Maven the instructions for finding our CodeArtifact repo and using it to retrieve packages

It's a security best practice to use IAM roles because they grant temporary permissions to an EC2 instance without storing long-term AWS access keys, making access more secure and easier to manage.

## The JSON policy attached to my role

The JSON policy I set up grants access to CodeARtifact Specificaly , it gransts access to three key actions related to CodeArtifact - retrieving an authorization token , finding repo(endpoints) , viewing the packages inside the repo

### ✍️ What are we doing in this step?

In this step, we are setting up rool that uses the policy that we just created . Then , we apply that role to our EC2 instance

![The JSON policy attached to my role](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codeartifact-updated_23rp7q8r9)

## Maven and CodeArtifact

### To test the connection between Maven and CodeArtifact, I compiled my web app using settings.xml

The settings.xml file configures Maven to use CodeArtifact repo . It supplies Maven with the name and authentication token to get access to CodeArtifact repo , and also sets up profile section in case we ever have multiple repos and we need tell maven when to use which one

Compiling means translating the human code (our web app) into something that machine can run . Maven is our compiler , so we asked Maven to compile our web app code . While it's compiling . Maven will need put together all the packages that our app needs in order to run. To retrieve those packages . Maven visits CodeArtifact ( who will say it doesn't have  any packages available) . Then Maven would go upstream to request the exact same packags from teh upstream repo . (Maven Central) and once Maven has those packages , store local copies in CodeArtifact

![Maven and CodeArtifact](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codeartifact-updated_c17eace8)

## Verify Connection

After compiling, we checked out the CodeArtifact repo and we noticed 4 pages of packages inside ! This tell up that we're success store our web app's  dependency in CodeArtifact repo

![Verify Connection](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codeartifact-updated_1d79e699)
