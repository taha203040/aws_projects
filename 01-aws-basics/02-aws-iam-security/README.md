## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS IAM TO control access permession settings in our AWS account We're doing this project to learn about cluod security from absoulete fonaatiosn - every company thinks about IAM Engineers' focusd on the skills we're about to build today : o

### Tools and concepts

Services I used were EC2 and AWS IAM ,  Key concepts we learn it include IAM users , policies , user groups and accoint aliaces. W e also learn how to use the Policy Simulator and how JSON polices work and lunsh EC2 instances login setup new account under a permission

### Project reflection

This project took me approximately 1.5 hour include demo time. The most challenging part was understanding json policies  It was most rewarding to see permission denied when our inter tired to delete our prod inctances so the permission it works !

### ❤️ Thanks for doing this project!

I chose to do this project today because IAM and clound security are key skills in the world of cloud computing .  Something that would make learning with NextWork even better is we cloud architecute diagrams and add taht o to our docs

## Tags

### What I did in this step

In this step, We will launch two ec2 instances because we need to incerase the boost computer - so we handle more users and more trafic

### Understanding tags

Tags are organaztions tools that lets label our recourse , in our recources , They are helpful  for grouping recourse , cost allocations and policies for all recoureses , with same tags

### My tag configuration

The tag I’ve used on my EC2 instances is called... The value I’ve assigned for my instances are devlopoment and productions

![Tags](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_2e0e5a5d)

## IAM Policies

### What I did in this step

In this step,we will to use IAM policy for new intern to control access of usage for the instances in dev and prod envs

### Understanding IAM policies

IAM Policies are set of rules that determine who can do what in our AWS account

### The policy I set up

For this project, I’ve set up a policy using json for easy implementing and saving time from lot of clicking

### Policy effect

I’ve created a policy that detrmine the acces of editing  in develompent mode

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy means appling the rules that already  setup in the json to the recoures

## My JSON Policy

![My JSON Policy](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_1c864649)

## Account Alias

### What I did in this step

In this step, we will setup Account  alias , to get ease login and manage

### Understanding account aliases

An account alias is  assign a nick name to our accont to get ease manage and login

### Setting up my account alias

Creating an account alias took us 30 sec and its simple configuration in the IAM dashboard and the url uses the alias instand the account ID

![Account Alias](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_0eb4439b)

## IAM Users and User Groups

### What I did in this step

In this step, We will setup a iam grou for new condat intern so he can access in his account in dedicated permissions

### Understanding user groups

IAM user groups are like folders taht collect IAM useras so that you can apply permission settings at the group level

### Attaching policies to user groups

we attached teh policy we created this user group  , which mean any user created inside this group will automaticlly get the permisssion at same attachment to our Nextworkdevenvpolicy

### Understanding IAM users

IAM users are people or entities that have access /can login to our AWS account

## Logging in as an IAM User

### Sharing sign-in details

The first way is csv file or sned email signin instructions

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that our usr is alredy login but it show him a lot of denied access to features not allowed based on the permission

![Logging in as an IAM User](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_6f2ab446)

## Testing IAM Policies

### What I did in this step

In this step , we will log in to our own aws account ans the intern and test access to the productionand develoment not the productions

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the dev and prod instances

### Stopping the production instance

When I tried to stop the production instance we facing a permission error due the policy that we implemnent it in the inter account

![Testing IAM Policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance and it success stoped the instances .This was because our permission policy allows the intern to manage the dev instance with our permission

![Testing IAM Policies](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_1811801c)

## IAM Policy Simulator

To extend our project, we are going to test policies in safer and more controlled way - a tol called the IAM Policy simulator we're \
doing this becasue having to stop instances and log into AWS accounts asd other users i bit disruptive Lets find a more efficient way.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool taht lets us simulate actions and test permission settings by definign a specific user/group/role...  It's useful for saving time for login to intern account and test the policies that we implement it into the account safely

### How I used the simulator

We set up a simulation for whether our dev group has permission to stpop instances or deletetags ,The results were denied for both - we had to adjust the scoop of the EC2 instance to ones that are tagged with "development" . Once we aplied that tag , permission wass allowed

![IAM Policy Simulator](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-security-iam_069d8a621)
