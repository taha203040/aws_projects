## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS IAM to control access permission settings in our AWS account. We're doing this project to learn about cloud security from absolute foundations — every company thinks about IAM. Engineers' focus is on the skills we're about to build today.

### Tools and concepts

Services I used were EC2 and AWS IAM. Key concepts we learned include IAM users, policies, user groups, and account aliases. We also learned how to use the Policy Simulator, how JSON policies work, and how to launch EC2 instances, log in, and set up a new account under a permission set.

### Project reflection

This project took me approximately 1.5 hours, including demo time. The most challenging part was understanding JSON policies. It was most rewarding to see "permission denied" when our intern tried to delete our prod instances — so the permission works!

### ❤️ Thanks for doing this project!

I chose to do this project today because IAM and cloud security are key skills in the world of cloud computing. Something that would make learning with NextWork even better is if we could use architecture diagrams and add them to our docs.

## Tags

### What I did in this step

In this step, we launched two EC2 instances because we need to increase the compute power so we can handle more users and more traffic.

### Understanding tags

Tags are organizational tools that let us label our resources. They are helpful for grouping resources, cost allocation, and applying policies to all resources with the same tags.

### My tag configuration

The tag I've used on my EC2 instances is called "Environment". The values I've assigned for my instances are "development" and "production".

![Tags](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_2e0e5a5d)

## IAM Policies

### What I did in this step

In this step, we used an IAM policy for the new intern to control access and usage of the instances in the dev and prod environments.

### Understanding IAM policies

IAM Policies are sets of rules that determine who can do what in our AWS account.

### The policy I set up

For this project, I've set up a policy using JSON for easy implementation and to save time from a lot of clicking.

### Policy effect

I've created a policy that determines access for editing in development mode.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy mean applying the rules already set up in the JSON to the resources.

## My JSON Policy

![My JSON Policy](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_1c864649)

## Account Alias

### What I did in this step

In this step, we set up an account alias to make login easier to manage.

### Understanding account aliases

An account alias assigns a nickname to our account to make it easier to manage and log in.

### Setting up my account alias

Creating an account alias took us 30 seconds and it's a simple configuration in the IAM dashboard. The URL uses the alias instead of the account ID.

![Account Alias](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_0eb4439b)

## IAM Users and User Groups

### What I did in this step

In this step, we set up an IAM group for the new contractor intern so he can access his account with dedicated permissions.

### Understanding user groups

IAM user groups are like folders that collect IAM users so that you can apply permission settings at the group level.

### Attaching policies to user groups

We attached the policy we created to this user group, which means any user created inside this group will automatically get the same permission — attached to our NextWorkDevEnvPolicy.

### Understanding IAM users

IAM users are people or entities that have access to and can log in to our AWS account.

## Logging in as an IAM User

### Sharing sign-in details

The first way is via a CSV file or by sending email sign-in instructions.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that our user was already logged in, but it showed a lot of "access denied" messages for features not allowed based on the permission set.

![Logging in as an IAM User](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_6f2ab446)

## Testing IAM Policies

### What I did in this step

In this step, we logged in to our own AWS account and as the intern, and tested access to the production and development instances (not the production ones).

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the dev and prod instances.

### Stopping the production instance

When I tried to stop the production instance, we faced a permission error due to the policy that we implemented in the intern account.

![Testing IAM Policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, it successfully stopped. This was because our permission policy allows the intern to manage the dev instance with our permission.

![Testing IAM Policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_1811801c)

## IAM Policy Simulator

To extend our project, we are going to test policies in a safer and more controlled way — a tool called the IAM Policy Simulator. We're doing this because having to stop instances and log into AWS accounts as other users is a bit disruptive. Let's find a more efficient way.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool that lets us simulate actions and test permission settings by defining a specific user/group/role. It's useful for saving time from logging into the intern account and testing the policies that we implement in the account safely.

### How I used the simulator

We set up a simulation for whether our dev group has permission to stop instances or delete tags. The results were "denied" for both — we had to adjust the scope of the EC2 instance to ones that are tagged with "development". Once we applied that tag, permission was allowed.

![IAM Policy Simulator](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_069d8a621)
