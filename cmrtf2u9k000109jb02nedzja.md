---
title: "🚀 IaC with AWS CloudFormation (CFT) | Complete Beginner Guide with Hands-on Examples"
seoTitle: "AWS CloudFormation (CFT) Complete Beginner Guide | IaC"
seoDescription: "Learn AWS CloudFormation (CFT) from scratch with IaC, YAML templates, Drift Detection, hands-on examples, and CFT vs Terraform."
datePublished: 2026-07-20T16:06:19.092Z
cuid: cmrtf2u9k000109jb02nedzja
slug: iac-aws-cloudformation-complete-guide
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/a9d7eb1c-636f-43f5-a1bf-f9e696d915f4.png
tags: cloudformation, aws, cloud-computing, devops, yaml, terraform, infrastructure-as-code, iac, terraform-cloud

---

# 📖 Introduction

As cloud infrastructure grows, manually creating AWS resources becomes time-consuming, error-prone, and difficult to manage.

Imagine creating:

*   20 EC2 Instances
    
*   15 S3 Buckets
    
*   8 IAM Roles
    
*   10 Security Groups
    
*   5 VPCs
    

every time you deploy an application.

Sounds impossible, right?

This is where **Infrastructure as Code (IaC)** comes into the picture.

Instead of creating infrastructure manually from the AWS Console, we define everything in code.

AWS provides its own IaC service called **CloudFormation (CFT)**.

In this guide, we'll learn everything about CloudFormation in a beginner-friendly way.

* * *

# 📚 Table of Contents

*   What is Infrastructure as Code (IaC)?
    
*   Why do we need IaC?
    
*   Problems with Manual Infrastructure
    
*   What is AWS CloudFormation?
    
*   How CloudFormation Works
    
*   CloudFormation Architecture
    
*   CloudFormation Components
    
*   Anatomy of a CloudFormation Template
    
*   Resources Section
    
*   Parameters
    
*   Outputs
    
*   Mappings
    
*   Conditions
    
*   Metadata
    
*   YAML vs JSON
    
*   Creating First CloudFormation Stack
    
*   Deploying an S3 Bucket
    
*   Stack Lifecycle
    
*   Change Sets
    
*   Drift Detection
    
*   CloudFormation Designer
    
*   CloudFormation Best Practices
    
*   CloudFormation vs Terraform
    
*   Advantages & Limitations
    
*   Real World Use Cases
    
*   Interview Questions
    
*   Conclusion
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/85045123-197b-44fd-8439-c7c33c96d691.png align="center")

# ☁️ What is Infrastructure as Code (IaC)?

Infrastructure as Code (IaC) means creating and managing cloud infrastructure using code instead of manually clicking through the AWS Console.

Instead of logging into AWS and creating resources one by one, you write a template that describes your infrastructure.

AWS automatically creates everything from that template.

Think of IaC like a blueprint for your infrastructure.

Just as architects use blueprints to construct buildings, DevOps engineers use IaC templates to build cloud infrastructure.

* * *

# 🤔 Why Do We Need Infrastructure as Code?

Without IaC:

*   Manual work
    
*   Human errors
    
*   Inconsistent environments
    
*   Difficult deployments
    
*   Slow provisioning
    
*   Hard to reproduce infrastructure
    

With IaC:

*   Automation
    
*   Consistency
    
*   Repeatability
    
*   Version control
    
*   Faster deployments
    
*   Easy disaster recovery
    

* * *

# ❌ Problems with Manual Infrastructure

Suppose you have to deploy an application.

You manually create:

*   EC2 Instance
    
*   VPC
    
*   Security Group
    
*   S3 Bucket
    
*   IAM Role
    
*   Load Balancer
    

Next month, you need the same infrastructure for testing.

You repeat everything again.

There is a high chance of:

*   Missing configurations
    
*   Wrong security rules
    
*   Different instance types
    
*   Incorrect subnet configuration
    

IaC solves all these problems.

* * *

![]( align="center")

# ☁️ What is AWS CloudFormation?

AWS CloudFormation is an Infrastructure as Code (IaC) service that allows you to create, update, and manage AWS resources using YAML or JSON templates.

Instead of manually provisioning resources, you define them in a template, and CloudFormation automatically creates everything for you.

* * *

# 🏗️ Real-Life Example

Imagine you're building a house.

Instead of explaining every room to the workers every day, you give them a blueprint.

They build the same house every time.

CloudFormation works exactly the same way.

Your YAML file is the blueprint.

AWS builds the infrastructure.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/c3f89752-b247-4653-b950-9fbc044092d3.png align="center")

# ⚙️ How CloudFormation Works

```plaintext
Developer

↓

Write YAML Template

↓

CloudFormation Stack

↓

AWS APIs

↓

AWS Resources Created
```

CloudFormation acts as a middle layer between your template and AWS services.

* * *

# 🏛 CloudFormation Architecture

```plaintext
Template (YAML/JSON)

↓

CloudFormation

↓

AWS APIs

↓

EC2
S3
IAM
VPC
Lambda
RDS
CloudFront
Load Balancer
Security Groups
```

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/5a32fbbf-48ae-4c90-9b21-ea644aa48e89.png align="center")

# 📄 What is a CloudFormation Template?

A template is simply a YAML or JSON file containing all the infrastructure details.

Example:

```plaintext
Create

1 EC2
1 S3 Bucket
1 IAM Role
1 Security Group
```

Everything is defined inside one file.

* * *

# 🧩 Components of a CloudFormation Template

A CloudFormation template can include:

*   AWSTemplateFormatVersion
    
*   Description
    
*   Metadata
    
*   Parameters
    
*   Mappings
    
*   Conditions
    
*   Resources ✅ (Mandatory)
    
*   Outputs
    

👉 **Resources** is the only mandatory section. All other sections are optional.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/5d402a22-2e3a-4619-96a2-fb4bddb5f5e3.png align="center")

# 📌 Resources (Most Important Section)

The **Resources** section defines the AWS services that CloudFormation will create.

Example resources:

*   EC2 Instance
    
*   S3 Bucket
    
*   Lambda Function
    
*   IAM Role
    
*   Security Group
    
*   RDS Database
    
*   VPC
    

Without this section, CloudFormation cannot create anything.

* * *

# 🎯 Parameters

Parameters allow users to provide values during stack creation instead of hardcoding them.

Examples:

*   Instance Type
    
*   Bucket Name
    
*   Region
    
*   Environment (Dev, Test, Prod)
    

Benefits:

*   Reusable templates
    
*   Flexible deployments
    
*   Better customization
    

* * *

# 📤 Outputs

Outputs display useful information after deployment.

Examples:

*   EC2 Public IP
    
*   Load Balancer DNS
    
*   Bucket Name
    
*   VPC ID
    

This saves time by providing important values immediately after stack creation.

* * *

# 🗺️ Mappings

Mappings help define different values for different regions or environments.

Example:

*   Mumbai → AMI A
    
*   Virginia → AMI B
    

This avoids hardcoding region-specific values.

* * *

# 🔀 Conditions

Conditions allow CloudFormation to create resources only if specific criteria are met.

Example:

If Environment = Production

Create:

*   RDS Database
    
*   Auto Scaling Group
    

Else

Skip those resources.

* * *

# 📝 Metadata

Metadata stores additional information about the template.

It doesn't create resources but helps document and organize your infrastructure.

* * *

# 📄 YAML vs JSON

CloudFormation supports:

*   YAML ✅ (Recommended)
    
*   JSON
    

YAML is easier to read, cleaner, and widely used in DevOps projects.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/5a1dbc15-56ca-445f-988e-ab05d3da8897.png align="center")

# 🚀 Creating Your First CloudFormation Stack

### Step 1

Open AWS Console

↓

CloudFormation

* * *

### Step 2

Create Stack

* * *

### Step 3

Upload YAML Template

* * *

### Step 4

Provide Stack Name

* * *

### Step 5

Review Configuration

* * *

### Step 6

Click **Create Stack**

CloudFormation automatically provisions all resources.

* * *

# 🪣 Demo Project – Create an S3 Bucket

CloudFormation Template:

```yaml
AWSTemplateFormatVersion: '2010-09-09'

Description: Create S3 Bucket

Resources:

  MyBucket:

    Type: AWS::S3::Bucket

    Properties:

      BucketName: my-demo-cloudformation-bucket
```

Deploy the template.

Within seconds, AWS creates the S3 bucket automatically.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/6f981477-caa1-4a45-bf8c-1632de598302.png align="center")

# 📦 What is a Stack?

A **Stack** is a collection of AWS resources created from a CloudFormation template.

One template = One Stack

A stack can include:

*   EC2
    
*   VPC
    
*   S3
    
*   IAM
    
*   Lambda
    
*   RDS
    

Everything is managed together.

* * *

# 🔄 Stack Lifecycle

CloudFormation supports:

*   Create Stack
    
*   Update Stack
    
*   Delete Stack
    
*   Rollback Stack
    

This makes infrastructure management simple.

* * *

# 🔍 What is Drift Detection?

Drift Detection checks whether someone manually changed AWS resources outside CloudFormation.

Example:

Template says:

```plaintext
S3 Versioning Enabled
```

Someone manually disables versioning from AWS Console.

CloudFormation detects the difference.

This difference is called **Drift**.

* * *

# 🎨 CloudFormation Designer

AWS provides a visual drag-and-drop interface called **CloudFormation Designer**.

Benefits:

*   Visual architecture
    
*   Easy editing
    
*   Beginner friendly
    
*   Auto-generates templates
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/dbd5d535-f105-4968-bbf0-7f39965322de.png align="center")

# 💡 Tips & Tricks for Writing Better Templates

*   Use YAML instead of JSON.
    
*   Keep templates modular.
    
*   Use Parameters instead of hardcoding values.
    
*   Add Outputs for important resources.
    
*   Use Change Sets before updating production.
    
*   Organize templates with comments.
    
*   Validate templates before deployment.
    
*   Store templates in GitHub for version control.
    

* * *

# ✅ Best Practices

*   Follow Least Privilege IAM.
    
*   Enable Drift Detection regularly.
    
*   Use descriptive stack names.
    
*   Separate Dev, Test, and Production stacks.
    
*   Use nested stacks for large projects.
    
*   Never hardcode secrets.
    
*   Reuse templates.
    
*   Test templates before production.
    

* * *

# ⚖️ CloudFormation vs Terraform

| Feature | CloudFormation | Terraform |
| --- | --- | --- |
| Cloud Support | AWS Only | Multi-Cloud |
| Language | YAML / JSON | HCL |
| AWS Integration | Excellent | Excellent |
| Azure Support | No | Yes |
| GCP Support | No | Yes |
| Learning Curve | Easy | Moderate |
| State File | Managed by AWS | Local/Remote |
| Open Source | No | Yes |

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/8fd2c19c-8a86-4498-94a6-07758e786755.png align="center")

# 🎯 When Should You Use CloudFormation?

Choose CloudFormation if:

*   You only use AWS.
    
*   You want native AWS integration.
    
*   You need tight AWS service support.
    
*   Your infrastructure is AWS-specific.
    

* * *

# 🎯 When Should You Use Terraform?

Choose Terraform if:

*   You manage AWS + Azure + GCP.
    
*   You want cloud-independent infrastructure.
    
*   You use Kubernetes, VMware, GitHub, Cloudflare, or other providers.
    
*   You need multi-cloud deployments.
    

* * *

# 🌍 Real-World Use Cases

CloudFormation is widely used for:

*   Creating complete VPC architectures
    
*   Deploying EC2 fleets
    
*   Setting up S3 buckets
    
*   Creating IAM users and roles
    
*   Deploying Lambda functions
    
*   Creating RDS databases
    
*   Auto Scaling Groups
    
*   Load Balancers
    
*   Disaster Recovery environments
    
*   CI/CD infrastructure automation
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/625d79e6-09d1-423e-86b2-176e73450582.png align="center")

# 🎯 Advantages

*   Native AWS service
    
*   Fully automated deployments
    
*   Version-controlled infrastructure
    
*   Repeatable environments
    
*   Easy rollback
    
*   Cost-effective
    
*   Supports Drift Detection
    
*   Integrates with CI/CD pipelines
    

* * *

# ⚠️ Limitations

*   AWS only
    
*   YAML/JSON can become large
    
*   Less flexible than Terraform for multi-cloud
    
*   Debugging complex templates can be challenging
    

* * *

# 💼 Real-World DevOps Workflow

```plaintext
Developer

↓

GitHub Repository

↓

CloudFormation Template

↓

CI/CD Pipeline

↓

CloudFormation Stack

↓

AWS Infrastructure

↓

Application Deployment
```

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/ae5d6ec2-6330-4042-917f-7b1546b103fb.png align="center")

# 🎤 AWS CloudFormation Interview Questions & Answers

### Q1. What is AWS CloudFormation?

**Answer:** AWS CloudFormation is an Infrastructure as Code (IaC) service that lets you create, manage, and update AWS resources using YAML or JSON templates instead of manual configuration.

* * *

### Q2. What is Infrastructure as Code (IaC)?

**Answer:** IaC is the practice of managing infrastructure using code, enabling automation, consistency, version control, and repeatable deployments.

* * *

### Q3. Which template formats does CloudFormation support?

**Answer:** YAML and JSON. YAML is preferred because it is easier to read and maintain.

* * *

### Q4. Which section is mandatory in a CloudFormation template?

**Answer:** The **Resources** section. Without it, CloudFormation cannot create any AWS resources.

* * *

### Q5. What is a CloudFormation Stack?

**Answer:** A Stack is a collection of AWS resources created and managed together using a single CloudFormation template.

* * *

### Q6. What are Parameters?

**Answer:** Parameters allow users to provide input values (such as instance type or bucket name) during stack creation, making templates reusable and flexible.

* * *

### Q7. What are Outputs?

**Answer:** Outputs display useful information after deployment, such as EC2 Public IP, Load Balancer DNS, or S3 Bucket Name.

* * *

### Q8. What is Drift Detection?

**Answer:** Drift Detection identifies differences between the CloudFormation template and the actual AWS resources if someone manually changes resources outside CloudFormation.

* * *

### Q9. What is a Change Set?

**Answer:** A Change Set previews the changes CloudFormation will make before updating a stack, helping avoid accidental modifications.

* * *

### Q10. What is the difference between CloudFormation and Terraform?

**Answer:** CloudFormation is AWS-native and best for AWS-only environments, while Terraform supports multiple cloud providers (AWS, Azure, GCP) and is ideal for multi-cloud infrastructure.

* * *

# 🎉 Conclusion

AWS CloudFormation is a powerful Infrastructure as Code service that helps automate AWS resource provisioning, improve consistency, and simplify infrastructure management. By using reusable YAML templates, Drift Detection, and stack management features, you can deploy reliable cloud environments with confidence. If your organization primarily uses AWS, CloudFormation is an excellent choice for managing infrastructure efficiently and following modern DevOps best practices.

* * *

# 🚀 Continue Your Learning Journey

Thank you for taking the time to read this article.

Technology is evolving rapidly, and continuous learning is one of the most valuable investments you can make in your career. Whether you're exploring **DevOps, Cloud Computing, Artificial Intelligence, Cybersecurity, Software Development, Data Science, or Career Growth**, the resources below can help you deepen your knowledge and stay ahead in the industry.

* * *

# 🎓 Recommended Learning Platforms

## 🚀 Coursera

Learn from world-renowned universities and industry leaders including Google, IBM, Stanford, Microsoft, Meta, and many more.

✔ Professional Certificates ✔ Career-focused Learning Paths ✔ AI & Machine Learning Programs ✔ Cloud & DevOps Certifications ✔ Business & Leadership Courses

🔗 https://imp.i384100.net/k0KvbV

* * *

## 💻 Udemy

One of the largest online learning platforms with practical, hands-on courses covering:

✔ DevOps & Kubernetes ✔ Docker & Cloud Computing ✔ AWS, Azure & GCP ✔ Programming & Development ✔ Cybersecurity & Ethical Hacking

🔗 https://trk.udemy.com/MAL2MY

* * *

## 📊 DataCamp

A great platform for anyone interested in:

✔ Python Programming ✔ SQL & Databases ✔ Data Analytics ✔ Machine Learning ✔ Artificial Intelligence

Interactive learning paths and hands-on projects make it ideal for beginners and professionals alike.

🔗 https://datacamp.pxf.io/nX4kER

* * *

## 🎓 edX

Access high-quality courses and certifications from leading institutions such as:

✔ Harvard University ✔ MIT ✔ Berkeley ✔ Microsoft

Perfect for learners seeking university-level education online.

🔗 https://edx.sjv.io/POvVeN

* * *

## 🎨 Domestika

Enhance your creative skills with courses on:

✔ Graphic Design ✔ Video Editing ✔ Animation ✔ Digital Marketing ✔ Content Creation

🔗 https://domestika.sjv.io/dynKAW

* * *

# 🛠️ Recommended Tools & Resources

## 🔥 AppSumo

Discover exclusive lifetime deals on:

✔ AI Tools ✔ Productivity Software ✔ Developer Utilities ✔ Marketing Platforms ✔ Business Applications

A must-have resource for developers, creators, freelancers, and entrepreneurs looking to save money while accessing premium tools.

🔗 https://appsumo.8odi.net/L04a33

* * *

## 🛒 Shopify

Looking to start an online business or launch an eCommerce store?

Shopify provides everything you need to build, manage, and scale an online business.

✔ Online Store Builder ✔ Payment Integration ✔ Inventory Management ✔ Marketing Tools

🔗 https://shopify.pxf.io/Vxv09k

* * *

## 🌐 WordPress, WooCommerce & Jetpack

Create professional websites, blogs, and online stores with one of the most trusted web ecosystems in the world.

Ideal for:

✔ Personal Blogs ✔ Portfolio Websites ✔ Business Websites ✔ eCommerce Stores

🔗 https://automattic.pxf.io/Z6vR5W

* * *

# 🌍 Language Learning Resources

## 🗣️ Preply

Learn English and other languages through personalized one-on-one tutoring sessions with experts from around the world.

🔗 https://preply.sjv.io/o4gBDY

* * *

## 📚 British Council English Online

Improve your professional communication skills and English fluency through structured learning programs.

🔗 https://englishonline.sjv.io/9VOGa4

* * *

## 🧠 Rosetta Stone

One of the most recognized language-learning platforms for immersive language acquisition.

🔗 https://aff.rosettastone.com/X4OyqG

* * *

# 🧪 Science & Educational Resources

## 🔬 MEL Science

Interactive science kits and educational experiences designed to make STEM learning engaging and practical.

🔗 https://imp.i328067.net/bk2beg

* * *

## 📖 Carson Dellosa Education

Educational materials and learning resources for students, teachers, and lifelong learners.

🔗 https://carsondellosaeducation.sjv.io/E0JbjW

* * *

# ❤️ Support My Work

Creating detailed technical content, tutorials, guides, and learning resources takes significant time and effort.

If you find my articles helpful and would like to support my work, you can do so through the following platforms:

## ⭐ Become a GitHub Sponsor

Support my open-source contributions, technical content, and community projects.

🔗 https://github.com/sponsors/hritikranjan1

* * *

## ☕ Buy Me a Chai

Enjoying my content? Consider buying me a chai and supporting future tutorials, guides, and educational resources.

🔗 https://www.chai4.me/hritikranjan

* * *

# 👨‍💻 Connect With Me

**Hritik Ranjan**

💡 AI Enthusiast ☁️ DevOps Learner 🔐 Cybersecurity Advocate 💻 Software Developer

### Connect & Follow

🔗 GitHub: https://github.com/hritikranjan1

🔗 LinkedIn: https://linkedin.com/in/hritikranjan1

* * *

## 📢 Found This Article Helpful?

If this article added value to your learning journey:

✅ Share it with your network ✅ Bookmark it for future reference ✅ Follow for more DevOps, AI, Cloud, Cybersecurity, and Software Engineering content

Thank you for reading and being part of this learning journey.

**Keep Learning. Keep Building. Keep Growing. 🚀**