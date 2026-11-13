## Introducing Today's Project!

### Project Goal
In today's project, I will Query Data with DynamoDb

### Setting Up DynamoDB Tables
In this step, I am going to Set Up DynamoDB Tables with AWS CLI

### Loading Data into Tables
In this step, I am going to Load Data into table that we created before

### Running Basic Queries
In this step, I am going to Run basick queries on our DynamoDB tables , and find data using partition and sort keys

### Table Display
I think this table displays  a long text as id

### What is Amazon DynamoDB?
Amazon DynamoDB is a fully managed NoSQL database service that provides fast and predictable performance with seamless scalability. It is useful for applications that need to handle large amounts of data and traffic without managing database servers. In today's project, I used Amazon DynamoDB to store and manage application data, create relationships between related items, and perform transactions using the `aws dynamodb transact-write-items` command.

### How I Used Amazon DynamoDB
In today's project, I used Amazon DynamoDB to run queries and learn more about using the CLI commandes with AWS Cloudshell

### Surprising Discovery
One thing I didn't expect in this project is how the queries works and how it so sensative

### Project Duration
This project took me 45 mins

## Querying DynamoDB Tables

Partition keys are like tags that DynamoDB uses to organise the table's data. When you search for an item in your table, DynamoDB will need its partition key!

A sort key is a secondary key used to filter your query results again! Sort keys work after the partition key i.e. you still have to use the partition key to split up your data first, and then the sort key partitions your data again.

![Querying DynamoDB Tables](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/0001cf4c-8256-52ae-b09c-6e99ed36462f_d105b0b0)

## Limits of Using DynamoDB

I ran into an error when I queried for PostedBy as filter with value `User Abdulrahman` This was because we must use the Id (Partition key) when we query items , as regarding the Data modelling

Insights we could extract from our Comment table includes cemmentDateTime postedby ...  Insights we can't easily extract from the Comment table includes the postedBy because the data modeling is so important to regard it

### Running Queries with AWS CLI
In this step, I am going to run queries with AWS CLI !! (to save time :)

### Expected Query Results
I think this query will return the data based on the query that we run on the CLI

![Limits of Using DynamoDB](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/0001cf4c-8256-52ae-b09c-6e99ed36462f_cb3e260c)

## Running Queries with CLI

A query I ran in CloudShell was about retrieve results with strong consistent read This query will read the latest data from DynamoDB , in the opposite if  we retrieve with eventual consistent it return not the latest data

Query options I could add to my query are table name key and --consistent-read for latest data retrieving

### Handling Related Data
In this step, I am going to Handle related data across DynamoDB tables.\
Update two tables in a single AWS CLI command.

![Running Queries with CLI](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/0001cf4c-8256-52ae-b09c-6e99ed36462f_18379f04)

### Table Relationships
My DynamoDB tables are related to each other because one table can store a key that references an item in another table. However, updating an item in one table does **not automatically update** the related item in another table. If I need changes to be reflected across both tables, the application must explicitly update both items.

![Running Queries with CLI](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/0001cf4c-8256-52ae-b09c-6e99ed36462f_733d9399)

## Transactions

A transaction is a group of related operations that are treated as a single unit of work, where either all operations succeed or all of them fail. This helps maintain data consistency and prevents partial updates when an error occurs.

I ran a transaction using the `aws dynamodb transact-write-items` command. This transaction did two things: first, it added a new comment to the **Comment** table, and second, it updated the **Forum** table by increasing the number of comments for the **Events** forum by one. Both operations were performed as part of a single transaction, ensuring that either both changes succeed or neither change is applied.

![Transactions](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/0001cf4c-8256-52ae-b09c-6e99ed36462f_2f65f83e)
