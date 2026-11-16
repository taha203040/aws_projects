<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://nextwork.ai/static/nextwork-logo-paper.svg" />
  <img src="https://nextwork.ai/static/nextwork-logo-leather.svg" alt="NextWork" width="300" />
</picture>

# Build a Three-Tier Web App

**Project Link:** [View Project](https://nextwork.ai/projects/f10f5983-0a15-5628-94b2-1cc37b19cb8c)

**Author:** Rabia Taha

![Screenshot](https://nextwork.ai/covers/screenshot_398facc5717b2c4a1ec15efee65f1f8b.png)

---

![Three-Tier Web App](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_2b3c4d5e)

## Designing a Three-Tier Web Application

### Project Goals and Learning Objectives

In this project, I will demonstrate how to build a three-tier web application. I'm doing this project to learn more about three-tier architecture with real practice using AWS.

## Delivering the Website Through CloudFront

### Presentation Tier Architecture

For the presentation tier, I will set up the presentation tier by:

- Creating an S3 bucket to store the website's files.
- Uploading a simple `index.html` file to the bucket.
- Setting up CloudFront to deliver the website's content globally.

All of that is done in this step.

![Delivering the Website Through CloudFront](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_3a4b5c6d)

### Accessing the Delivered Website

I accessed my website using the distribution domain name provided by CloudFront. By opening this URL in my browser, I could view the website hosted in my S3 bucket.

## Building Serverless Application Logic

### Logic Tier Architecture

For the logic tier, I will set up AWS Lambda to handle the application's business logic and Amazon API Gateway to receive HTTP requests and route them to the appropriate Lambda functions.

![Building Serverless Application Logic](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_6a7b8c9d)

### Retrieving Data with Lambda

The Lambda function retrieves data from Amazon DynamoDB based on the provided `userId` and returns the user's information to the API caller.

## Creating the DynamoDB Data Layer

### Data Tier Architecture

For the data tier, I will set up Amazon DynamoDB to store user data and allow the Lambda function to retrieve it correctly based on the provided `userId`.

### DynamoDB Table Design

The partition key for my DynamoDB table is `userId`, which means each item is identified by its user ID, allowing DynamoDB to efficiently retrieve user data using that key.

![Creating the DynamoDB Data Layer](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_u1v2w3x4)

## Connecting the Application Tiers

### Integration Strategy

Once all three layers of my three-tier architecture are set up, the next step is to integrate them so the frontend can send requests through API Gateway, Lambda can process them, and DynamoDB can store and retrieve the required data.

![Connecting the Application Tiers](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_a112c3d5)

### Testing API Responses

To test my API, I navigated to the Invoke URL provided by API Gateway and appended `/users?userId=1` to the URL. The API successfully retrieved and returned the corresponding user data from DynamoDB.

### Investigating Missing User Data

My suggestion is that we don't update the `script.js` to accept data and push it into the HTML file.

### Diagnosing the CloudFront Error

The error on my deployed website occurred because I had not configured the correct API endpoint in the frontend. I needed to replace the placeholder with my production API Gateway URL and append `/users?userId={userId}` to retrieve the corresponding user data from DynamoDB. Without this configuration, the frontend could not send requests to the correct API endpoint.

### Updating the Website Script

To resolve the error, I updated `script.js` by pasting the invoke URL from API Gateway. I then reuploaded it into S3 to update the code to the newest version.

## Troubleshooting and Validating the Full Web App

### End-to-End Validation Plan

In this step, I will test the CloudFront site again and resolve an error that is related to the browser side.

![Troubleshooting and Validating the Full Web App](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_a1b2c3d5)

### Diagnosing the Browser Error

I encountered a second error after updating `script.js`. This time, the issue was related to Cross-Origin Resource Sharing (CORS) in API Gateway. The browser blocked requests from my frontend because the API needed to be configured to allow requests from the website's origin.

### Resolving CORS in the API

To resolve the CORS error, I opened API Gateway, selected the `/users` resource, and enabled CORS by adding my website's origin to the allowed origins.

![Resolving CORS in the API](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/f10f5983-0a15-5628-94b2-1cc37b19cb8c_1qthryj2)

### Updating Lambda for CORS

I also updated my Lambda function to resolve the CORS issue. I added the `Access-Control-Allow-Origin` header to both the `200 OK` and `404 Not Found` responses, allowing the browser to accept responses from different origins. I also included the `Content-Type: application/json` header to indicate that the response contains JSON data.

### Verifying the Completed Connection

I verified the connection between API Gateway and CloudFront by returning to the website, entering the user ID `1`, and pressing Enter. The user's data was successfully displayed, confirming that the connection was working correctly.

## Reflecting on the Serverless Build

### Services and Concepts Learned

Services I used were AWS Lambda, Amazon DynamoDB, and AWS Identity and Access Management (IAM). Key concepts I learned include Lambda functions, DynamoDB tables and partition keys, AWS SDK, execution roles, IAM permissions, and the principle of least privilege.

### Project Experience and Challenges

This project took me approximately 1 hour. The most challenging part was debugging the error and solving it by attaching the right policy to Lambda. It was most rewarding to learn more about three-tier architecture.

### Learning Reflection

I chose to do this project today because I wanted to gain hands-on experience with AWS Lambda and DynamoDB and learn how to retrieve data securely using IAM permissions.

Something that would make learning with NextWork even better is providing more practical troubleshooting exercises and real-world scenarios to help learners develop their problem-solving skills.
