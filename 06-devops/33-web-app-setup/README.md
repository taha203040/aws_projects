## Introducing Today's Project!

In this project, I will demonstrate how to lunch an app in aws , and  I'm doing this project to learn setup IAM user and login with it and lunch EC2 regarding the best practises to achive the application working well

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project tommorow to finish it and improve my self well

I did this project to add devops to my skills and it deserve the time that i spend it to do the project

### Key tools and concepts

Services I used were EC2. Key concepts I learnt include \
setup SSH connection from creating keypair and make connection via terminal and setup vscode remote ssh connection so we can edit and navigate throw the folders inside the EC2 easly

### Project reflection

This project took me approximately 2hours  The most challenging part was run the cmds of maven and java , and setup connection via SSH .It was most rewarding to use the VScode extention that make it easly to update the code using the extention

One thing I didn't expect in this project was using the vscode remote SSH extention

## Launching an EC2 instance

### What I did in this step

In this step, I will lunch EC2 instance because its the machine that located in the cloud that provide the ability to run my application without complex configuration

I started this project by launching an EC2 instance because its the first step to run our app in the cloud

![Launching an EC2 instance](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_7852fbf3)

### I also enabled SSH

SSH is Secure shell  I enabled SSH so that we can make secure connection with this protocol for only authorized users can access to the remote servers like EC2 its also a type of traffic data back and forth with our EC2 , and for best practise we make sure that only allowed SSH traffic from our IP address for security

### Key pairs

A key pair is mechanism to for us to connect and got access to our instance in the cloude that we create a key-pair for the EC2 that  we lunsh it

### Downloaded key pair file

Once I set up my key pair, AWS automatically downloaded in computer and save it in safe place and be carefull to share it to someone

## Set up VS Code

### What I did in this step

In this step, I will install vs code for edit the code and make terminal commands  and update the permission settings of our private key

### What is VS Code?

VS Code is a tool that allow to edit and update codes and it have a lot of tools that help us develop our app without problems

I installed VS Code to update edit and develop the code and setup permission and SSH connection ,  throw the terminal

![Set up VS Code](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_53d05e68)

## My first terminal commands

A terminal is command line interface for running a jobs in the computer with specified cmds, The first command I ran for this project is cd /destkop/devops

### Updating file permissions

I also updated my private key's permissions by run the command\
chmod 400 nextwork-keypair.pem \
this cmd givees ourserlves access to use this file so we can connect to and EC2 instance later

![My first terminal commands](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_9328ada1)

## SSH connection to EC2 instance

### What I did in this step

In this step, we going to try to connect our EC2 instance Once we've connected to the EC2 instance , we can start setting our web app inside

### Connecting to EC2

To connect to my EC2 instance, I ran the command\
ssh -i ./your-kaypair-path ec2-user@public IPv4 \
this cmd setup connection directly between our local pc to ec2 instance

### This command required an IPv4 address

A server's IPV4 DNS is public address that indetifiels where the server lives in the cloud . In our case  . am EC2 instance's IPv4 DNS is userfull inforamtio to give to our local machine so it make easy for our local machine to connect to the EC2 that we lunch

![SSH connection to EC2 instance](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_e3069dca)

## Maven & Java

### What I did in this step

In this step, we are going to install MAVEN and AMAZON Correttto 8 in our EC2 We 're doing this because both tools are iimportatant for setting up JAVA web app from scratch

### Why I'm using Maven

Apache Maven is package manager that help to organize java projects , and it have many benifits in system development

Maven is required in this project because we want to use its ability to spin web apps using temeplets . We're about to setup our Java web app using the archetype

### Why I'm using Java

Java is a programming laguage that we using it to devleop a web app , because its very popular in system dev

Java is required in this project because its lays of the foundation of the writing our web app code and the maven needs java to in order to work with the web app code

## Create the Application

### What I did in this step

In this step, we will  generate a web app inside our EC2 instance , using maven and java

### Creating the Java web app

I generated a Java web app using the command: \
'mvn archetype:generate -DgroupId=com.nextwork.app -DartifactId=nextwork-web-project -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false'\
 This cmd tells Maven to generate a web app using an existing template that it has . it also tells Maven t ocall the generated web app project 'nextwork-webapp-project'

### ✍️ Can you see your Java web app?  (Your response to this won't be in your documentation)

Yes using given url

### Installing Remote - SSH

We installed Remote - SSH, which is extention in vscode , we installed to connect our vscode  (remote-ssh) to our EC2 via the  same cmd that we run it in the ec2 terminal

### SSH configuration details

Configuration details required to set up a remote connection include  \
Host , HostName(IPv4 public) , IdentityFile (location to pem key), User(ec2-user)

![Create the Application](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_2939cf01)

## Create the Application

### Exploring the project structure

Using VS Code's file explorer, we could see the files that in our ec2 instance and we can navigate , edit it from vscode directly

Two of the project folders created by Maven are src and webapp, each of them have different parts fo the web app . for example , the recours sub-folder store connection details , while the webapp subfolder store webapp files for the look and feel of the web app , src is the parent folder that contain all the source code of the wepapp

![Create the Application](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_45f91fd7)

## Using Remote - SSH

### What I did in this step

In this step, we're connecting vs code with our EC2 instace ! This is diffreent from jsut connecting the terminal

### Updating the web app

The index.jsp is a file that have the struct of web app interface so by edit it we can see the changes in the web app

I edited index.jsp by updating the content of the file by another custom code

![Using Remote - SSH](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_7a1de541)

## Using nano

### Additional improvements

In this secret mission, We will edit  the index.jsp using the terminal instand of an IDE

### Terminal vs IDE

An alternative to using IDEs is using nano or (vim)To edit index.jsp, I ran the command nano index.jsp to enter the file and start edit it

Compared to using an IDE, editing index.jsp in the terminal felt a little handly (using keyboard keys to change the postion of the cursor and saving and exiting the file) compare to the IDE. I'd be more likely to use an IDE if i had a lot of codes to update inside the folders that located in the EC2 or more conveniente interface

### Verifying my work

To verify my editing work in the terminal, I open the ssh remote in the vscode and check if the updates are applied/  It was possible to see my changes in VS Code right away because the window share the same connection with the ssh connection in the terminal

![Using nano](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-vscode_a3324ad41)
