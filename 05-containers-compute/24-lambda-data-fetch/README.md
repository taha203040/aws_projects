## Introducing Today's Project!

In this project, I will demonstrate fetching data with AWS lambda using the DynamoDb as Database four our project . I'm doing this project to learn more about Three-Tier

### ✍️ What are we doing in this step?

In this step, I will setup DynamoDb as fondation for our project

### Tools and concepts

The services I used were AWS Lambda, Amazon DynamoDB, AWS Identity and Access Management (IAM), Amazon S3, Amazon CloudFront, and Amazon API Gateway. Key concepts I learned include serverless computing, DynamoDB tables and partition keys, the AWS SDK, Lambda execution roles, IAM permissions, the principle of least privilege, and three-tier architecture. I also learned how to integrate the presentation tier (S3 and CloudFront), logic tier (API Gateway and Lambda), and data tier (DynamoDB) to build a complete web application.

### Project reflection

This project took me approximately 1 hour . The most challenging part was debug the error and solve it by attach the right policy to Lambda .It was most rewarding to learn more about Three-tier

I chose to do this project today because I wanted to gain hands-on experience with AWS Lambda and DynamoDB and learn how to retrieve data securely using IAM permissions.

Something that would make learning with NextWork even better is providing more practical troubleshooting exercises and real-world scenarios to help learners develop their problem-solving skills.

## Project Setup

To set up my project, I created a database table using Amazon DynamoDB. The partition key is \`userId\`, which uniquely identifies each user's partition key value and allows DynamoDB to efficiently store and retrieve items based on their user ID.

### ✍️ What are we doing in this step?

In this step, I will add a table Items as sample user to my UserData table

DynamoDB is schemaless, which means that items in the same table can have different attributes, without requiring a fixed structure for every item. However, each item must include the table's required primary key attributes, such as \`userId\` in my project.

### ✍️ What are we doing in this step?

In this step, I will setup a Lambda function that used to retrieve data correclty from DynamoDb whenever we call the function

![Project Setup](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/465096ce-f136-53fb-8a99-ebab7c406cd9_a112c3d5)

### AWS Lambda

AWS Lambda is a serverless compute service that runs code without requiring me to manage servers. I'm using Lambda in this project to retrieve user data from DynamoDB based on the provided \`userId\` and return the results to the API caller.

## AWS Lambda Function

My Lambda function has an execution role, which defines the AWS resources it can access. By default, the role grants permission to write logs to Amazon CloudWatch, but I also need to grant it permission to read data from my DynamoDB table.

### ✍️ What are we doing in this step?

In this step, I will implement Lmbda function logic as step in this project

My Lambda function will retrieve a user's data from the \`UserData\` DynamoDB table using the provided \`userId\`. It uses the AWS SDK to query the table, returns the user information if a matching item is found, and logs the result or any errors to CloudWatch.

The AWS SDK is a collection of libraries that allows developers to interact with AWS services programmatically. My code uses the AWS SDK for JavaScript to connect to DynamoDB, retrieve user data based on \`userId\`, and handle the response.

![AWS Lambda Function](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/465096ce-f136-53fb-8a99-ebab7c406cd9_a1b2c3d5)

### ✍️ What are we doing in this step?

In this step, I will test the Lambda function and observing the results of the test

## Function Testing

To test whether my Lambda function works, I opened the \*\*Test\*\* tab in the AWS Lambda console and created a test event using JSON: \`{"userId":"1"}\`. If the test is successful, I'd see the user's data returned from DynamoDB, including their \`userId\`, \`name\`, and \`email\`.

The test displayed a 'success' status, but the function encountered an error because we hadn't granted the Lambda execution role permission to access DynamoDB. As a result, the function couldn't retrieve the user's data from the table.

### ✍️ What are we doing in this step?

In this step, I will Grant Dynamo DynamoDB Access to Lambda in order to solve the permission's problem

### 🤔 Which policy should you pick?

i think i use AWSLambdaInvocation-DynamoDB\
AWS managed

![Function Testing](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/465096ce-f136-53fb-8a99-ebab7c406cd9_u1v2w3x4)

## Function Permissions

To resolve the AccessDenied error we must review the error message again to specify the right policy to attach it to Lambda

There were four DynamoDB permission policies I could choose from, but I didn't pick \`AmazonDynamoDBFullAccess\` because it grants unnecessary permissions, \`AWSLambdaDynamoDBExecutionRole\` because it is designed for processing DynamoDB Streams, or \`AWSLambdaInvocation-DynamoDB\` because it is used to trigger Lambda functions in response to DynamoDB Stream events. Instead, I chose \`AmazonDynamoDBReadOnlyAccess\` because my function only needs to retrieve user data.

I also didn't pick \`AmazonDynamoDBFullAccess\` because it grants more permissions than my Lambda function needs, including the ability to modify and delete data. \`AmazonDynamoDBReadOnlyAccess\` was the right choice because my function only needs to retrieve user data from DynamoDB, following the principle of least privilege.

### ✍️ What are we doing in this step?

In this step, I will Re-run the Lambda function test to validate that our Lambda function is work !

![Function Permissions](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/465096ce-f136-53fb-8a99-ebab7c406cd9_3ethryj2)

## Final Testing and Reflection

To validate my new permission settings, I ran the test again. This time, the function successfully returned the data stored in DynamoDB because I had granted the Lambda execution role the necessary read permissions.\
'{\
  "email": "test@example.com",\
  "name": "Test User",\
  "userId": "1"\
}\
\`

Web apps are a popular use case for Lambda and DynamoDB. For example, I could build a user management application where API Gateway receives HTTP requests, Lambda processes them, and DynamoDB stores and retrieves user information.

![Final Testing and Reflection](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/465096ce-f136-53fb-8a99-ebab7c406cd9_p9thryj2)
