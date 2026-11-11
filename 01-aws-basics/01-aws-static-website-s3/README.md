## Introducing Today's Project!

### Tools and concepts

The service we used was Amazon S3. Key concepts we learned include bucket policies, uploading static website files, index.html, bucket endpoint URLs, and ACLs (Access Control Lists) and how to control access.

### Time, challenges, and wins

This project took me approximately 1.5 hours, including demo time, quiz time, and secret mission time. The most challenging part was resolving the 403 Forbidden error. It was most rewarding to see our webpage load live and be public to the world.

### ❤️ Thanks for doing this project!

I chose to do this project today because it was the beginner-friendly first step to learning AWS properly. Something that would make learning with NextWork even better: I think we should have more secret missions.

## How I Set Up an S3 Bucket

### What I did in this step

In this step, I opened the S3 bucket page and created a bucket for storage.

### How long it took to create the bucket

Creating an S3 bucket took me 5 minutes and it was easy — just make sure we have a solid understanding of ACLs, managing versioning, and managing the visibility of the app.

### Region selection

The Region I picked for my S3 bucket was the one closest to us. It's best practice to pick the region closest to you because it lowers the time to retrieve your data (low latency).

### Understanding bucket name uniqueness

S3 bucket names are globally unique! This means no two buckets in the entire world can have the same name, regardless of the account or the region.

![How I Set Up an S3 Bucket](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_ba6d42ad)

## Upload Website Files to S3

### What I did in this step

In this step, I uploaded the website files into our S3 bucket. This is important because no files = no website.

### Files I uploaded

I uploaded two files to my S3 bucket — they were index.html and the asset files needed for the website to work correctly.

### How the files work together

Both files are necessary for this project, as index.html explains the structure of the app and the other files make the website look properly.

![Upload Website Files to S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_a265af88)

## Static Website Hosting on S3

### What I did in this step

In this step, I made my app visible to the public world by setting up static website hosting. This is important because our website is not shown to the public yet.

### Understanding website hosting

Website hosting means putting our website files on a web server, which is a special computer designed to turn the files into a real, active website that is visible to the public.

### How I enabled website hosting

To enable website hosting with my S3 bucket, I clicked on the properties of the selected bucket, scrolled down to the static website section, and clicked edit. After that, I set the name of the file that gets hosted (the index document).

### Access Control Lists (ACLs)

An ACL is a way to decide and configure the permission settings inside buckets. We enabled ACLs so that we can control access to our website files later. There was a popup warning advising us not to enable it, but we enabled it to learn how ACLs work and compare them with bucket policies later.

![Static Website Hosting on S3](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_c22c54c0)

## Bucket Endpoints

### Understanding bucket endpoint URLs

Once static website hosting is enabled, S3 produces a bucket endpoint URL, which is the way to see the website after it's set up in the S3 bucket.

### What I saw when I tested the endpoint

When I first visited the bucket endpoint URL, I saw a 403 Forbidden error. The reason for this error was that the files were not publicly accessible, which made visiting the page fail.

![Bucket Endpoints](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_22ce4daf)

## Success!

### What I did in this step

In this step, we went into the files and made them public, because that was causing the problem.

### How I resolved the 403 error

To resolve this 403 Forbidden error, I selected the checkbox for the files we wanted to make public, clicked the Actions option, and hit "Make public" via ACL.

### ✅ What were the key services and concepts you learnt in this project?

The service we used was Amazon S3. Key concepts we learned include bucket policies, uploading static website files, index.html, bucket endpoint URLs, and ACLs and how to control access.

### ✅ How long did it take you to complete this project?

This project took me approximately 1.5 hours, including demo time, quiz time, and secret mission time. The most challenging part was resolving the 403 Forbidden error. It was most rewarding to see our webpage load live and be public to the world.

### ❤️ Thanks for doing this project!

I chose to do this project today because it was the beginner-friendly first step to learning AWS properly. Something that would make learning with NextWork even better: I think we should have more secret missions.

![Success!](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_5d4474f9)

## Bucket Policies

### What I did in this extension

In this project extension, we wanted to implement a policy that denies everyone from deleting our files.

### Understanding bucket policies

An alternative to ACLs are bucket policies, which are JSON-based policy documents that define who can perform which actions on the bucket and its objects. The benefit of using bucket policies is that they determine who has permission to perform certain actions (and who doesn't), while ACLs are useful for public access to individual objects inside the bucket.

![Bucket Policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-host-a-website-on-s3_sm2sm2sm)

### What my bucket policy does

Our bucket policy denies everyone from deleting our index.html in the bucket. We tested this by trying to delete the HTML file and saw a "denied access" error preventing the deletion.
