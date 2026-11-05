![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_dd9d254e)

## Introducing Today's Project!

In this project, I will demonstrate how to use github with aws in the series of daily devops and currently in day 2.  I'm doing this project to learn multiple skills in devops field

### ✍️ What are we doing in this step?

In this step, I will deploy the app in AWS by lunch the EC2 instace and setup the remote-ssh in vscode (built in) to easy develop.

### ✍️ What are we doing in this step?

In this step, I will install Git (version control system). because it provide the abiility to tracks the changes of the code

### Key tools and concepts

Services I used were Git, GitHub, and the Git command line (Git Bash/Terminal).\
Key concepts I learnt include Git repositories, commits, branches, pushing and pulling changes, cloning repositories, and using GitHub tokens for authentication.

### Project reflection

This project took me approximately 2 hours to complete.\
The most challenging part was setting up Git authentication with a GitHub token and connecting my local repository to GitHub.\
It was most rewarding to see my changes successfully pushed to GitHub and understand how Git tracks project versions

I did this project because its a long with the daily devops projects and i push my self to complete and add devops in my skills

\*\*This project is part two of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project to learn more about automation, continuous integration, and deploying applications.\*\*

## Git and GitHub

Git is a version control that allow to track code changes  in development phase.I installed Git using the commands \
'sudo dnf update -y\
sudo dnf install git -y\
'

### ✍️ What are we doing in this step?

In this step, I will create a github account and repository,because it provide the ability to store the code and access with ease by copy the url of the reporo download the code as zip (depands on the visibilty of the repository))

GitHub is storage space for different version. I'm using GitHub in this project to edit and update the code and store it in the cloud so that i dont worry about losing it in the future

![Git and GitHub](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_efaadbf7)

## My local repository

A Git repository is folder that contain all project files and their entire version history. Hosting a repo in the cloud, like on GitHub, means we can also collaborate with other engineers and access to the work from anywhere.

### ✍️ What are we doing in this step?

In this step, I will Set up a local git repo in web app folder and Connect to the local repo with GitHub repo to publish the code in the EC2 easly

git init is a command that creates a new Git repository. I ran git init in my project folder to start tracking my files with Git.

A branch in Git is a separate version of the project where you can work on changes without affecting the main project.\
After running git init, the response from the terminal was: "Initialized empty Git repository in ..."

![My local repository](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_7bf21bae)

## To push local changes to GitHub, I ran three commands

### git add

The first command I ran was\
'git add .' tages all (marked by the '.') files in nextwork-web-project to be saved in the next version of your project.\
A staging area is telling Git to put together all our  modified files for a final review before we commit them. This is incredibly handy because we get to see all your edits in one spot, which means its much easier to check if there were are mistakes or unwanted changes before you commit.

### git commit

The second command I ran was \
'git push -u origin master' \
Using '-m' means  flag lets us to leave a message describing what the commit is about

### git push

The third command I ran was \
'git push -u origin master' Using '-u' means setting an 'upstream' for our local branch , which means telling Git to remember to push to master by default. Next time , we  can simply run git push without needing to define origin and master.

![To push local changes to GitHub, I ran three commands](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_c92fbe05)

## Authentication

When we commit changes to GitHub, Git asks for our credentials because needs to double check that we have the right to push any changes to the remote origin of local repo is connected with. To do this, Git is now authenticating our identity by asking for our  GitHub credentials.

### Local Git identity

Git needs my name and email because it uses them to identify who made each commit and to keep a record of the project's history.

Running git log showed me that Git keeps a history of my commits, including the commit ID, author, date, and commit message.

### ✍️ What are we doing in this step?

In this step, I will making changes to our web app and commit and push those changes to github , for update the code that in Github

![Authentication](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_9a27ee3b)

## GitHub tokens

GitHub authentication failed when I entered my password because it require a hard guess  string called token it have combination of random charactars for security reasons

### ✍️ What are we doing in this step?

In this step, I will Set up a token on GitHub  and Use the generated token to access your GitHub repo from my local repo. because the password won't work for authentication

A GitHub token is a secure key used to authenticate your GitHub account instead of a password.\
I'm using one in this project because it allows Git to securely access my GitHub repository when pushing or pulling code.

I could set up a GitHub token by going to GitHub Settings, creating a Personal Access Token, copying it, and using it to authenticate Git instead of a password.\*\*

![GitHub tokens](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_fa11169d)

## Making changes again

A simple completion:

I wanted to see Git working in action, so I made changes in my project files and committed them. I couldn't see the changes in my GitHub repository initially because I hadn't pushed my commits to the remote repository yet.

I finally saw the changes in my GitHub repo after I pushed my commits using \`git push\`.

![Making changes again](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_6becb2bc)

## Setting up a READMe file

As a finishing touch to my GitHub repository, I added a README file, which is A README is a document that introduces and explains your project, like what the project does, how to set it up, and how to use it. I added a README file by creating it in the main app folder by the command 'touch README.md '

My README is written in Markdown because Markdown provides a simple way to structure and format documentation using plain text.

Special characters can help you format text in Markdown, such as:\
\# for headings\
\*\*text\*\* for bold text\
\*text\* for italic text\
\- or \* for bullet lists\
etc...

My README file has 6 sections that outline The Header Introduction ,Technologies , Setup , Contact ,Conclusion

![Setting up a READMe file](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/aws-devops-github_c94976902)
