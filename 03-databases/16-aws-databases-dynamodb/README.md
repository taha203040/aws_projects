## Introducing Today's Project!

### ✍️ What are we here to do today?

In today's project, I will be load data into Dynamo Db

### ✍️ What are we doing in this step?

In this step, I am going to  create my first DynamoDb as Foundation for my project

### What is Amazon DynamoDB?

Amazon DynamoDB is  useful for their speed and flexibility using the NoSQL  benifites over SQL Database

### How I used Amazon DynamoDB in this project

In today's project, I used Amazon DynamoDB to load data from console and CloudShell CLI (which very helpfull)

### One thing I didn't expect in this project was...

One thing I didn't expect in this project is loading data and manage tables from AWS CLI CloudShell

### This project took me...

This project took me 45 mins

## Create a DynamoDB table

DynamoDB tables organize data using items and attributes. An item is similar to a row in a relational database, while attributes are the individual pieces of data stored within each item. Each item is uniquely identified by a primary key.

### ✍️ What are we doing in this step?

In this step, I will interact with DynamoDb using AWS CloudShell , using the CLI i will run commands inside CloudShell to Create DynamoDB tables !!!!

An attribute is key for for an item stored in DynamoDB

![Create a DynamoDB table](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_a3cefee0)

## Read and Write Capacity

Read capacity units (RCUs) and write capacity units (WCUs) are first for RCUs are used to measure how many engines DynamoDB is using to operate , for WCUs  they give the DynamoDB tables the engines to edit/update/delete data!

Amazon DynamoDB's Free Tier covers  25GB of data storage, plus 25 Write and 25 Read Capacity Units (WCU, RCU). This is enough to handle 200M requests per month... all for free. I turned off auto scaling because Auto scaling can automatically adjust the database's performance (i.e. how fast it can return query results) based on real-time demand.

![Read and Write Capacity](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_ef47dd8f)

## Using CLI and CloudShell

AWS CloudShell is shell in AWS Management Console, which means it's a space forto run code! The awesome thing about AWS CloudShell is that it already has AWS CLI pre-installed.

AWS CLI is command Line Interface) is a software that lets you create, delete and update AWS resources with commands instead of clicking through your console.

I ran a CLI command in AWS CloudShell that created four new tables in AWS DynamoDB, each with specific attributes and settings.\
The four tables created are:\
ContentCatalog Table: This table has a numeric attribute called Id.\
Forum Table: This table has a partition key called Name.\
Post Table: This table has a partition key called ForumName and a sort key called Subject. We'll dive into sort keys soon!\
Comment Table: This table has a partition key called Id and a sort key called CommentDateTime.

### ✍️ What are we doing in this step?

In this step, I will Load some data into DynamoDB table,  after that i view and update theloaded data.

![Using CLI and CloudShell](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_81e0258b)

## Loading Data with CLI

I ran a CLI command in AWS CloudShell that fetch a folder and unzip it after that i run a command that send the data to DynamoDb to store it there and it works!!!

![Loading Data with CLI](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_791c600b)

## Observing Item Attributes

![Observing Item Attributes](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_b481c731)

I checked a ContentCatalog item, which had the following attributes \` id Authors ContentTypes , Difficulty, Price ,ProjectCategory , Published , Title , URL

I checked another ContentCatalog item, which had a different set of attributes from the ContentCatalog items which mean it's only effect it stays in the edited item table

![Observing Item Attributes](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_9078b333)

## Benefits of DynamoDB

A benefit of DynamoDB over relational databases is flexibility, because very item having their own unique set of attributes is a huge advantage when items in a table could look different from each other. For example, e-commerce sites and shopping carts need to store different types of products with different attributes in the same place.

Another benefit over relational databases is speed, because  DynamoDB tables can use partition keys to split up a table and quickly find the items they're looking for. Relational databases have to scan through the entire table to find data, which can slow down performance.

![Benefits of DynamoDB](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/8bd82466-f5ee-569e-9125-2c4c6ce7a07f_b481c730)

### ✍️ What do you think this table is displaying?

I think this table displays the items that we send it from Cloudshell to DynamoDB and it works!
