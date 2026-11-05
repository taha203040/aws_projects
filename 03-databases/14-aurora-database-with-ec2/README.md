## Introducing Today's Project!

### ✍️ What are we here to do today?

In this project, I will demonstrate using Aurora Database with EC2 instance

### ✍️ What are we doing in this step?

In this step, I will login with my IAM user in order to protect bad practices from my AWS Root account

### What is Amazon Aurora?

Amazon Aurora is  relational database and why it is useful because it create multiple types of Databases with ease and rich configuration

### How I used Amazon Aurora in this project

In today's project, I used Amazon Aurora to create a MySql Database in ease with friendly configuration that provides by the Aurora

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was setup the instance type of the Aurora RDS

### This project took me...

The project takes me 35 mins

### ❤️ Thanks for doing this project!

I chose to do this project today because rich platform with large types of projects

## In the first part of my project...

### Creating an Aurora Cluster

A relational database is type of database that organizes data into tables, which are collections of rows and columns. Kind of like a spreadhsheet! We call it "relational" because the rows relate to the columns and vice-versa.

Aurora is a good choice when  we needed something large-scale, with peak performance and uptime. This is because Aurora databases use clusters Ordinary relational databases, like MySQL and Oracle are more generic and cost-effective. They suit smaller databases and less demanding workloads.

![In the first part of my project...](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/cee72c3a-f285-55a6-8217-3cee4023a3bf_44443546)

## Halfway through I stopped!

I stopped creating my Aurora database because we need to lunch an EC2 instance for web-app, and in order to connect it to the Aurora RDS

### ✍️ What are we doing in this step?

In this step, I will lunch and EC2 instance for connect it to Aurora DB

### Features of my EC2 instance

I created a new key pair for my EC2 instance because we need it to secure connection to EC2 instance

When I created my EC2 instance, I took particular note of creating a SSH connection throw the EC2 using Key Pair key to secure the connection

### ✍️ What are we doing in this step?

In this step, I will lunch the Aurora DB and connect it to EC2 instance

![Halfway through I stopped!](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/cee72c3a-f285-55a6-8217-3cee4023a3bf_91b9fd1g)

## Then I could finish setting up my database

![Then I could finish setting up my database](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/cee72c3a-f285-55a6-8217-3cee4023a3bf_1fddb0b5)

Aurora Database uses clusters because it is a group of database copies that work together so our data is always available.\
Each cluster consists of a primary instance (where all write operations occur) and multiple read replicas as back-ups. If our database's primary instance fails, one of the replicas can be promoted to primary automatically.
