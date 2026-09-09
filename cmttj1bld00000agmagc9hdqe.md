---
title: "🚀 Deploy a Static Portfolio Website to AWS S3 Using GitHub Actions | Complete CI/CD Project for Beginners"
seoTitle: "Deploy Website to AWS S3 with GitHub Actions"
seoDescription: "Learn how to deploy a static portfolio website to AWS S3 using GitHub Actions, IAM, AWS CLI, GitHub Secrets, and automated CI/CD."
datePublished: 2026-09-09T03:16:31.417Z
cuid: cmttj1bld00000agmagc9hdqe
slug: aws-s3-github-actions-deployment
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/695343af-32e3-4bda-8387-1114b97f6e6a.png
tags: aws, devops, s3, github-actions, ci-cd, devops-articles, devops-journey, devopscommunity, s3-bucket, s3-static-website-hosting

---

A simple static website can teach you some of the most important DevOps concepts:

*   Git and GitHub
    
*   AWS IAM
    
*   Amazon S3
    
*   AWS CLI
    
*   GitHub Actions
    
*   GitHub Secrets
    
*   CI/CD
    
*   Static Website Hosting
    
*   Automated Deployment
    

In this project, I built a personal portfolio website using **HTML, CSS, and JavaScript**, stored the source code on GitHub, created an **Amazon S3 bucket** for hosting, and configured **GitHub Actions** to automatically deploy the website to S3 whenever I push new changes.

The final workflow looks like this:

```text
Developer
    |
    | git push
    ↓
GitHub Repository
    |
    ↓
GitHub Actions
    |
    ↓
Ubuntu Runner
    |
    ↓
AWS Authentication
    |
    ↓
AWS S3
    |
    ↓
Live Portfolio Website
```

The main idea is simple:

> **Write code → Push to GitHub → GitHub Actions runs automatically → Website is updated on AWS S3.**

This project is based on the **Git & GitHub for DevOps workshop**, starting from approximately **02:54:02**.

🎥 Workshop Reference:

https://www.youtube.com/live/DyqAdz96mok?si=yTWM7TqpWvtRsDTU&t=10442

* * *

# 📌 Project Overview

The goal of this project is to deploy a static portfolio website to an Amazon S3 bucket and automate the deployment using GitHub Actions.

The portfolio is built with:

```text
HTML
CSS
JavaScript
```

The source code is stored in GitHub.

AWS S3 is used to host the static website.

GitHub Actions is used to automate deployment.

* * *

# 🎯 What We Are Building

Our final architecture looks like this:

```text
                 GitHub Repository
                        |
                        |
                    git push
                        |
                        ↓
                GitHub Actions
                        |
                        ↓
                Ubuntu Runner
                        |
                AWS Authentication
                        |
                        ↓
                  AWS S3 Bucket
                        |
                        ↓
              Static Website Hosting
                        |
                        ↓
              🌐 Live Portfolio
```

Whenever we make a change to the website:

```text
Change Code
    ↓
git add .
    ↓
git commit
    ↓
git push
    ↓
GitHub Actions
    ↓
AWS S3
    ↓
Website Updated
```

This eliminates the need to manually upload website files to S3 every time.

* * *

# 🛠️ Technologies Used

This project uses:

| Technology | Purpose |
| --- | --- |
| HTML5 | Website structure |
| CSS3 | Website styling |
| JavaScript | Website functionality |
| Git | Version control |
| GitHub | Source code hosting |
| GitHub Actions | CI/CD automation |
| AWS IAM | Authentication and permissions |
| Amazon S3 | Static website hosting |
| AWS CLI | Uploading files to S3 |

* * *

# 📂 My GitHub Repository

The complete project source code is available here:

https://github.com/hritikranjan1/hritik-portfolio1

The repository contains the main website files along with the GitHub Actions workflow.

The current repository structure includes:

```text
hritik-portfolio1/
│
├── .github/
│   └── workflows/
│
├── css/
│   └── style.css
│
├── js/
│   └── script.js
│
├── index.html
│
└── README.md
```

The GitHub repository confirms the presence of the `.github/workflows`, `css`, `js`, `index.html`, and `README.md` structure.

* * *

# 🌐 Final Live Website

The final portfolio is hosted on Amazon S3.

You can access it here:

http://hritik-portfolio1.s3-website-us-east-1.amazonaws.com

The website is a static portfolio built using:

```text
HTML
CSS
JavaScript
```

* * *

# 🤔 Why Use Amazon S3 for a Static Website?

Amazon S3 is an object storage service provided by AWS.

Although S3 is commonly used to store files, it can also serve static website content.

Static websites generally contain files such as:

```text
index.html
style.css
script.js
images
fonts
```

For a simple portfolio website, we don't need a traditional backend server.

Instead:

```text
Browser
   |
   ↓
S3
   |
   ├── index.html
   ├── CSS
   ├── JavaScript
   └── Images
```

S3 can serve these files to users.

* * *

# 🧠 What is Static Website Hosting?

A static website does not require server-side application processing.

For example:

```text
HTML
CSS
JavaScript
Images
```

are delivered directly to the browser.

Examples of static websites:

*   Portfolio
    
*   Resume website
    
*   Documentation
    
*   Landing page
    
*   Product information page
    
*   Simple business website
    

For this project, our portfolio is a static website.

* * *

# ☁️ Why S3 Instead of a Traditional Server?

For a simple static website, using a full EC2 server can be unnecessary.

With S3:

```text
No EC2 server
No operating system management
No web server installation
No manual server deployment
```

Instead:

```text
Website Files
      ↓
AWS S3
      ↓
Website
```

This makes S3 a simple option for static content hosting.

* * *

# 🔐 Step 1 — Create an IAM User

Before GitHub Actions can upload files to S3, it needs permission to access AWS.

For this project, we create an IAM user for programmatic access.

IAM stands for:

> **Identity and Access Management**

AWS IAM allows us to control:

*   Who can access AWS
    
*   What resources they can access
    
*   What actions they can perform
    

* * *

# 👤 Why Do We Need IAM?

GitHub Actions needs to communicate with AWS.

The workflow needs AWS credentials so it can perform actions such as uploading website files.

The basic flow is:

```text
GitHub Actions
      |
      | AWS Credentials
      ↓
     IAM
      |
      ↓
    S3 Bucket
```

* * *

# ⚠️ Important Security Rule

Never write AWS credentials directly inside your GitHub workflow.

❌ Don't do this:

```yaml
aws_access_key_id: AKIAxxxxxxxx
aws_secret_access_key: xxxxxxxxx
```

If your repository is public, this can expose your credentials.

Instead, use:

```text
GitHub Secrets
```

We will configure this later.

* * *

# 📸 Screenshot 1 — IAM User

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/cf240226-aec4-44d5-8cc1-97ae1a0230fe.png align="center")

### Screenshot: IAM User Creation

This screenshot shows the IAM user created for the project.

The IAM user is used to provide controlled AWS access for the deployment workflow.

* * *

# 🪣 Step 2 — Create an S3 Bucket

Now we create an S3 bucket.

The bucket name used for this project is:

```text
hritik-portfolio1
```

The bucket will store the files of our portfolio.

For example:

```text
hritik-portfolio1
│
├── index.html
├── css/
├── js/
└── other assets
```

* * *

# 🏷️ Why Is the Bucket Name Important?

S3 bucket names must follow AWS naming requirements and are globally unique within the S3 namespace.

For this project, our bucket is:

```text
hritik-portfolio1
```

* * *

# 📸 Screenshot 2 — S3 Bucket Creation

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/90ffeeb7-b563-4c60-8d96-45969c2637ba.png align="center")

### Screenshot: S3 Bucket

This screenshot shows the S3 bucket created for hosting the portfolio website.

The bucket acts as the storage location for our static website files.

* * *

# ⚙️ Step 3 — Configure Static Website Hosting

Creating the bucket is not enough.

We also need to configure it to serve our website as a static website.

The important file is:

```text
index.html
```

This is the entry point of our portfolio.

The basic structure becomes:

```text
S3 Bucket
    |
    └── index.html
            |
            ├── CSS
            ├── JavaScript
            └── Other Assets
```

When a visitor opens the website, the `index.html` page is served as the main page.

* * *

# 🌐 Step 4 — Configure Website Access

For an S3 static website endpoint to serve content publicly, the required bucket/object access configuration must allow the intended website access.

This is an important AWS security concept.

You should avoid making more permissions public than necessary.

For a simple learning project, you may configure public website access as required by S3 static website hosting.

For a production website, consider a more secure architecture such as:

```text
CloudFront
    ↓
S3
```

instead of directly exposing the S3 website endpoint.

* * *

# 🧑‍💻 Step 5 — Prepare the Portfolio Website

Our portfolio is built using:

```text
HTML
CSS
JavaScript
```

The main file is:

```text
index.html
```

CSS:

```text
css/style.css
```

JavaScript:

```text
js/script.js
```

The project repository currently follows this basic structure.

* * *

# 📁 Project Structure

```text
hritik-portfolio1/
│
├── .github/
│   └── workflows/
│       └── deploy.yml
│
├── css/
│   └── style.css
│
├── js/
│   └── script.js
│
├── index.html
│
└── README.md
```

Let's understand it.

* * *

## `.github/workflows/`

This directory contains GitHub Actions workflow files.

Example:

```text
.github/workflows/deploy.yml
```

GitHub automatically detects workflow files stored in this directory.

* * *

## `index.html`

This is the main page of the portfolio.

* * *

## `css/style.css`

Contains the styling of the website.

* * *

## `js/script.js`

Contains JavaScript functionality.

* * *

## `README.md`

Contains project documentation.

* * *

# 🔄 Step 6 — Git Workflow

Before creating the CI/CD pipeline, our website source code needs to be available on GitHub.

The basic Git workflow is:

```bash
git status
```

Check the project status.

Then:

```bash
git add .
```

Stage all changes.

Then:

```bash
git commit -m "Add portfolio website"
```

Create a commit.

Finally:

```bash
git push
```

Push the changes to GitHub.

* * *

# 🤖 Step 7 — Create GitHub Actions Workflow

Now we create the CI/CD pipeline.

Inside the project:

```text
.github/
└── workflows/
    └── deploy.yml
```

The workflow file uses YAML.

GitHub Actions reads this file and executes the instructions automatically.

* * *

# 📝 GitHub Actions Workflow

A basic workflow for this project can look like this:

```yaml
name: Deploy Portfolio to AWS S3

on:
  push:
    branches:
      - main

jobs:

  deploy:

    runs-on: ubuntu-latest

    steps:

      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1

      - name: Deploy website to S3
        run: |
          aws s3 sync . s3://hritik-portfolio1 --delete
```

Let's understand this workflow step by step.

* * *

# 🧩 Understanding the Workflow

## 1\. Workflow Name

```yaml
name: Deploy Portfolio to AWS S3
```

This gives the workflow a readable name.

On GitHub, you can see this name in the Actions section.

* * *

# 2\. Trigger

```yaml
on:
  push:
    branches:
      - main
```

This means:

> Run the workflow whenever code is pushed to the `main` branch.

For example:

```text
Developer
    ↓
Modify index.html
    ↓
git add .
    ↓
git commit
    ↓
git push
    ↓
GitHub Actions starts
```

* * *

# 3\. Runner

```yaml
runs-on: ubuntu-latest
```

GitHub Actions creates a temporary Ubuntu environment to execute the workflow.

You can think of it as:

```text
GitHub
   ↓
Temporary Ubuntu Machine
   ↓
Execute Commands
   ↓
Finish
```

* * *

# 4\. Checkout Repository

```yaml
- name: Checkout repository
  uses: actions/checkout@v4
```

This action downloads the repository files into the GitHub Actions runner.

Without checking out the repository, the runner would not have the website files available for deployment.

* * *

# 5\. Configure AWS Credentials

```yaml
- name: Configure AWS credentials
  uses: aws-actions/configure-aws-credentials@v4
```

This allows the GitHub Actions runner to authenticate with AWS.

The credentials are retrieved from GitHub Secrets.

* * *

# 🔐 Step 8 — GitHub Secrets

This is one of the most important parts of the project.

We don't put AWS credentials directly in our code.

Instead, GitHub provides:

```text
Repository
   ↓
Settings
   ↓
Secrets and variables
   ↓
Actions
```

We can create secrets such as:

```text
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
```

The workflow then references:

```yaml
${{ secrets.AWS_ACCESS_KEY_ID }}
```

and:

```yaml
${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

* * *

# 🔒 Why GitHub Secrets?

Imagine writing:

```yaml
aws-access-key-id: AKIAxxxxxxxx
```

in a public repository.

Anyone could potentially see it.

Instead:

```text
GitHub Secret
     ↓
Encrypted/managed by GitHub
     ↓
GitHub Actions
     ↓
AWS
```

The actual secret value is not written into the workflow file.

* * *

# ⚠️ Very Important AWS Security Note

For a real production setup, avoid using a long-lived AWS access key when possible.

A stronger approach is **GitHub Actions OIDC with an AWS IAM role**.

The architecture becomes:

```text
GitHub Actions
      |
      | OIDC Identity
      ↓
AWS IAM Role
      |
      ↓
S3
```

This avoids storing long-lived AWS access keys in GitHub.

However, for a beginner learning project, understanding GitHub Secrets first is useful because it clearly demonstrates the basic authentication flow.

* * *

# 📤 Step 9 — Upload Website to S3

The most important deployment command is:

```bash
aws s3 sync . s3://hritik-portfolio1 --delete
```

Let's understand it.

* * *

# 🔄 What is `aws s3 sync`?

`aws s3 sync` synchronizes files between a local directory and an S3 bucket.

In our project:

```text
GitHub Actions Runner
        |
        | aws s3 sync
        ↓
S3 Bucket
```

The command:

```bash
aws s3 sync . s3://hritik-portfolio1
```

means:

> Upload/synchronize the files from the current directory to the S3 bucket.

* * *

# 🗑️ What Does `--delete` Do?

The workflow uses:

```bash
--delete
```

This makes the S3 bucket reflect the current contents of the source directory by deleting destination files that no longer exist in the source.

For example:

Initial version:

```text
index.html
old-page.html
style.css
```

Later you delete:

```text
old-page.html
```

After running:

```bash
aws s3 sync . s3://hritik-portfolio1 --delete
```

the old file can also be removed from the bucket.

This helps keep the deployed website synchronized with the repository.

* * *

# 🔁 Complete CI/CD Flow

Now let's connect everything.

```text
                 Developer
                     |
                     ↓
               Edit Website
                     |
                     ↓
                  Git
                     |
                git commit
                     |
                git push
                     |
                     ↓
              GitHub Repository
                     |
                     ↓
             GitHub Actions
                     |
                     ↓
             Ubuntu Runner
                     |
                     ↓
             Checkout Code
                     |
                     ↓
          Configure AWS Credentials
                     |
                     ↓
               AWS CLI
                     |
                     ↓
             aws s3 sync
                     |
                     ↓
              S3 Bucket
                     |
                     ↓
         Static Website Hosting
                     |
                     ↓
             🌐 Live Website
```

This is our CI/CD pipeline.

* * *

# 🚀 Step 10 — Push the Workflow to GitHub

Once `deploy.yml` is created:

```bash
git add .
```

Then:

```bash
git commit -m "Add S3 deployment workflow"
```

Then:

```bash
git push origin main
```

GitHub detects the workflow.

Because our workflow has:

```yaml
on:
  push:
    branches:
      - main
```

the pipeline starts automatically.

* * *

# 👀 Step 11 — Check GitHub Actions

Open your GitHub repository.

Go to:

```text
Actions
```

You should see:

```text
Deploy Portfolio to AWS S3
```

Click the workflow run.

You can see steps such as:

```text
✓ Checkout repository
✓ Configure AWS credentials
✓ Deploy website to S3
```

If every step succeeds:

```text
✓ Workflow completed successfully
```

* * *

# 🧪 Step 12 — Test Automatic Deployment

Now comes the most important part of the project.

Modify your portfolio.

For example:

```text
Change:
"DevOps Learner"

to:

"DevOps & Cloud Engineer"
```

Save the file.

Then:

```bash
git add .
```

```bash
git commit -m "Update portfolio content"
```

```bash
git push
```

Now:

```text
git push
    ↓
GitHub
    ↓
GitHub Actions
    ↓
AWS S3
    ↓
Updated Website
```

You don't manually upload anything.

That's the power of CI/CD.

* * *

# 🔥 Before Automation vs After Automation

## ❌ Traditional Manual Deployment

Without GitHub Actions:

```text
Change Website
     ↓
Build/Prepare Files
     ↓
Open AWS Console
     ↓
Open S3
     ↓
Upload Files
     ↓
Replace Old Files
     ↓
Check Website
```

Every update requires manual work.

* * *

# ✅ Automated Deployment

With GitHub Actions:

```text
Change Website
     ↓
git push
     ↓
GitHub Actions
     ↓
AWS S3
     ↓
Live Website Updated
```

Much simpler.

* * *

# 📊 Manual vs Automated Deployment

| Manual Deployment | CI/CD Deployment |
| --- | --- |
| Upload files manually | Automatic |
| More repetitive | Less repetitive |
| Easy to forget files | Automated synchronization |
| Takes more time | Faster |
| More human involvement | Pipeline-driven |
| Difficult to repeat consistently | Consistent workflow |

* * *

# 📸 Screenshot 3 — Final Live Portfolio

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/68ba1bee-dc8f-4e05-b5ab-87d618863578.png align="center")

### Screenshot: Final AWS S3 Hosted Portfolio

This screenshot shows the final portfolio website successfully running after deployment.

The website is accessible through the S3 static website endpoint:

http://hritik-portfolio1.s3-website-us-east-1.amazonaws.com

* * *

# 🎯 What Happens When I Push New Code?

Let's say I modify:

```text
index.html
```

Then:

```bash
git add .
```

```bash
git commit -m "Update portfolio"
```

```bash
git push
```

GitHub receives the code.

Because the workflow listens for pushes to `main`:

```yaml
on:
  push:
    branches:
      - main
```

GitHub Actions starts automatically.

Then:

```text
Checkout
   ↓
AWS Authentication
   ↓
AWS CLI
   ↓
S3 Sync
   ↓
Deployment Complete
```

The updated website is now available from S3.

* * *

# 🧠 Important DevOps Concepts Learned

This small project teaches several important concepts.

* * *

## 1️⃣ Version Control

Git tracks changes to the website.

```text
Code
 ↓
Git
 ↓
GitHub
```

* * *

## 2️⃣ CI/CD

GitHub Actions automates deployment.

```text
Push
 ↓
Pipeline
 ↓
Deploy
```

* * *

## 3️⃣ Cloud Storage

S3 stores the website files.

```text
S3
 ↓
index.html
CSS
JavaScript
Assets
```

* * *

## 4️⃣ IAM

IAM controls AWS access.

```text
Identity
 +
Permissions
 =
Controlled AWS Access
```

* * *

## 5️⃣ Secrets Management

GitHub Secrets protect sensitive credentials from being hardcoded into the repository.

* * *

## 6️⃣ AWS CLI

AWS CLI allows us to interact with AWS from commands and automation.

Example:

```bash
aws s3 sync
```

* * *

## 7️⃣ Infrastructure + Automation

AWS provides the infrastructure.

GitHub Actions provides the automation.

Together:

```text
AWS
 +
GitHub Actions
 =
Automated Deployment
```

* * *

# 🏗️ Project Architecture

The final architecture can be represented as:

```text
                  ┌──────────────────┐
                  │    Developer     │
                  └────────┬─────────┘
                           │
                       git push
                           │
                           ↓
                  ┌──────────────────┐
                  │     GitHub       │
                  │   Repository     │
                  └────────┬─────────┘
                           │
                           ↓
                  ┌──────────────────┐
                  │ GitHub Actions   │
                  │      CI/CD       │
                  └────────┬─────────┘
                           │
                           ↓
                  ┌──────────────────┐
                  │   AWS CLI /      │
                  │ AWS Credentials  │
                  └────────┬─────────┘
                           │
                           ↓
                  ┌──────────────────┐
                  │    AWS S3        │
                  │     Bucket       │
                  └────────┬─────────┘
                           │
                           ↓
                  ┌──────────────────┐
                  │ Static Website   │
                  │    Hosting       │
                  └────────┬─────────┘
                           │
                           ↓
                       🌐 User
```

* * *

# 📁 Final Repository Structure

The project structure is:

```text
hritik-portfolio1/
│
├── .github/
│   └── workflows/
│       └── deploy.yml
│
├── css/
│   └── style.css
│
├── js/
│   └── script.js
│
├── index.html
│
└── README.md
```

The repository currently shows this core structure on GitHub.

* * *

# 🧩 Understanding Each Component

## HTML

Responsible for the structure.

```html
<h1>My Portfolio</h1>
```

* * *

## CSS

Responsible for styling.

```css
body {
    font-family: Arial, sans-serif;
}
```

* * *

## JavaScript

Adds functionality.

```javascript
console.log("Portfolio loaded");
```

* * *

## Git

Tracks changes.

```bash
git add .
git commit -m "Update portfolio"
```

* * *

## GitHub

Stores the source code remotely.

* * *

## GitHub Actions

Automates deployment.

* * *

## IAM

Provides AWS identity and permissions.

* * *

## S3

Stores and serves the static website files.

* * *

# 🔐 Security Considerations

Security is extremely important in AWS projects.

There are several things to remember.

* * *

## ❌ Never Commit AWS Credentials

Never put this directly into:

```text
deploy.yml
README.md
index.html
```

or any other repository file:

```text
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
```

* * *

## ✅ Use GitHub Secrets

Store sensitive credentials in:

```text
GitHub Repository
      ↓
Settings
      ↓
Secrets and variables
      ↓
Actions
```

* * *

## ✅ Use Least Privilege

The IAM identity used for deployment should have only the permissions required for the deployment.

For this project, that generally means restricting access to the target S3 bucket and only the necessary S3 actions.

Avoid giving broad permissions such as unrestricted administrator access just to make the deployment work.

* * *

# 🔐 Production-Level Improvement: OIDC

For learning purposes, GitHub Secrets are easy to understand.

But for a more production-oriented setup, GitHub Actions can authenticate to AWS using **OIDC** and an IAM role.

Instead of:

```text
GitHub
   ↓
Long-Lived AWS Access Key
```

you can use:

```text
GitHub Actions
       ↓
OIDC
       ↓
AWS IAM Role
       ↓
S3
```

Advantages include:

*   No long-lived AWS access keys in GitHub
    
*   Short-lived credentials
    
*   Better security
    
*   Fine-grained trust policies
    

This is an excellent next step after completing this beginner project.

* * *

# 🌍 Why This Project is Useful for DevOps Beginners

At first glance, this looks like a simple website deployment.

But it teaches the complete idea behind a CI/CD pipeline.

You learn:

```text
Source Code
    ↓
Version Control
    ↓
Remote Repository
    ↓
Automation
    ↓
Cloud Authentication
    ↓
Cloud Storage
    ↓
Deployment
```

These same concepts appear in much larger systems.

For example:

```text
Java Application
      ↓
GitHub
      ↓
GitHub Actions
      ↓
Docker
      ↓
AWS ECR
      ↓
EC2 / ECS / Kubernetes
```

The technology changes, but the DevOps workflow remains similar.

* * *

# 📈 How This Project Can Be Improved

This project can be extended in several ways.

* * *

## 🚀 Improvement 1 — Add CloudFront

Instead of directly serving the website from S3:

```text
User
 ↓
CloudFront
 ↓
S3
```

CloudFront provides a CDN layer.

* * *

## 🔒 Improvement 2 — Use HTTPS

Instead of relying on the basic S3 website endpoint, a production architecture can use:

```text
CloudFront
   ↓
HTTPS
   ↓
S3
```

* * *

## 🌐 Improvement 3 — Add a Custom Domain

For example:

```text
www.example.com
```

using:

```text
Route 53
+
CloudFront
+
S3
```

* * *

## 🔐 Improvement 4 — Use OIDC

Replace long-lived AWS credentials with:

```text
GitHub Actions
       ↓
OIDC
       ↓
IAM Role
       ↓
S3
```

* * *

## 🧪 Improvement 5 — Add Testing

Before deployment:

```text
Push
 ↓
HTML Validation
 ↓
CSS Validation
 ↓
JavaScript Check
 ↓
Deploy
```

* * *

## 🔍 Improvement 6 — Add Security Scanning

The workflow can also include:

```text
Secret Scanning
Dependency Scanning
Security Checks
```

before deployment.

* * *

# 🧪 Example Improved Pipeline

A more advanced version could look like:

```text
Developer
    ↓
git push
    ↓
GitHub
    ↓
GitHub Actions
    ↓
Checkout
    ↓
Validate
    ↓
Test
    ↓
Security Scan
    ↓
AWS Authentication
    ↓
S3 Sync
    ↓
CloudFront Cache Invalidation
    ↓
Production
```

This is much closer to a real-world DevOps workflow.

* * *

# 🧑‍💻 Complete Deployment Commands

Here are the important commands used in the project.

### Check Git status

```bash
git status
```

### Stage files

```bash
git add .
```

### Commit changes

```bash
git commit -m "Update portfolio"
```

### Push changes

```bash
git push origin main
```

### AWS S3 synchronization

```bash
aws s3 sync . s3://hritik-portfolio1 --delete
```

The last command is the core deployment command used by the CI/CD workflow.

* * *

# 🔄 Complete Project Workflow in One Diagram

```text
                ┌───────────────────┐
                │   Portfolio Code  │
                │ HTML/CSS/JS       │
                └─────────┬─────────┘
                          │
                       Git Push
                          │
                          ↓
                ┌───────────────────┐
                │      GitHub       │
                │    Repository     │
                └─────────┬─────────┘
                          │
                          ↓
                ┌───────────────────┐
                │  GitHub Actions   │
                │      CI/CD        │
                └─────────┬─────────┘
                          │
                          ↓
                ┌───────────────────┐
                │ Checkout Source   │
                └─────────┬─────────┘
                          │
                          ↓
                ┌───────────────────┐
                │ AWS Authentication│
                └─────────┬─────────┘
                          │
                          ↓
                ┌───────────────────┐
                │     AWS CLI       │
                │   aws s3 sync     │
                └─────────┬─────────┘
                          │
                          ↓
                ┌───────────────────┐
                │    S3 Bucket      │
                │ hritik-portfolio1 │
                └─────────┬─────────┘
                          │
                          ↓
                ┌───────────────────┐
                │ Static Website    │
                │     Hosting       │
                └─────────┬─────────┘
                          │
                          ↓
                🌐 Live Portfolio
```

* * *

# 💡 What I Learned From This Project

This project helped me understand how a simple website can become an automated DevOps deployment.

The major concepts I practiced were:

```text
Git
GitHub
GitHub Actions
AWS IAM
AWS S3
AWS CLI
GitHub Secrets
CI/CD
Static Website Hosting
Cloud Deployment
```

The most important lesson was:

> **Deployment does not have to be a manual process.**

Instead of uploading files manually every time, we can automate the entire process:

```text
Code Change
    ↓
git push
    ↓
GitHub Actions
    ↓
AWS S3
    ↓
Live Website
```

* * *

# 🏆 Final Result

The final result is a portfolio website hosted on Amazon S3 and deployed through a GitHub Actions workflow.

### GitHub Repository

https://github.com/hritikranjan1/hritik-portfolio1

### Live Portfolio

http://hritik-portfolio1.s3-website-us-east-1.amazonaws.com

### Workshop

https://www.youtube.com/live/DyqAdz96mok?si=yTWM7TqpWvtRsDTU&t=10442

* * *

# 📸 Project Screenshots

## 1\. IAM User Creation

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/71e9b3ba-b7c7-4e50-a7ba-5af8134b47a2.png align="center")

**What it demonstrates:** Creation/configuration of the AWS identity used for the deployment process.

* * *

## 2\. S3 Bucket Creation

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/8c7e5062-980c-4106-ade4-de8fc60bf68d.png align="center")

**What it demonstrates:** The `hritik-portfolio1` S3 bucket created to store the static website files.

* * *

## 3\. Final Live Portfolio

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/ae88235c-9589-4891-92dd-40631bc2b436.png align="center")

**What it demonstrates:** The final portfolio successfully deployed and accessible through the AWS S3 website endpoint.

* * *

# 📌 Key Takeaways

If you are a beginner, remember these five things:

### 1\. GitHub stores the source code

```text
Portfolio → GitHub
```

### 2\. GitHub Actions automates the deployment

```text
git push → GitHub Actions
```

### 3\. IAM controls AWS access

```text
IAM → Permissions
```

### 4\. S3 stores and serves the static website

```text
S3 → Website Files
```

### 5\. CI/CD removes repetitive manual deployment

```text
Code Change
     ↓
Push
     ↓
Automatic Deployment
```

* * *

# 🎯 Final DevOps Architecture

The complete project can be summarized as:

```text
                 👨‍💻 Developer
                       |
                       |
                    Git Push
                       |
                       ↓
              ☁️ GitHub Repository
                       |
                       ↓
               ⚙️ GitHub Actions
                       |
                       ↓
                🐧 Ubuntu Runner
                       |
                       ↓
                🔐 AWS IAM
                       |
                       ↓
                 ☁️ AWS S3
                       |
                       ↓
             🌐 Static Website
                       |
                       ↓
                👥 End Users
```

This is a small project, but it demonstrates a **real DevOps concept: automatically moving code from source control to a cloud-hosted environment through a CI/CD pipeline.**

* * *

# 🚀 Conclusion

Deploying a portfolio website to S3 manually is easy.

But automating the deployment with **GitHub Actions** is where the DevOps learning begins.

In this project, we connected:

```text
HTML
CSS
JavaScript
   +
Git
   +
GitHub
   +
GitHub Actions
   +
IAM
   +
AWS CLI
   +
Amazon S3
```

The final result is an automated deployment pipeline:

```text
                    CODE
                     ↓
                  GITHUB
                     ↓
              GITHUB ACTIONS
                     ↓
                AWS AUTH
                     ↓
                  AWS S3
                     ↓
              LIVE WEBSITE
```

Now, whenever I update my portfolio and push the changes to GitHub, GitHub Actions can automatically synchronize the latest files with my S3 bucket.

That's the real power of CI/CD:

> **Build once. Automate the process. Deploy consistently. 🚀**

If you're a beginner learning DevOps, this is a great project to build yourself because it combines **Git, GitHub, CI/CD, AWS IAM, S3, AWS CLI, secrets management, and static website hosting** in one practical project.

**Happy Dockering!**

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/d52bb675-1b82-4184-9cc5-688d297a52b7.png align="center")

# 🚀 Complete Learning & Career Resources | 2027–2028

**A curated collection of learning resources for AI, Data Analytics, Python, Data Engineering, Cybersecurity, Cloud, Networking, Finance, Digital Marketing, Project Management, DevOps and Generative AI.**

📚 Learn  →  🧪 Practice  →  🛠️ Build  →  🐙 Share  →  🚀 Grow

[![](https://img.shields.io/badge/GitHub-hritikranjan1-181717?style=for-the-badge&logo=github&logoColor=white align="center")](https://github.com/hritikranjan1)

[![](https://img.shields.io/badge/Portfolio-hritikranjan.in-36BCF7?style=for-the-badge align="center")](https://hritikranjan.in)

[![](https://img.shields.io/badge/Tech%20Blog-Read%20Articles-orange?style=for-the-badge align="center")](https://blogs.hritikranjan.in/)

[![](https://img.shields.io/badge/Telegram-Join%20Channel-26A5E4?style=for-the-badge&logo=telegram&logoColor=white align="center")](https://t.me/codewithluv143)

![](https://img.shields.io/badge/AI-%F0%9F%A4%96-8A2BE2?style=flat-square align="center")

![](https://img.shields.io/badge/Data-%F0%9F%93%8A-36BCF7?style=flat-square align="center")

![](https://img.shields.io/badge/Python-%F0%9F%90%8D-3776AB?style=flat-square align="center")

![](https://img.shields.io/badge/Cloud-%E2%98%81%EF%B8%8F-4285F4?style=flat-square align="center")

![](https://img.shields.io/badge/Cybersecurity-%F0%9F%94%90-111111?style=flat-square align="center")

![](https://img.shields.io/badge/DevOps-%E2%9A%99%EF%B8%8F-0A0A0A?style=flat-square align="center")

![](https://img.shields.io/badge/Career-%F0%9F%9A%80-success?style=flat-square align="center")

* * *

# 🌟 About This Repository

Welcome to the **Complete Learning & Career Resources Repository**! 🚀

This repository is designed as a centralized learning hub for students, developers, QA engineers, DevOps engineers, cloud learners, cybersecurity enthusiasts, data professionals, project managers, business professionals and anyone interested in continuous learning.

The goal is simple:

> **Learn → Practice → Build → Document → Share → Grow**

Instead of searching for useful resources again and again, this repository brings them together in one place.

* * *

# 🎯 What You Will Find Here

*   🤖 Artificial Intelligence
    
*   🧠 Generative AI
    
*   📊 Data Analytics
    
*   🐍 Python
    
*   ⚙️ Data Engineering
    
*   ☁️ Cloud Computing
    
*   🌐 Computer Networking
    
*   🔐 Cybersecurity
    
*   ⚙️ DevOps
    
*   📋 Project Management
    
*   💰 Finance
    
*   📈 Digital Marketing
    
*   🧩 Business Analysis
    
*   🚀 Career Development
    
*   🎓 Professional Learning
    
*   🛠️ Project Ideas
    
*   📚 Learning Roadmaps
    

* * *

# 📊 Repository Overview

| Category | Resources |
| --- | --- |
| 🤖 AI Courses | 15 |
| 🔵 Google Courses | 15 |
| 🟣 IBM Courses | 10 |
| 🔥 Best Courses 2027–2028 | 21 |
| 🌟 Learning & Career Resources | 14 |
| 📖 Personal Resources | 4+ |

* * *

# 📚 Table of Contents

*   [🌟 About This Repository](#-about-this-repository)
    
*   [🎯 What You Will Find Here](#-what-you-will-find-here)
    
*   [📊 Repository Overview](#-repository-overview)
    
*   [🤖 AI Courses](#-ai-courses)
    
*   [🔵 Google Courses](#-google-courses)
    
*   [🟣 IBM Courses](#-ibm-courses)
    
*   [🔥 Best Courses 2027–2028](#-best-courses-20272028)
    
*   [🌟 Learning & Career Resources](#-learning--career-resources)
    
*   [🗺️ Recommended Learning Roadmaps](#%EF%B8%8F-recommended-learning-roadmaps)
    
*   [📊 Data Analytics Roadmap](#-data-analytics-roadmap)
    
*   [🐍 Python Roadmap](#-python-roadmap)
    
*   [☁️ Cloud & DevOps Roadmap](#%EF%B8%8F-cloud--devops-roadmap)
    
*   [🔐 Cybersecurity Roadmap](#-cybersecurity-roadmap)
    
*   [🤖 AI Roadmap](#-ai-roadmap)
    
*   [🧪 How to Learn Effectively](#-how-to-learn-effectively)
    
*   [🛠️ Project Ideas](#%EF%B8%8F-project-ideas)
    
*   [📂 Recommended GitHub Project Structure](#-recommended-github-project-structure)
    
*   [📈 Career Roadmap](#-career-roadmap)
    
*   [💡 Learning Checklist](#-learning-checklist)
    
*   [🧠 Golden Rules](#-golden-rules)
    
*   [📖 My Resources](#-my-resources)
    
*   [🌐 Useful Links](#-useful-links)
    
*   [⭐ Support This Repository](#-support-this-repository)
    
*   [🔄 Future Updates](#-future-updates)
    
*   [⚠️ Affiliate Disclosure](#%EF%B8%8F-affiliate-disclosure)
    

* * *

# 🤖 AI Courses

> 🚀 Explore AI fundamentals, Python, AI infrastructure, Generative AI, AI governance and specialized AI applications.

| # | Course | Link |
| --- | --- | --- |
| 1 | AI For Everyone | [Start Course ↗](https://imp.i384100.net/jeaEZ5) |
| 2 | AI Python for Beginners | [Start Course ↗](https://imp.i384100.net/B5bEAy) |
| 3 | AI Infrastructure and Operations Fundamentals | [Start Course ↗](https://imp.i384100.net/OYEqWG) |
| 4 | Generative AI for Human Resources (HR) Professionals | [Start Course ↗](https://imp.i384100.net/dyrBry) |
| 5 | AI Fundamentals | [Start Course ↗](https://imp.i384100.net/bkQXqv) |
| 6 | AI for Healthcare | [Start Course ↗](https://imp.i384100.net/qWoMoO) |
| 7 | AI Applications in Accounting and Finance | [Start Course ↗](https://imp.i384100.net/DWaoaq) |
| 8 | AI Governance and Privacy Professional Certification (AIGP) | [Start Course ↗](https://imp.i384100.net/Pznxnq) |
| 9 | Ethics and Governance in the Age of Generative AI | [Start Course ↗](https://imp.i384100.net/1GzxzB) |
| 10 | Hands-on quantum error correction with Google Quantum AI | [Start Course ↗](https://imp.i384100.net/zzOMO7) |
| 11 | AI-Powered Higher Education | [Start Course ↗](https://imp.i384100.net/MKEOYN) |
| 12 | Modern Project Leadership: Agile, AI, and Beyond | [Start Course ↗](https://imp.i384100.net/qWoMGq) |
| 13 | AI-Powered Business Analysis: Excel, KPIs & GenAI | [Start Course ↗](https://imp.i384100.net/9VqkBY) |
| 14 | AI in Law: Research, Risk, and Legal Drafting | [Start Course ↗](https://imp.i384100.net/5kzrBo) |
| 15 | Generative AI for Project Managers | [Start Course ↗](https://imp.i384100.net/Gb1WY6) |

* * *

# 🔵 Google Courses

> 🌐 Explore Data Analytics, AI, Cybersecurity, Networking, Cloud, Digital Marketing and Project Management.

| # | Course | Link |
| --- | --- | --- |
| 1 | Foundations: Data, Data, Everywhere | [Start Course ↗](https://imp.i384100.net/jRZX4a) |
| 2 | Ask Questions to Make Data-Driven Decisions | [Start Course ↗](https://imp.i384100.net/Gb1WEm) |
| 3 | Prepare Data for Exploration | [Start Course ↗](https://imp.i384100.net/zzOMRr) |
| 4 | Agile Project Management | [Start Course ↗](https://imp.i384100.net/qWoMVY) |
| 5 | Project Initiation: Starting a Successful Project | [Start Course ↗](https://imp.i384100.net/JkZnjq) |
| 6 | AI Fundamentals | [Start Course ↗](https://imp.i384100.net/bkQXqv) |
| 7 | Foundations of Digital Marketing and E-commerce | [Start Course ↗](https://imp.i384100.net/YVKejP) |
| 8 | Play It Safe: Manage Security Risks | [Start Course ↗](https://imp.i384100.net/aNDgLR) |
| 9 | The Bits and Bytes of Computer Networking | [Start Course ↗](https://imp.i384100.net/L0E65M) |
| 10 | Analyze Data to Answer Questions | [Start Course ↗](https://imp.i384100.net/vDmM0v) |
| 11 | Automate Cybersecurity Tasks with Python | [Start Course ↗](https://imp.i384100.net/YVKe3e) |
| 12 | Architecting with Google Compute Engine | [Start Course ↗](https://imp.i384100.net/jRabAM) |
| 13 | AI for Writing and Communicating | [Start Course ↗](https://imp.i384100.net/9Vqk3E) |
| 14 | From Likes to Leads: Interact with Customers Online | [Start Course ↗](https://imp.i384100.net/YVKexr) |
| 15 | AI for Data Analysis | [Start Course ↗](https://imp.i384100.net/L0E6q0) |

* * *

# 🟣 IBM Courses

> 💙 Explore SQL, Python, Data Analytics, Deep Learning, RAG and Generative AI resources.

| # | Course | Link |
| --- | --- | --- |
| 1 | Databases and SQL for Data Science with Python | [Start Course ↗](https://imp.i384100.net/9VqkPE) |
| 2 | RAG and Agentic AI Capstone Project | [Start Course ↗](https://imp.i384100.net/Pznx9R) |
| 3 | Excel Basics for Data Analysis | [Start Course ↗](https://imp.i384100.net/Gb1WB2) |
| 4 | Introduction to Data Analytics | [Start Course ↗](https://imp.i384100.net/1GzxLz) |
| 5 | Data Visualization and Dashboards with Excel and Cognos | [Start Course ↗](https://imp.i384100.net/X4EkA3) |
| 6 | IBM AI Foundations for Business | [Start Course ↗](https://imp.i384100.net/zzOM3G) |
| 7 | AI Capstone Project with Deep Learning | [Start Course ↗](https://imp.i384100.net/6kzj9m) |
| 8 | Python Project for Data Engineering | [Start Course ↗](https://imp.i384100.net/B5kge9) |
| 9 | Building Generative AI-Powered Applications with Python | [Start Course ↗](https://imp.i384100.net/MKEOzn) |
| 10 | Vector Databases for RAG: An Introduction | [Start Course ↗](https://imp.i384100.net/m41MqO) |

* * *

# 🔥 Best Courses 2027–2028

> 🎯 A broader collection covering AI, Data, Python, Finance, Cybersecurity, Marketing, Networking, Management and Data Engineering.

| # | Course | Link |
| --- | --- | --- |
| 1 | AI For Everyone | [Start Course ↗](https://imp.i384100.net/jeaEZ5) |
| 2 | Foundations: Data, Data, Everywhere | [Start Course ↗](https://imp.i384100.net/jRZX4a) |
| 3 | Ask Questions to Make Data-Driven Decisions | [Start Course ↗](https://imp.i384100.net/Gb1Wem) |
| 4 | Prepare Data for Exploration | [Start Course ↗](https://imp.i384100.net/zzOMRr) |
| 5 | Financial Markets | [Start Course ↗](https://imp.i384100.net/7Xoexg) |
| 6 | Agile Project Management | [Start Course ↗](https://imp.i384100.net/qWoMVY) |
| 7 | Play It Safe: Manage Security Risks | [Start Course ↗](https://imp.i384100.net/aNDgLR) |
| 8 | Project Initiation: Starting a Successful Project | [Start Course ↗](https://imp.i384100.net/JkZnjq) |
| 9 | AI Fundamentals | [Start Course ↗](https://imp.i384100.net/bkQXqv) |
| 10 | Analyze Data to Answer Questions | [Start Course ↗](https://imp.i384100.net/vDmM0v) |
| 11 | Foundations of Digital Marketing and E-commerce | [Start Course ↗](https://imp.i384100.net/YVKejP) |
| 12 | The Bits and Bytes of Computer Networking | [Start Course ↗](https://imp.i384100.net/L0E65M) |
| 13 | Sequence Models | [Start Course ↗](https://imp.i384100.net/rEWM0v) |
| 14 | Federal Taxation I: Individuals, Employees, and Sole Proprietors | [Start Course ↗](https://imp.i384100.net/k4A6kL) |
| 15 | Designing the Organization | [Start Course ↗](https://imp.i384100.net/enjzQO) |
| 16 | Game Theory | [Start Course ↗](https://imp.i384100.net/L0E6oa) |
| 17 | Using Python to Access Web Data | [Start Course ↗](https://imp.i384100.net/5kzrmn) |
| 18 | Viral Marketing and How to Craft Contagious Content | [Start Course ↗](https://imp.i384100.net/JkZnoQ) |
| 19 | Python Project for Data Engineering | [Start Course ↗](https://imp.i384100.net/B5kge9) |
| 20 | Value Chain Management | [Start Course ↗](https://imp.i384100.net/OYEqoA) |
| 21 | Applying Data Analytics in Finance | [Start Course ↗](https://imp.i384100.net/4aM9R1) |

* * *

# 🌟 Learning & Career Resources

> 💡 Additional resources for learning, career development, language learning, hosting, education and professional growth.

| Category | Program | Tracking Link |
| --- | --- | --- |
| 📱 Apps | **AppSumo** | https://appsumo.8odi.net/c/5203965/416948/7443 |
| 🌐 Website Hosting | **Automattic, Inc. (WordPress.com, Pressable, WooCommerce, Jetpack)** | https://automattic.pxf.io/c/5203965/1900456/22744 |
| 🇬🇧 College | **British Council - EOL English Online** | https://englishonline.sjv.io/c/5203965/1152772/14579 |
| 📚 Educational | **Carson Dellosa Education** | https://carsondellosaeducation.sjv.io/c/5203965/2241626/29119 |
| 🎓 College | **Coursera B2C Affiliate Program** | https://imp.i384100.net/c/5203965/1164545/14726 |
| 📊 Learning | **DataCamp** | https://datacamp.pxf.io/c/5203965/1012793/13294 |
| 🎨 Collectibles & Hobbies | **Domestika** | https://domestika.sjv.io/c/5203965/1492994/17608 |
| 🎓 College | **edX** | https://edx.sjv.io/c/5203965/1505390/17728 |
| 💼 Career | **Medical Spanish** | https://curiositymediainc.sjv.io/c/5203965/2899794/33984 |
| 🧪 Educational | **MEL Science** | https://imp.i328067.net/c/5203965/574569/9515 |
| 🗣️ Apps | **Preply Learners** | https://preply.sjv.io/c/5203965/1987575/24422 |
| 🌍 Learning | **Rosetta Stone** | https://aff.rosettastone.com/c/5203965/1637427/18979 |
| 🛍️ Website Hosting | **Shopify** | https://shopify.pxf.io/c/5203965/1061744/13624 |
| 🎯 Learning | **Udemy** | https://trk.udemy.com/c/5203965/3193860/39854 |

* * *

# 🗺️ Recommended Learning Roadmaps

> Choose one roadmap according to your career goal. You don't need to learn everything at once.

* * *

# 🤖 AI Roadmap

```text
AI Fundamentals
      ↓
Python Basics
      ↓
Mathematics & Statistics
      ↓
Data Fundamentals
      ↓
Machine Learning
      ↓
Deep Learning
      ↓
Generative AI
      ↓
Prompt Engineering
      ↓
RAG
      ↓
Vector Databases
      ↓
Agentic AI
      ↓
AI Applications
      ↓
Real-World Projects
      ↓
GitHub Portfolio
```

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/5d7a1a0d-3891-47ed-a6eb-8508aca5dd73.png align="center")