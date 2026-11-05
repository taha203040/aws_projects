## Introducing Today's Project!

In this project, I will demonstrate how to use APIs with Lambda + API Gateway .I'm doing this project to learn about more deeply in application infra world

### ✍️ What are we doing in this step?

In this step, I will create a serverless Lambda function as fondation of our project

### Tools and concepts

Services I used were Amazon API Gateway, AWS Lambda, and Amazon DynamoDB. Key concepts I learnt include Lambda functions, REST APIs, API resources and methods, deployment stages, and how API Gateway routes requests to Lambda functions to retrieve data from a database.

### Project reflection

This project took me approximately 45 min The most challenging part was implementing the lambda and the API gateway It was most rewarding to learn about lambda function as stateless way run apps

I chose to do this project today because I wanted to gain practical experience with AWS and understand how to deliver website content securely and efficiently using S3 and CloudFront.

Something that would make learning with NextWork even better is providing more troubleshooting exercises and real-world scenarios to help learners understand and solve common AWS errors independently.

## Lambda functions

AWS Lambda is a  service that lets us run code without needing to manage any computers/servers - Lambda will manage them for us .  the way it works it's easy when the code is triggerd it runs automatically I'm using Lambda in this project to use with API gateway and serverless application and retrieve users

The code I added to my function will retrieves data from DynamoDB table . it's retrieve the user basd on a 'userId' and return taht dataif  does not exist it return an error

### ✍️ What are we doing in this step?

In this step, I will config a new API in API gateway that lets the requests to reach Lambda easly

![Lambda functions](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_a1b2c3d5)

## API Gateway

APIs are interfaces that allow different software applications to communicate and exchange data. There are different types of APIs, like REST APIs, GraphQL APIs, and WebSocket APIs. My API is a \*\*REST API\*\*, which uses HTTP methods such as GET, POST, PUT, and DELETE to interact with resources.

Amazon API Gateway is a service I use in this project to route incoming HTTP requests to the appropriate endpoints and invoke the corresponding AWS Lambda functions.

When a user makes a request through API Gateway, it routes the request to the appropriate Lambda function. Lambda executes the code, processes the request, and returns a response to API Gateway, which sends it back to the user.

![API Gateway](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_m3n4o5p6)

### ✍️ What are we doing in this step?

In this step, I will create API resources that define the endpoints and structure of my API to meet the application's requirements.

## API Resources and Methods

An API is made up of resources, which represent the data or entities that an application exposes. Each resource can have different HTTP methods, such as GET, POST, PUT, and DELETE, to retrieve, create, update, or delete data.

![API Resources and Methods](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_u1v2w3x4)

### ✍️ What are we doing in this step?

In this step, I will setup a get method for users resources , and connecting it to Lambda function!!

Each resource consists of methods, which define the HTTP actions clients can perform, such as GET to retrieve data, POST to create data, PUT to update data, and DELETE to remove data. Each method can be connected to a Lambda function to handle the request.

I created a \`/users\` resource and connected it to a Lambda function that retrieves data from the database and returns it to the client.

### ✍️ What are we doing in this step?

In this step, I will our API to a new stage in order to deploy it correclty

![API Resources and Methods](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_c9d0e1f2)

## API Deployment

When you deploy an API, you deploy it to a specific stage. A stage is a named environment that represents a specific version of your API. I deployed my API to the \`prod\` stage, which represents the production environment where the API is intended to serve real users.

To visit my API, I used the Invoke URL generated after deployment. The API displayed an error because I hadn't created the DynamoDB table required by the Lambda function to retrieve data.

![API Deployment](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_3ethryj2)

## API Documentation

For my project's extension, I am writing API documentation to make the API easier for developers to understand, test, and integrate with their applications. I can do this using tools like Swagger (OpenAPI).

API documentation is a detailed description of an API's functionality, including its endpoints (e.g., \`/users\`), HTTP methods (e.g., GET), parameters (e.g., \`userId\`), and responses (e.g., success messages and error codes). Good documentation helps developers use the API correctly and efficiently.

Once I prepare my documentation, I can publish it to the \`prod\` stage. I have to publish my API to a specific stage because each stage represents a deployment environment and provides a URL through which clients can access the API.

My published and downloaded documentation showed me the API's metadata, including its title, version, base URL, resources such as \`/users\`, and supported methods like GET. It also included automatically generated details that help developers understand the API's structure and how to interact with its endpoints.

![API Documentation](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_z9a0b1c2)
