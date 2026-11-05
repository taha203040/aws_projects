## Introducing Today's Project!

### Tools and concepts

Services we used were amazo s3 key conspes we learn include policies , uploading static ewbsite fiels , index.html bucket endpoiint urls and acls and how control access

### Time, challenges, and wins

This project took me approximately 1.5 howrs including dem time , queiz time and secret misstion time , the most chalenging part was resolving the 403 forbidden error  it was most rewarding to see our webpage load live and be public  to the world

### ❤️ Thanks for doing this project!

I chose to do this project today because it was the biggner and first step to learn aws proprely... Something that would make learning with NextWork even better ,  ithink we should more secret missions

## How I Set Up an S3 Bucket

### What I did in this step

in this step i open s3 bucket page and create bucket storage

### How long it took to create the bucket

Creating an S3 bucket took me 5 mins and its easy just make sure that we have a solid inderstand in acls and managing the versionning and manage the visibility of the app

### Region selection

The Region I picked for my S3 bucket was... because its the region thats closest to us , its best practise to pick the region closest to you because it lowers time to retrieve your things (low latency)

### Understanding bucket name uniqueness

S3 bucket names are globally unique! This means no two buckes in the entire woorld can have same name regadless the account or the region

![How I Set Up an S3 Bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_ba6d42ad)

## Upload Website Files to S3

### What I did in this step

In this step, I will upload the website files into our s3 bucket . This important because \
no files = no website

### Files I uploaded

I uploaded two files to my S3 bucket - they were index.html and files of assessts that needed for the websitse to wotk  correctly

### How the files work together

Both files are necessary for this project as index explain the struct of the app and the other for the website to look probpley

![Upload Website Files to S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_a265af88)

## Static Website Hosting on S3

### What I did in this step

In this step, I will make the my app visible to public in the world by setp the static website hosting and its important becausse our website its nopt showen now to the public

### Understanding website hosting

Website hosting means...website hositng means putting oru webisite fiels on the web server , which is as special computer designed to turn the fiels unto real and active website and visible to public

### How I enabled website hosting

To enable website hosting with my S3 bucket, I click on the properties of selected bucket and after that i scroll down to the static website and click edit after that i set up the name of the file that get hosted

### Access Control Lists (ACLs)

An ACL its a way to decide and configure the premision settings inside buckes . We enable ACL sp that we can control access to our webiste files later , there popup warning that warn that should we not enable it but we eneable it to learn how acl works and compare it with buckts policis later

![Static Website Hosting on S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_c22c54c0)

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website is enabled, S3 produces a bucket endpoint URL, which is the way to see the website after it set it up in s3 bucket

### What I saw when I tested the endpoint

When I first visited the bucket endpoint URL, I saw... The reason for this error was about its forbidden error which make visiting  the page incorreclty

![Bucket Endpoints](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_22ce4daf)

## Success!

### What I did in this step

In this step, we will got into the files and make them public to because that cause the problem

### How I resolved the 403 error

To resolve this 403 Forbidden error, I select the box button for the files that we make them public after that i click the action option and hit the make publci by acl

### ✅ What were the key services and concepts you learnt in this project?

Services we used were amazo s3 key conspes we learn include policies , uploading static ewbsite fiels , index.html bucket endpoiint urls and acls and how control access

### ✅ How long did it take you to complete this project?

This project took me approximately 1.5 howrs including dem time , queiz time and secret misstion time , the most chalenging part was resolving the 403 forbidden error  it was most rewarding to see our webpage load live and be public  to the world

### ❤️ Thanks for doing this project!

I chose to do this project today because it was the biggner and first step to learn aws proprely... Something that would make learning with NextWork even better ,  ithink we should more secret missions

![Success!](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_5d4474f9)

## Bucket Policies

### What I did in this extension

In this project extension we want to implement a policy that deny every one from delting our files

### Understanding bucket policies

An alternative to ACLs are bucket policies, which are... The benefit of using bucket policies is (determine which has the permission and not to apply certain ACTIONS)... while ACLs are useful for public access to individual objects inside the bucket

![Bucket Policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

our bucket policy denies every one from deleting our index.tml n the bucket... we  tested this by deleting the html file ... and saw and error of denied access to delete it
