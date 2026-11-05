![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/c1513937-a6bf-53e9-9512-a7d466c0e79c_1dddddwe)

## Introducing Today's Project!

In this project, I will demonstrate how to use Cloud front in our applicationdoing this project to learn...

### ✍️ What are we doing in this step?

In this step, I will create an S# bucket as fondation for our project

### Tools and concepts

Services I used were \*\*Amazon S3 and Amazon CloudFront\*\*. Key concepts I learnt include \*\*content delivery networks (CDNs), origin access control (OAC), S3 bucket policies, and secure content delivery\*\*. I also learnt how CloudFront distributes content through global edge locations while keeping the S3 bucket private.

### Project reflection

This project took me approximately 1 horu The most challenging part was config the OAC  and figure out the problem of error of Access restricion by adding 'index.html' into Default root object in general settings in Distrubution . It was most rewarding to learn about cloudfront!!!!

I chose to do this project today because I wanted to gain practical experience with AWS and understand how to deliver website content securely and efficiently using S3 and CloudFront.

Something that would make learning with NextWork even better is providing more troubleshooting exercises and real-world scenarios to help learners understand and solve common AWS errors independently.

## Set Up S3 and Website Files

I started the project by creating an S3 bucket to create a space where we can store our files webapp I can't use CloudFront for this task because Cloudfront is Content delivery not a storage state

### ✍️ What are we doing in this step?

In this step, I will upload the website files in S3 in order to use it later with cloudfront

The three files that make up my website are index.html, which is the sturct of the webpage  from texts inputs ...style.css, which used to style the webpage (it's like the makeup for webpages ) and script.js, which the functionality of the web page that can the usser intreact with it

I validated that my website files work by open the downloads file and see if its download with its unique file extention

![Set Up S3 and Website Files](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/c1513937-a6bf-53e9-9512-a7d466c0e79c_qgo7wcd3)

### ✍️ What are we doing in this step?

In this step, I will Set Up a CloudFront Distribution for our project

## Exploring Amazon CloudFront

Amazon CloudFront is a content delivery network (CDN), which means it delivers content to users through a global network of edge locations closer to them. Businesses and developers use CloudFront because it reduces latency, improves application performance, and reduces the load on origin servers by caching content closer to users.

To use Amazon CloudFront, I set up a distribution, which defines how CloudFront delivers content to users. I created a distribution for my web application, using the S3 bucket where I had already uploaded the files as the origin.

My CloudFront distribution's default root object is \`index.html\`. This means CloudFront automatically serves this file when a user accesses the distribution's domain name without specifying a particular file, allowing the web application to load its main page by default.

### ✍️ What are we doing in this step?

In this step, I will Verify my CloudFront Distribution by seeing the  distributed site from internt

### ✍️ Why do you think you ran into an access denied error?

Make a guess - this won't go into your documentation! by we don't give the Cloudfront the permission to get the web's files from it

![Exploring Amazon CloudFront](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/c1513937-a6bf-53e9-9512-a7d466c0e79c_qgo7wcdt)

## Handling Access Issues

When I tried visiting my distributed website, I ran into an access denied error because we don't give access to Cloudfront to S3 so we run into error due a permission issue

### ✍️ What are we doing in this step?

In this step, I will setup Origin Access control (OAC) to grant Cloudfront necessary permissions to access our S3 bucket

My CloudFront distribution's origin access settings were configured incorrectly (even it's public), which caused the Access Denied error because CloudFront did not have the required permissions to access the files in my S3 bucket. To fix this, I needed to configure Origin Access Control (OAC) and update the S3 bucket policy to allow CloudFront to retrieve the files securely.

To resolve the error, I set up Origin Access Control (OAC). OAC is an Amazon CloudFront feature that allows CloudFront to securely access files in an S3 bucket without making the bucket publicly accessible. It works with an S3 bucket policy that grants permission to my CloudFront distribution to retrieve the files, protecting the content from unauthorized direct access.

![Handling Access Issues](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/c1513937-a6bf-53e9-9512-a7d466c0e79c_egrhntyu)

## Updating S3 Permissions

Once I set up my OAC, I still needed to update my S3 bucket policy because creating an OAC does not automatically grant CloudFront permission to access my bucket. I added a policy statement that allows my specific CloudFront distribution to access the S3 objects, ensuring that CloudFront can deliver the files while the bucket remains private.

### ✍️ What are we doing in this step?

In this step, I will Update my S3 bucket's settings in order to resolve the cloudfront 's permission  problem

Creating an OAC automatically gives me a policy I could copy, which grants the CloudFront service permission to read objects from my private S3 bucket (\`s3:GetObject\`), restricted to my specific CloudFront distribution using the \`AWS:SourceArn\` condition. also an additional config which add Default root object in general settings with value 'index.html' (for static content)

![Updating S3 Permissions](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/c1513937-a6bf-53e9-9512-a7d466c0e79c_eg98ntyu)
