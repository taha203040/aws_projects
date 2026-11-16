<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" />
  <img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" />
</picture>

# APIs with Lambda + API Gateway

**Project Link:** [View Project](https://nextwork.ai/projects/2af91800-3f42-5fc1-b405-c5069180c0df)

**Author:** Rabia Taha

![Screenshot](https://nextwork.ai/covers/screenshot_ec7e99d00480579a43d58df428ef8556.png)

![Screenshot](https://nextwork.ai/covers/screenshot_253ce0cd744b897f6d4e66418c9e28c8.png)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use APIs with Lambda + API Gateway. I'm doing this project to learn more deeply about the application infrastructure world.

### Creating the Serverless Lambda Function

In this step, I will create a serverless Lambda function as the foundation of our project.

### Tools and Concepts

Services I used were Amazon API Gateway, AWS Lambda, and Amazon DynamoDB. Key concepts I learned include Lambda functions, REST APIs, API resources and methods, deployment stages, and how API Gateway routes requests to Lambda functions to retrieve data from a database.

### Project Reflection

This project took me approximately 45 minutes. The most challenging part was implementing the Lambda and the API Gateway. It was most rewarding to learn about Lambda functions as a stateless way to run apps.

I chose to do this project today because I wanted to gain practical experience with AWS and understand how to deliver website content securely and efficiently using S3 and CloudFront.

Something that would make learning with NextWork even better is providing more troubleshooting exercises and real-world scenarios to help learners understand and solve common AWS errors independently.

## Lambda Functions

AWS Lambda is a service that lets us run code without needing to manage any computers or servers — Lambda will manage them for us. The way it works is easy: when the code is triggered, it runs automatically. I'm using Lambda in this project to work with API Gateway and build a serverless application that retrieves users.

The code I added to my function will retrieve data from a DynamoDB table. It retrieves the user based on a `userId` and returns that data; if it does not exist, it returns an error.

### Configuring a New API in API Gateway

In this step, I will configure a new API in API Gateway that lets requests reach Lambda easily.

![Lambda functions](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_a1b2c3d5)

## API Gateway

APIs are interfaces that allow different software applications to communicate and exchange data. There are different types of APIs, like REST APIs, GraphQL APIs, and WebSocket APIs. My API is a **REST API**, which uses HTTP methods such as GET, POST, PUT, and DELETE to interact with resources.

Amazon API Gateway is a service I use in this project to route incoming HTTP requests to the appropriate endpoints and invoke the corresponding AWS Lambda functions.

When a user makes a request through API Gateway, it routes the request to the appropriate Lambda function. Lambda executes the code, processes the request, and returns a response to API Gateway, which sends it back to the user.

![API Gateway](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_m3n4o5p6)

### Creating API Resources

In this step, I will create API resources that define the endpoints and structure of my API to meet the application's requirements.

## API Resources and Methods

An API is made up of resources, which represent the data or entities that an application exposes. Each resource can have different HTTP methods, such as GET, POST, PUT, and DELETE, to retrieve, create, update, or delete data.

![API Resources and Methods](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_u1v2w3x4)

### Setting Up the GET Method

In this step, I will set up a GET method for the `/users` resource and connect it to the Lambda function.

Each resource consists of methods, which define the HTTP actions clients can perform, such as GET to retrieve data, POST to create data, PUT to update data, and DELETE to remove data. Each method can be connected to a Lambda function to handle the request.

I created a `/users` resource and connected it to a Lambda function that retrieves data from the database and returns it to the client.

### Deploying the API to a Stage

In this step, I will deploy our API to a new stage in order to deploy it correctly.

![API Resources and Methods](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_c9d0e1f2)

## API Deployment

When you deploy an API, you deploy it to a specific stage. A stage is a named environment that represents a specific version of your API. I deployed my API to the `prod` stage, which represents the production environment where the API is intended to serve real users.

To visit my API, I used the Invoke URL generated after deployment. The API displayed an error because I hadn't created the DynamoDB table required by the Lambda function to retrieve data.

![API Deployment](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_3ethryj2)

## API Documentation

For my project's extension, I am writing API documentation to make the API easier for developers to understand, test, and integrate with their applications. I can do this using tools like Swagger (OpenAPI).

API documentation is a detailed description of an API's functionality, including its endpoints (e.g., `/users`), HTTP methods (e.g., GET), parameters (e.g., `userId`), and responses (e.g., success messages and error codes). Good documentation helps developers use the API correctly and efficiently.

Once I prepare my documentation, I can publish it to the `prod` stage. I have to publish my API to a specific stage because each stage represents a deployment environment and provides a URL through which clients can access the API.

My published and downloaded documentation showed me the API's metadata, including its title, version, base URL, resources such as `/users`, and supported methods like GET. It also included automatically generated details that help developers understand the API's structure and how to interact with its endpoints.

![API Documentation](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/2af91800-3f42-5fc1-b405-c5069180c0df_z9a0b1c2)
