![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_r7s8t9u0)

## Introducing Today's Project!

In this project, I will demonstrate how to securely store and retrieve credentials using AWS Secrets Manager. I am undertaking this project to learn more about securing web applications, protecting sensitive information, and preventing credentials from being exposed in the codebase.

### ✍️ What are we doing in this step?

In this step, I'm going to access a GitHub repository containing a web app's code , after that we identify where credentials are stored (insecurely!) , clone it into my pc and Hardcode AWS credentials (which means writing them directly into the code, instead of retrieving them in a secure way)

### Tools and concepts

The service I used was AWS Secrets Manager. Key concepts I learned include securely storing and retrieving sensitive credentials, managing secrets outside the codebase, avoiding hardcoded credentials, and protecting environment variables and other sensitive configuration data from accidental exposure.

### Project reflection

This project took me approximately one hour to complete. The most challenging part was rebasing the commits to remove the commit containing sensitive credentials from Git history. The most rewarding part was learning how to secure AWS credentials using AWS Secrets Manager, apply IAM permissions, and use GitHub's secret scanning and push protection to prevent accidental exposure of sensitive information.

I chose to work on this project today because the topic is unique and valuable, and it gave me an opportunity to gain practical experience in securing web applications and managing sensitive credentials.

## Hardcoding credentials

In this project, a sample web app is exposing... It is unsafe to harcode credentiaIn this project, a sample web application exposes environment variables in its code. Hardcoding credentials or exposing them in frontend code is unsafe because attackers could access sensitive information, such as API keys and database credentials, and use them to gain unauthorized access to services or data. To improve security, secrets should be stored securely and accessed on the server side, using tools such as AWS Secrets Manager or environment variables configured outside the source code.ls because...

I've set up the initial configuration with paste the AWS  credentials in the 'config.py' These credentials are just examples because we it's just demonstration on how we use Secret M

### ✍️ What are we doing in this step?

In this step, I am going to explore GitHub's secret scanning feature to understand how it detects exposed credentials and helps prevent security risks. I will fork the original repository, attempt to push code containing example credentials to GitHub, and observe how secret scanning detects potential secrets and helps protect sensitive information from being exposed.

![Hardcoding credentials](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_j2k3l4m5)

## Using my own AWS credentials

As an extension to this project, I decided to build a web application using FastAPI to interact with AWS services. To set up my Python virtual environment, I installed FastAPI for building the API, Uvicorn for running the application server, Boto3 for interacting with AWS services, and Python Multipart for handling form data and file uploads. I pinned specific package versions to maintain a consistent and reproducible development environment.

When I first ran the app, I encountered an error because \`config.py\` was using placeholder AWS credentials instead of valid credentials. As a result, the application could not authenticate with AWS and retrieve my S3 bucket names. This helped me understand the importance of configuring valid credentials and storing them securely using AWS Secrets Manager.

To resolve the \`InvalidAccessKeyId\` error, I replaced the placeholder credentials in AWS Secrets Manager with valid access keys generated for an IAM user. This allowed the application to authenticate with AWS using valid credentials and retrieve the names of my S3 buckets.

![Using my own AWS credentials](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_wghjteykut)

## Pushing Insecure Code to GitHub

Once I updated the web application code with example credentials, I forked the repository to create my own copy on GitHub, allowing me to experiment with changes without affecting the original repository. A fork is different from a clone because a fork creates a copy of the repository under my GitHub account, while a clone creates a local copy on my computer. Forks can be publicly accessible, depending on their visibility settings, whereas a local clone is stored on my machine.

To connect my local repository to the forked repository, I copied the fork's URL from GitHub and added it as the remote origin of my local copy. Then, I used \`git add\` and \`git commit\` to stage and save my changes in a local commit. Finally, I used \`git push\` to upload my committed changes to the forked repository on GitHub.

GitHub blocked my push because its secret scanning and push protection detected an AWS Access Key ID in \`config.py\` within my commit. This prevented potentially sensitive credentials from being uploaded to the repository. This is a good security feature because it helps prevent accidental exposure of secrets, reducing the risk of unauthorized access to AWS resources and potential security breaches.

### ✍️ What are we doing in this step?

In this step, I am going to create a new secret in AWS Secrets Manager to store sensitive AWS credentials securely instead of hardcoding them in the codebase. This helps protect credentials from being exposed in source code or version control and allows the application to retrieve them securely when needed.

![Pushing Insecure Code to GitHub](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_o2p3q4r5)

## Secrets Manager

AWS Secrets Manager is a service that securely stores, manages, and retrieves sensitive information. I am using it to store my \`AWS\_ACCESS\_KEY\_ID\` and \`AWS\_SECRET\_ACCESS\_KEY\` instead of hardcoding them in my application's source code. Other common use cases include storing database credentials, API keys, and third-party service credentials. Secrets Manager also supports secret rotation, encryption, and access control through IAM policies, helping protect sensitive information from unauthorized access.

Another feature of AWS Secrets Manager is secret rotation, which means automatically changing secrets, such as database passwords, on a regular schedule. This improves security by reducing the time a compromised secret can remain valid. It is particularly useful for high-risk credentials, such as database passwords and privileged service credentials, where regular updates help limit the potential damage caused by unauthorized access.

AWS Secrets Manager provides sample code in various programming languages, such as Python, JavaScript, Java, and C#. This is helpful because developers can use the AWS SDK to retrieve secrets programmatically without hardcoding sensitive information in their applications. These examples also make integration easier and help developers follow AWS security best practices.

### ✍️ What are we doing in this step?

In this step, I am going to use the sample code provided by AWS Secrets Manager to update my \`config.py\` file. Instead of hardcoding AWS credentials in the source code, I will retrieve them securely from Secrets Manager. This improves security by keeping sensitive information out of the codebase and reducing the risk of accidental exposure through version control.

![Secrets Manager](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_h2i3j4k5)

## Updating the web app code

I updated the \`config.py\` file to retrieve secrets from AWS Secrets Manager. The \`get\_secret()\` function creates a Secrets Manager client, requests the secret by its name from the AWS Region where it is stored, and extracts its value from the response. If the request fails, it raises a \`ClientError\`. This allows the application to retrieve sensitive credentials at runtime instead of hardcoding them in the source code.

I also added code to \`config.py\` to extract the AWS access key ID, secret access key, and Region from the retrieved secret. This is important because it allows the application to access the required configuration values dynamically instead of hardcoding them. If the Region is not included in the secret, the code uses the default Region from the Boto3 session, falling back to \`us-east-2\` if no Region is configured.

![Updating the web app code](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_v0w1x2y3)

## Rebasing the repository

Git rebasing is a process that rewrites a branch's commit history by moving, editing, or removing commits. I used interactive rebasing to remove the commit containing sensitive AWS credentials from my local Git history. This was necessary because GitHub's push protection blocked my push after detecting the credentials. Removing the commit helps prevent the sensitive information from being uploaded, even though the credentials were only examples.

A merge conflict occurred during rebasing because Git encountered conflicting changes between the commits being replayed. I resolved the conflict by removing the section containing the hardcoded credentials and deleting the conflict markers (\`\<\<\<\<\<\<\< HEAD\`, \`=======\`, and \`\>\>\>\>\>\>\> feature-branch\`). I then saved the file, ensuring that the sensitive credentials were removed while preserving the updated code that retrieves secrets from AWS Secrets Manager.

Once I resolved the merge conflict, I returned to GitHub to verify that the sensitive data had been removed from the repository. This confirmed that the hardcoded credentials were no longer present in the updated code. I also ensured that the application retrieved secrets from AWS Secrets Manager instead of storing credentials directly in the codebase.

![Rebasing the repository](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/d6a05ea4-6c31-5e53-8688-de54814d6209_t5u6v7w8)
