![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/921d7b78-ffa4-5e41-a5b5-aed76c78efad_1709b26b)

## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate connecting a Wbe app with Aurora , i am doing this project in order to level up the Cloud computing skils

### ✍️ What are we doing in this step?

In this step, I will login to my IAM user in order to secure the root app from bad behaviors

### ✍️ What are we doing in this step?

In this step, I will lunch an EC2 instance as fundation for this project

### ✍️ What are we doing in this step?

In this step, I will create an Aurora Create an Aurora MySQL Database for my web app project to store the data on SQL

### ✍️ What are you doing in this step?

In this step, i will create a web app for this project

### What is Amazon Aurora?

Amazon Aurora is  relational database and why it is useful because it create multiple types of Databases with ease and rich configuration

### How I used Amazon Aurora in this project

In today's project, I used Amazon Aurora to connect my web app with Aurora with direct DB updates data!!

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was seeing the Data in Mysql db using CLI

### This project took me...

the project takes me 30mins ( i keep the previous setup!! wit stoping the computing resources)

### ❤️ Thanks for doing this project!

I chose to do this project today because rich platform with large types of projects

## Creating a Web App

![Creating a Web App](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/921d7b78-ffa4-5e41-a5b5-aed76c78efad_b7999168)

To connect to my EC2 instance, I used to go to the terminal and run this command \
\`ssh -i ./NextWork\_key\_pair.pem ec2-user@\[your-ecc2 instance\]\`\
before we run this cmd we run first \`chmod 400 NextWorkAuroraApp.pem\` in order to protect the Key from bad uses

To help me create my web app, I first update the instance software files by running \`sudo dnf update -y\` , second command is \`sudo dnf install -y httpd php php-mysqli mariadb105\` is used to install these packages after that i start the server by runing \`sudo systemctl start httpd\`

### ✍️ What are we doing in this step?

In this step, I will make our web app Cool by creating a new folder nd file in my EC2 instance to connect to our Aurora database , second thing is add a PHP schript to make a more user-friendly web page for my app

## Connecting my Web App to Aurora

I set up my EC2 instance's connection details to my database by creating a \`dbinfo.inc\` file and  pasting in a contain  defining DB\_SERVER ,DB\_USERNAME, DB\_PASSWORD ,DB\_DATABAS

![Connecting my Web App to Aurora](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/921d7b78-ffa4-5e41-a5b5-aed76c78efad_1709b25b)

## My Web App Upgrade

Next, I upgraded my web app by creating a new file called Samplepge.php and paste a code that contain the interface of the web app , and it works!!!

### ✍️ What are we doing in this step?

In this step, I will test my new web app in the browser and checkt if that correctly updating my aurora database by using MySQL CLI

![My Web App Upgrade](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/921d7b78-ffa4-5e41-a5b5-aed76c78efad_2709b25b)

## Testing my Web App

To make sure my web app was working correctly, I connect to my CLI and run \`mysql ....\` command to connect to Aurora , after that i run these commands \
\`SHOW DATABASES;\
USE sample;\
SHOW TABLES;\
DESCRIBE EMPLOYEES;\
SELECT \* FROM EMPLOYEES;\
\` and i see the tables of the Emoloyes by the end !!!

![Testing my Web App](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/921d7b78-ffa4-5e41-a5b5-aed76c78efad_1409z22b)
