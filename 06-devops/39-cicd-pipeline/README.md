<picture><source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" /><img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" /></picture>

# Build a CI/CD Pipeline with AWS

**Project Link:** [View Project](https://nextwork.ai/projects/7ade5e2f-0020-55fb-9bba-abede6ce1de9)

**Author:** Rabia Taha

---

## Introducing Today's Project!

In this project, I will demonstrate how implement the CodePipeline  I'm doing this project to learn how to automate servrel process in software development

### ✍️ What are you doing in this step and why?

In this step, I will setup CI/CD Pipeline for our app , because it's perfect way to automate bunch of manual steps in app developmnet

### Key tools and concepts

Services I used were Codepipelines, Key concepts I learnt include Amazon S3 Amazon EC2 AWS IAM GitHub , how to combine all of these in one single service called Codepipline that automate a lot of steps in one single workflow that runs all these sequencly

### Project reflection

This project took me approximately 90 mins including a debug  The most challenging part was setup the stages and configure them correctly It was most rewarding to learn Codepipeline (saves a lot of time)

I chose to do this project today because to complete this series of AWS Devops Something that would make learning with NextWork even better is simplicity and clear instructions

### ⭐️ Well done on completing the 7 Day DevOps challenge!

Are there any other projects or series you'd like to see at NextWork? What would make learning an even better experience for you? \
I would see here the Terraform projects its so rewards to learn it , and the clear insturctions make learning an even better experience for me

## Starting a CI/CD Pipeline

AWS CodePipeline is a sequence of automated instructions or workflow it very usefull  in software development , it can automate bunch of commands and instructions once we edit the code , it can automate the changes through the tests , builds and deployment stage , and it ensure the changes are reliable and happend automatically avoiding the human mistakes and errors when we handle the development software manually and its save time

CodePipeline offers different execution modes based on speed , independence and the sequence I chose Supreseded means mode, if a new pipeline execution is triggered while another execution is already in progress, the newer execution will immediately take over and cancel the older one. other options include Quereed and Parallel (it does'nt fit in our case)

A service role gets created automatically during setup so he performs actions on behalf us. It's like giving CodePipeline permission to access other AWS resources it needs to run your pipeline, such as S3 buckets for storing artifacts or CodeBuild for building your code.

### ✍️ What are you doing in this step and why?

In this step, I will config  GitHub repository , CodeBuild , CodeDeploy and a webhook to catch the chages and run the pipeline

![Starting a CI/CD Pipeline](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codepipeline-updated_gdnhtm)

## CI/CD Stages

The three stages I've set up in my CI/CD pipeline are Sourcing , Building , Deploying While setting up each part, I learnt about how the workflow work , and sequence of running the pipeline start with Sourcing which get the the source Code from github after that Building the app from the source code after that Deploying and app into the cloud

CodePipeline organizes the three stages into one single workflow automating the Stages sequencelly .In each stage, you can see more details on the commits  that catched that Triggers  Pipeline workflow to start , and the artifact (result's build) where it stored ...

### ✍️ What are you doing in this step and why?

In this step, I will test the Pipeline by implementing changes in the codebase  to see if the workflow works correctly

![CI/CD Stages](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codepipeline-updated_fbdetger)

## Source Stage

In the Source stage, the default branch tells CodePipeline exactlly which version of our code we want to use in this workflow  . In production env , you van have many branch for many versions of code

The source stage is also where you enable webhook events, which whenver we push a change , the webhook catch the changes and tell theCodepipeline to start the pipeline workflow

![Source Stage](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codepipeline-updated_sergt)

## Build Stage

The Build stage sets up the build provider and the project name with Service role  (FROM IAM ) I configured the Build type to Single Build (trigger one build) The input artifact for the build stage is Source Artifact

![Build Stage](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codepipeline-updated_j1k2l3m4)

## Deploy Stage

The Deploy stage is where our web-app get ship into production and where we can see it in real time I configured the deploy provider and 'DeploymentGroupName'  and 'Configure automatic rollback on stage failure as true' (if something goes bad we get a rollback to previous version

### ✍️ What are you doing in this step and why?

In this step, I will finnish creating my pipeline and start it up and connect Github , CodeBuild , CodeDeploy

![Deploy Stage](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codepipeline-updated_m4n5o6p7)

## Success!

Since my CI/CD pipeline gets triggered by code changesI tested my pipeline by editing my code automaticly the pipeline catch the changes and starts the workflow to implement the changs without handy stuff

The moment I pushed the code change the pipeline catch the new changes  and starts the workflow The commit message under each stage reflects to the change id that triggers the pipeline to start

Once my pipeline executed successfully, I checked the Public IPv4 DNS and copy it and navigate throw it and i see the changes live in our webapp !!!!

![Success!](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-codepipeline-updated_e1f2g3h4)
