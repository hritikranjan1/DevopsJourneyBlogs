---
title: "Jenkins for Beginners: Complete Guide to CI/CD, Pipelines, Agents, Jenkinsfile & Architecture"
seoTitle: "Jenkins for Beginners: Complete CI/CD Guide"
seoDescription: "Learn Jenkins from scratch with CI/CD, pipelines, Jenkinsfile, agents, jobs, credentials, triggers, Docker, Shared Libraries, and best practices."
datePublished: 2026-09-12T14:18:47.962Z
cuid: cmtyh0kif00000bgmequ1hfty
slug: jenkins-beginners-guide
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/6e92881a-9ec5-42ce-945e-1237d9d1d69c.png
tags: docker, aws, github, kubernetes, automation, devops, jenkins, cloudcomputing, docker-images, devops-articles, jenkins-devops, devops-journey, jenkins-pipeline, cicd-jenkins-goal

---

If you are learning **DevOps, AWS, Docker, Kubernetes, or CI/CD**, Jenkins is one of the most important tools you should understand.

At first, Jenkins can look confusing because you see terms like:

*   Controller
    
*   Agent
    
*   Job
    
*   Build
    
*   Workspace
    
*   Pipeline
    
*   Jenkinsfile
    
*   Stage
    
*   Step
    
*   Credentials
    
*   SCM
    
*   Freestyle Project
    
*   Multibranch Pipeline
    
*   Shared Library
    
*   Webhook
    

Don't worry. 😊

In this guide, we will start from **zero** and gradually understand Jenkins with practical examples.

* * *

# 📌 What We Will Learn

In this article, we will cover:

1.  What is Jenkins?
    
2.  Why do we need Jenkins?
    
3.  What is CI/CD?
    
4.  Jenkins in a real-world DevOps workflow
    
5.  Jenkins architecture
    
6.  Jenkins components
    
7.  Jenkins Controller and Agent
    
8.  Installing Jenkins on AWS EC2
    
9.  Jenkins dashboard
    
10.  Important Jenkins terminology
     
11.  Jenkins Jobs
     
12.  Freestyle Project
     
13.  Pipeline Project
     
14.  Multibranch Pipeline
     
15.  Organization Folder
     
16.  Folder
     
17.  Multi-configuration Project
     
18.  Jenkins Pipeline
     
19.  Declarative Pipeline
     
20.  Jenkinsfile
     
21.  Jenkinsfile structure
     
22.  `pipeline`
     
23.  `agent`
     
24.  `stages`
     
25.  `stage`
     
26.  `steps`
     
27.  Environment variables
     
28.  Parameters
     
29.  Triggers
     
30.  Build periodically
     
31.  Poll SCM
     
32.  GitHub webhook
     
33.  Pipeline from SCM
     
34.  Credentials
     
35.  Jenkins Agents
     
36.  Docker with Jenkins
     
37.  Complete CI/CD example
     
38.  Shared Libraries
     
39.  Basic RBAC
     
40.  Beginner mistakes
     
41.  Production best practices
     
42.  Jenkins interview questions
     
43.  What to learn next
     

* * *

# 1\. 🚀 What is Jenkins?

![Image](https://images.openai.com/static-rsc-4/xZ_c15dijfUIh-GRmkBw5gtatqlandtMBhZWcPQCyOeseIpUfyfv0wI4Q6mp4KWJEo58uw7uQtmyG9iKWwjSpLQBoxj0rehvGWx1xekcQi0Xi2dXAj75zpydX5OcSZvG9s6tjqk8yMCW46o6sqZyOZ7W-8DE4sUpNDCg7kmaP_JRWCnPnk_vROjPj8FfzUck?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/iN3xsDYO7PzqrXawTZjovJxVWE3mTQCZY9fePXmXeVqH88LVzaTlFzJ4Lzo2mYY3E-6VcbX0XX7cDRNFWLs-6RGRdJcNXZBukoJpYoYQcxNlg3ovidcGFMaqf-QlQLOUVA51aEq57UmV20p4SaFbUnz8FNyYC2sodXyG35_tYELZoeS2l89TFT54e4adQiTS?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/q62ISvFLB27PmTb0mnyKiHMwxOqWh-mdhSgQwmP9r97YJ08GkMdIqcc5Paw2or23PWPwpHhEhHf9CngperW-icxUJ3Bl5QRlGZHGDbY9r8VO0j-BOHCO710RR15QqABksU8iPjj8eaemuIpQJambcgobxd6BoeVd6jG3Bh73i1bWqsW4u4w0anFAER328pdP?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/61ji_4SkZK_tQEM6xIfTxvzg9HQRql6NzGIEnNhY8l6SyoW8HdVtGhzXdG3YQxP1yfRVSHp0jJNpZgKN-dwufpwo5pZF9r-SUhHEGKcrRny0bY5-g007dZPHzORP8cDFIcrTDMn6cFHlppfsH-nnbYH28ezOgwhz-PGXzppSIGICy9LSZzShz3mYODroMJla?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/FlpR4y-fsmSXTkGkdDH9WR9L9iArBSL4BNgKPR7W0e7N-xGI6wgDY4oIn5Yz6QYOaK6LzmxoFYQ653oOrG8LBK_3DjF_dpUknX13h9MBlwtUpRetbjYJTYN4ouvR85rK96bqJ9tV2QNyLrCQUw3BaVop_nd0D-EZFJmcIL43_3bN-xuMO4p5NSU3ACSrd41E?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/XbQZEUAgefEkcVdAKXwUCJowM-PM6Hz20uKuhs2TfcOYPQuxXibAL41YqMlUXxwtz4GL50SgoDPEgaR-VZ4f_vVEu0SbfDFjAxTu4P0cHvCZMn1eWKVzqOrQC6w2FdTCtVxvugvMuyfSigVt0HFIQH2-FVyihf7W3ZRE9BzScd_UuVOsoAjHQVJIBE-z9bkB?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/M0McNmp6Ar2k1q5n8GNk5hNpojKmSvLRb7TwrJhGalRx_iNY89ToRKj1foLrlHAHBwmuyyaG80TXNgKo3wc_SZyyKQ04zGIaegQW9WcF1LGfp85nm_TsJxlCzdYiNoPJFdgFacm1n8TqPSOz3DZmj5VZBGJFTpwqf48QZCDkEgW8HAKw3CJ06ITsLXMs6vPD?purpose=fullsize align="center")

**Jenkins is an open-source automation server used to automate software development processes.**

In simple words:

> **Jenkins automatically performs repetitive tasks such as building, testing, and deploying applications.**

For example, imagine a developer pushes code to GitHub.

Without Jenkins:

```text
Developer
   ↓
Push Code
   ↓
Developer manually builds application
   ↓
Developer manually runs tests
   ↓
Developer manually creates Docker image
   ↓
Developer manually pushes image
   ↓
Developer manually deploys application
```

This takes time and can introduce human errors.

With Jenkins:

```text
Developer
    ↓
Push Code to GitHub
    ↓
Jenkins
    ↓
Build
    ↓
Test
    ↓
Docker Build
    ↓
Push Docker Image
    ↓
Deploy
    ↓
Application Running
```

Jenkins automates the process.

* * *

# 2\. 🤔 Why Do We Need Jenkins?

Suppose your company deploys an application 20 times every day.

Every deployment might require:

```text
1. Pull latest code
2. Install dependencies
3. Run tests
4. Build application
5. Build Docker image
6. Push image
7. Deploy application
8. Verify deployment
```

Doing this manually 20 times is inefficient.

Jenkins can automate these activities.

### Benefits of Jenkins

### ✅ Automation

Jenkins automatically executes repetitive tasks.

### ✅ Faster Releases

Automation reduces deployment time.

### ✅ Continuous Integration

Developers can frequently integrate their code.

### ✅ Continuous Delivery/Deployment

Applications can automatically move toward production.

### ✅ Early Bug Detection

Automated tests can identify problems early.

### ✅ Integration

Jenkins can integrate with:

*   GitHub
    
*   GitLab
    
*   Bitbucket
    
*   Docker
    
*   Kubernetes
    
*   AWS
    
*   SonarQube
    
*   Slack
    
*   Jira
    
*   Maven
    
*   Gradle
    
*   npm
    
*   Terraform
    

* * *

# 3\. 🔄 What is CI/CD?

Before understanding Jenkins, you should understand **CI/CD**.

CI/CD means:

```text
CI = Continuous Integration

CD = Continuous Delivery / Continuous Deployment
```

* * *

# 4\. What is Continuous Integration?

**Continuous Integration (CI)** means developers frequently merge their code into a shared repository.

For example:

```text
Developer A → GitHub
Developer B → GitHub
Developer C → GitHub
```

Whenever new code is pushed, Jenkins can automatically:

```text
Pull Code
   ↓
Build
   ↓
Run Tests
   ↓
Generate Report
```

If the tests fail, the team gets notified.

* * *

# 5\. What is Continuous Delivery?

Continuous Delivery means the application is automatically prepared for deployment.

Example:

```text
Code
 ↓
Build
 ↓
Test
 ↓
Docker Image
 ↓
Staging Environment
```

The production deployment may still require manual approval.

* * *

# 6\. What is Continuous Deployment?

Continuous Deployment goes one step further.

The deployment to production is also automated.

```text
Developer
    ↓
GitHub
    ↓
Jenkins
    ↓
Build
    ↓
Test
    ↓
Docker
    ↓
Production
```

No manual production approval is required if all pipeline conditions pass.

* * *

# 7\. Jenkins in a Real-World DevOps Workflow

A typical DevOps workflow might look like this:

![Image](https://images.openai.com/static-rsc-4/11wlMVITxWf87lV3GT--eowhUvELwYsky5Wej0ZGwaIonTNVSazVonueZumhc15AbrIVbHx1AyK-pB12SVbDSFopKfhMrVACzRveD9atK4KQr_4SuhfDCYYqO_4evqTXQZzecqFqFrPh0-QSuUdOjkEXjjO0x_ThsTgunJh4HL7vHYrL3Sxd5o8NSXZxIyc_?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/JyBFUBMJcfjn_D0jExyIy3xOmZXmhKtUq5yMVkQaOHwLFgcWJGmFdIogwYTR7zoLH7_svB4NcKvixZvYF2V9DCcq-60RLIwY4cKHce40zvTztFUHcRTBPF-oN2FFXNaN917xEQQlRpI1G_ffnjlv_OUzu2Sn3T3y7584ICAJAABPnbgg7JCB1WDiOf8uzQih?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/81Dno0WohaULOBnp4I__dyNhTotXz7SafDlBDIM5LEd-dtN1b1Ni4TNNy-_n7fsMtb81TcUlWyY_kLUDXYJlChJePnNk9M6UBDQxL1JQS1-XvdmkdTBRjRKKZb3ayHnQYBCIIpCb4-j1NmwcnNhZO2efzsqQMqZ4hhV57xB7SLwrEaaUEuuYSdsHGXdZ4cY7?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/asaebqbRJP1SMnXZp1idxAyHOwlAhh7uol2dplzQPGDaXl3-ugMXGNfnwCBurDZz_75-17yjJyJES-TBxPiiLBidh2XZNpNb6moheuv2hzUmfUuHMnWR4d7hKNhseoH9RCm5lX-l2HqZPzkBVC1p6R2bMdPL-OGj-48wMLD6hMhqXrQKRJaDe6Z7lcAPxssL?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/sVG38MZB92eMXjVH1k_55Y8sP_PJplF4TmV_fqf5dBCYDRFKb8pptwYKgHk9xokja38c_QiCY5XUYY5KSAb9oOtt87I7hC5BBCoJk8mhaYhkNYu3bNpHBx4MDX1scgx8nJSXAiem5N4SF9qSa7yakF1Wonxjc9ZMOQwKQQ6Z1i8zPEr3OTQWYC7Og-EdAoLH?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/f9Vw_97YMWTpPAvVja9o0jwiy6-jWdIvT2xrIwlFxYvVERqdjt61tF3L6QoSnB5hHUntCW2WCVS8DV8NudeEjtngnIfDVXGM360DiL5gHrDrMsbGLVkIUYjr_2AhiyOjrvZOV3CyfQrynko4TvauDzpxRx8ObNyc4DaJxt1keWO5wW__H2TuyMvFH8UzpoWD?purpose=fullsize align="center")

```text
                 Developer
                     |
                     v
                  GitHub
                     |
                  Webhook
                     |
                     v
                  Jenkins
                     |
          +----------+----------+
          |          |          |
          v          v          v
        Build      Test       Scan
          |          |          |
          +----------+----------+
                     |
                     v
               Docker Build
                     |
                     v
              Docker Registry
                     |
                     v
          +----------+----------+
          |                     |
          v                     v
        AWS EC2             Kubernetes
          |                     |
          +----------+----------+
                     |
                     v
                 Monitoring
                     |
                     v
             Prometheus/Grafana
```

This is a simplified production-style architecture.

* * *

# 8\. 🏗️ Jenkins Architecture

Jenkins follows a **Controller-Agent architecture**.

Older Jenkins documentation commonly used the term **Master-Slave**. The preferred terminology today is:

```text
Controller
Agent
```

A basic architecture looks like:

```text
                 Jenkins Controller
                       |
          +------------+------------+
          |            |            |
          v            v            v
       Agent 1      Agent 2      Agent 3
       Linux        Docker       Windows
```

The Controller manages Jenkins.

Agents perform the actual workload.

* * *

# 9\. Jenkins Controller

The **Jenkins Controller** is the central Jenkins server.

It is responsible for things such as:

*   Managing jobs
    
*   Managing pipelines
    
*   Scheduling builds
    
*   Managing credentials
    
*   Managing agents
    
*   Providing the Jenkins UI
    
*   Storing Jenkins configuration
    
*   Monitoring builds
    

Example:

```text
Jenkins Controller
       |
       +── Job configuration
       +── Pipeline configuration
       +── Credentials
       +── Build scheduling
       +── Agent management
```

* * *

# 10\. Jenkins Agent

A Jenkins **Agent** is a machine that performs pipeline tasks.

For example:

```text
Controller
     |
     +---- Linux Agent
     |
     +---- Docker Agent
     |
     +---- Windows Agent
```

Suppose you have:

```text
Project A → Java
Project B → Python
Project C → Node.js
```

You could use different agents for different workloads.

* * *

# 11\. Why Use Jenkins Agents?

Running every build directly on the Controller is generally not recommended for production.

Imagine 50 developers trigger builds simultaneously.

```text
50 Builds
    ↓
Controller
    ↓
CPU/Memory overloaded
```

Instead:

```text
                 Controller
                     |
        +------------+------------+
        |            |            |
        v            v            v
     Agent 1      Agent 2      Agent 3
     Java         Python       Node.js
```

This provides:

*   Better scalability
    
*   Isolation
    
*   Better performance
    
*   Different environments
    
*   Distributed builds
    

* * *

# 12\. Jenkins Installation on AWS EC2

A common beginner setup is:

```text
AWS
 |
 └── EC2
      |
      └── Ubuntu
           |
           └── Jenkins
```

You can create an Ubuntu EC2 instance and install Jenkins.

For learning, a machine with enough CPU and RAM is useful, especially when you run Docker builds or multiple jobs.

* * *

# 13\. Jenkins Installation — Basic Flow

After creating your Ubuntu EC2 instance:

```text
EC2
 ↓
SSH
 ↓
Update packages
 ↓
Install Java
 ↓
Install Jenkins
 ↓
Start Jenkins
 ↓
Open Jenkins port
 ↓
Access Jenkins UI
```

Jenkins requires Java.

Example:

```bash
java -version
```

Check Jenkins service:

```bash
sudo systemctl status jenkins
```

Start Jenkins:

```bash
sudo systemctl start jenkins
```

Enable Jenkins at boot:

```bash
sudo systemctl enable jenkins
```

* * *

# 14\. Jenkins Port

By default, Jenkins commonly runs on:

```text
8080
```

So your Jenkins URL might look like:

```text
http://EC2_PUBLIC_IP:8080
```

You need to allow the required port through the EC2 Security Group.

For a learning environment:

```text
Internet
   |
   | TCP 8080
   v
AWS Security Group
   |
   v
EC2
   |
   v
Jenkins
```

### ⚠️ Production Note

Do not blindly expose Jenkins directly to the public internet.

A production architecture would normally use things such as:

```text
Internet
   ↓
Load Balancer / Reverse Proxy
   ↓
HTTPS
   ↓
Jenkins
```

and appropriate network restrictions.

* * *

# 15\. Jenkins Initial Admin Password

When Jenkins is installed for the first time, you need the initial administrator password.

It is commonly stored at:

```bash
/var/lib/jenkins/secrets/initialAdminPassword
```

You can retrieve it with:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

Copy the password and use it during the initial Jenkins setup.

* * *

# 16\. Jenkins Dashboard

After logging in, you will see the Jenkins dashboard.

The dashboard is the main interface for managing Jenkins.

You can:

*   Create jobs
    
*   Run builds
    
*   View build history
    
*   Manage credentials
    
*   Manage nodes
    
*   Configure Jenkins
    
*   View pipeline status
    
*   Check console output
    

* * *

# 17\. Important Jenkins Terminology

Before creating a pipeline, understand these terms.

| Term | Simple Meaning |
| --- | --- |
| Job | Task/configuration Jenkins executes |
| Build | One execution of a job |
| Pipeline | Automated workflow |
| Stage | Logical section of pipeline |
| Step | Individual command/action |
| Agent | Machine that runs the job |
| Workspace | Directory where Jenkins works |
| Console Output | Build execution logs |
| Credentials | Securely stored secrets |
| Artifact | Output produced by a build |
| SCM | Source Code Management |
| Jenkinsfile | Pipeline definition file |

* * *

# 18\. What is a Jenkins Job?

A **Job** is a task configured in Jenkins.

For example:

```text
Build Django Application
```

or:

```text
Run Automated Tests
```

or:

```text
Deploy Application
```

A job can contain:

```text
Source Code
+
Build Steps
+
Triggers
+
Post-build Actions
```

* * *

# 19\. What is a Build?

A **build** is one execution of a Jenkins job.

For example:

```text
Job: Django Application

Build #1
Build #2
Build #3
Build #4
```

Every time Jenkins executes the job, a build is created.

A build may be:

```text
SUCCESS
FAILURE
ABORTED
UNSTABLE
```

* * *

# 20\. What is a Workspace?

The **workspace** is the directory where Jenkins performs work for a job.

For example:

```text
/var/lib/jenkins/workspace/my-project/
```

Inside it, Jenkins may have:

```text
workspace/
├── application/
├── Dockerfile
├── requirements.txt
├── Jenkinsfile
└── tests/
```

Jenkins checks out your source code into the workspace.

* * *

# 21\. What is Console Output?

Console Output contains logs generated while the job is running.

Example:

```text
Started by user admin

Checking out source code...

Running tests...

Building Docker image...

Successfully built image

Finished: SUCCESS
```

When a pipeline fails, **Console Output is one of the first places you should check.**

* * *

# 22\. Jenkins "New Item"

When you click:

```text
New Item
```

Jenkins provides several project types.

Common options include:

```text
Freestyle Project
Pipeline
Multi-configuration Project
Folder
Multibranch Pipeline
Organization Folder
Duplicate Existing Item
```

Let's understand each.

* * *

# 23\. Freestyle Project

A **Freestyle Project** is the traditional Jenkins job type.

You configure the job through the Jenkins UI.

Typical workflow:

```text
New Item
   ↓
Freestyle Project
   ↓
Configure
   ↓
Source Code Management
   ↓
Build Steps
   ↓
Post-build Actions
```

Example:

```text
GitHub
  ↓
Checkout Code
  ↓
Run Maven
  ↓
Run Tests
  ↓
Archive Results
```

* * *

# 24\. Freestyle Project Example

Suppose you have a Java application.

You can configure:

### Source Code Management

```text
Git
Repository:
https://github.com/example/demo.git
```

### Build Step

```bash
mvn clean test
```

Jenkins executes:

```text
Git Clone
   ↓
mvn clean test
   ↓
Test Result
```

* * *

# 25\. Advantages of Freestyle Projects

Freestyle projects are:

*   Easy for beginners
    
*   Simple for small jobs
    
*   UI-based
    
*   Quick to configure
    

But there is a major limitation.

The configuration lives primarily inside Jenkins.

If someone changes the job configuration manually, tracking those changes can be difficult.

* * *

# 26\. Why Pipelines Are Better for Modern CI/CD

Instead of configuring everything through the UI, you can define your pipeline as code.

Example:

```groovy
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }
}
```

This is called a **Declarative Jenkins Pipeline**.

* * *

# 27\. What is a Jenkins Pipeline?

A Jenkins Pipeline is an automated workflow.

For example:

```text
Checkout
   ↓
Build
   ↓
Test
   ↓
Docker Build
   ↓
Docker Push
   ↓
Deploy
```

Instead of manually performing these activities, Jenkins executes them automatically.

* * *

# 28\. Declarative Pipeline

There are different ways of writing Jenkins pipelines.

One of the most commonly used approaches is:

> **Declarative Pipeline**

It provides a structured syntax that is relatively easy to read.

Basic structure:

```groovy
pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}
```

* * *

# 29\. Understanding Jenkinsfile

A **Jenkinsfile** is a file containing Jenkins Pipeline code.

Usually, it is stored inside your Git repository.

Example project:

```text
django-notes-app/
│
├── app/
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
└── README.md
```

The Jenkinsfile defines:

```text
What Jenkins should do
How Jenkins should do it
When Jenkins should do it
Where Jenkins should run it
```

* * *

# 30\. Why Store Jenkinsfile in Git?

Suppose your pipeline is configured manually inside Jenkins.

Someone changes:

```text
Build Step
```

You might not know:

*   Who changed it?
    
*   What changed?
    
*   Why did it change?
    

With Jenkinsfile:

```text
Git
 |
 +── Jenkinsfile
```

Changes can be tracked using Git.

Example:

```text
Commit 1 → Build + Test

Commit 2 → Added Docker Build

Commit 3 → Added Deployment
```

This is called **Pipeline as Code**.

* * *

# 31\. Jenkinsfile Structure

Let's understand the basic structure carefully.

```groovy
pipeline {

    agent any

    stages {

        stage('Build') {

            steps {
                echo 'Building application'
            }
        }

        stage('Test') {

            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {

            steps {
                echo 'Deploying application'
            }
        }
    }
}
```

The hierarchy is:

```text
pipeline
 ├── agent
 └── stages
      ├── stage
      │    └── steps
      │
      ├── stage
      │    └── steps
      │
      └── stage
           └── steps
```

* * *

# 32\. `pipeline`

The `pipeline` block is the root of a Declarative Pipeline.

Example:

```groovy
pipeline {

}
```

Everything related to your pipeline is generally defined inside it.

* * *

# 33\. `agent`

The `agent` tells Jenkins where the pipeline should execute.

Example:

```groovy
agent any
```

This means:

> Run this pipeline on any available Jenkins agent.

Another example:

```groovy
agent {
    label 'linux'
}
```

This means:

> Run the pipeline on an agent with the `linux` label.

* * *

# 34\. `stages`

The `stages` block contains the major sections of your pipeline.

Example:

```groovy
stages {

    stage('Build') {
        ...
    }

    stage('Test') {
        ...
    }

    stage('Deploy') {
        ...
    }
}
```

Think of stages as major milestones.

* * *

# 35\. `stage`

A `stage` represents one logical part of your CI/CD process.

For example:

```groovy
stage('Build')
```

```groovy
stage('Test')
```

```groovy
stage('Deploy')
```

A pipeline can contain many stages.

* * *

# 36\. `steps`

`steps` contains the actual commands Jenkins executes.

Example:

```groovy
steps {
    echo 'Hello Jenkins'
}
```

Another example:

```groovy
steps {
    sh 'docker build -t myapp .'
}
```

On Linux, `sh` can execute shell commands.

For Windows agents, you may use:

```groovy
bat 'dir'
```

* * *

# 37\. Complete Beginner Jenkinsfile

Here is a simple example:

```groovy
pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }

}
```

Pipeline flow:

```text
Checkout
   ↓
Build
   ↓
Test
   ↓
Deploy
```

* * *

# 38\. Jenkins Pipeline with Shell Commands

Let's make it more practical.

```groovy
pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/example/demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t demo-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running tests'
            }
        }
    }
}
```

* * *

# 39\. Environment Variables

Jenkins allows you to define environment variables.

Example:

```groovy
pipeline {

    agent any

    environment {
        APP_NAME = 'demo-app'
        ENVIRONMENT = 'production'
    }

    stages {

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
            }
        }
    }
}
```

Environment variables are useful for:

*   Application names
    
*   Environment names
    
*   URLs
    
*   Version numbers
    
*   Configuration values
    

* * *

# 40\. Parameters

Sometimes you don't want every pipeline execution to use the same values.

For example:

```text
Environment:
1. Dev
2. QA
3. Production
```

You can make the pipeline parameterized.

Example:

```groovy
pipeline {

    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'qa', 'prod'],
            description: 'Select deployment environment'
        )
    }

    stages {

        stage('Deploy') {

            steps {
                echo "Deploying to ${params.ENVIRONMENT}"
            }
        }
    }
}
```

When you start the build, Jenkins asks:

```text
Select Environment:

[ dev ]
[ qa  ]
[ prod ]
```

* * *

# 41\. Jenkins Triggers

A trigger tells Jenkins **when to start a job or pipeline**.

Common triggers include:

```text
Build after other projects are built
Build periodically
GitHub hook trigger
Poll SCM
Remote trigger
```

Let's understand them.

* * *

# 42\. Build After Other Projects Are Built

Suppose you have:

```text
Build Application
       ↓
Run Tests
       ↓
Deploy
```

You can configure one job to start after another job completes.

Example:

```text
Job A
 ↓
Job B
 ↓
Job C
```

* * *

# 43\. Build Periodically

This executes a job according to a schedule.

Example:

```text
Every night at 12 AM
```

Cron syntax may be used.

Example:

```text
H 0 * * *
```

This is useful for:

*   Nightly builds
    
*   Scheduled tests
    
*   Maintenance tasks
    
*   Periodic security scans
    

* * *

# 44\. Poll SCM

With **Poll SCM**, Jenkins periodically checks the source-code repository.

For example:

```text
Jenkins
   ↓
Check GitHub
   ↓
Any changes?
   ↓
Yes → Build
No  → Do nothing
```

This works, but it can generate unnecessary polling traffic.

* * *

# 45\. GitHub Webhook

A more efficient approach is a webhook.

Flow:

```text
Developer
   ↓
git push
   ↓
GitHub
   ↓
Webhook
   ↓
Jenkins
   ↓
Pipeline
```

Instead of Jenkins repeatedly asking GitHub:

> "Did something change?"

GitHub tells Jenkins:

> "New code was pushed. Start the pipeline."

* * *

# 46\. Pipeline from SCM

This is one of the most important options.

SCM means:

> **Source Code Management**

Examples:

*   Git
    
*   GitHub
    
*   GitLab
    
*   Bitbucket
    

Instead of writing the Jenkinsfile directly inside Jenkins, you can store it in Git.

Example:

```text
GitHub Repository
│
├── application/
├── Dockerfile
├── Jenkinsfile
└── README.md
```

Jenkins reads the Jenkinsfile from Git.

* * *

# 47\. Pipeline Definition

When creating a Pipeline project, Jenkins commonly provides options such as:

```text
Definition
```

You may see:

```text
Pipeline script
```

or:

```text
Pipeline script from SCM
```

* * *

# 48\. Pipeline Script

With:

```text
Pipeline script
```

you write the Jenkinsfile directly inside Jenkins.

Example:

```groovy
pipeline {

    agent any

    stages {

        stage('Hello') {
            steps {
                echo 'Hello Jenkins'
            }
        }
    }
}
```

This is useful for learning.

* * *

# 49\. Pipeline Script from SCM

For real projects, you will commonly store the pipeline code in Git.

Configuration looks conceptually like:

```text
Definition:
Pipeline script from SCM

SCM:
Git

Repository URL:
https://github.com/example/project.git

Branch:
main

Script Path:
Jenkinsfile
```

Then Jenkins does:

```text
Jenkins
   ↓
Clone Git Repository
   ↓
Find Jenkinsfile
   ↓
Read Pipeline
   ↓
Execute Pipeline
```

* * *

# 50\. Script Path

Suppose your repository looks like:

```text
project/
│
├── application/
│
└── ci/
    └── Jenkinsfile
```

Then your Script Path would be:

```text
ci/Jenkinsfile
```

If the Jenkinsfile is in the root:

```text
Jenkinsfile
```

* * *

# 51\. Lightweight Checkout

You may see:

```text
Lightweight checkout
```

This allows Jenkins to retrieve the Jenkinsfile without necessarily checking out the complete repository initially.

It can reduce unnecessary work when Jenkins only needs to read the pipeline definition.

* * *

# 52\. Discard Old Builds

Jenkins stores build history.

For example:

```text
Build #1
Build #2
Build #3
...
Build #500
```

Keeping hundreds or thousands of builds can consume disk space.

You can enable:

```text
Discard old builds
```

and configure retention.

For example:

```text
Keep last 20 builds
```

This helps control disk usage.

* * *

# 53\. Do Not Allow Concurrent Builds

Suppose a pipeline is currently running:

```text
Build #101 → Running
```

A developer pushes more code:

```text
Build #102 → Triggered
```

If concurrent builds are disabled, Jenkins waits instead of running both simultaneously.

This can be useful when deployments must happen sequentially.

* * *

# 54\. Pipeline Resume After Controller Restart

You may see an option similar to:

```text
Do not allow the pipeline to resume if the controller restarts
```

Normally, Jenkins Pipeline has mechanisms that can allow a pipeline to continue after certain controller interruptions.

Whether you disable resume depends on your pipeline design and operational requirements.

For beginners, understand the concept rather than changing it without a reason.

* * *

# 55\. GitHub Project

The:

```text
GitHub project
```

option provides GitHub-related project configuration.

It can associate the Jenkins project with a GitHub repository.

* * *

# 56\. Pipeline Speed/Durability

Jenkins provides pipeline durability settings that affect how pipeline execution state is persisted.

There is a trade-off between:

```text
Performance
```

and:

```text
Durability / recovery
```

For production pipelines, choose settings based on workload and reliability requirements rather than blindly selecting an option.

* * *

# 57\. Preserve Stashes

Jenkins Pipeline supports:

```groovy
stash
```

and:

```groovy
unstash
```

These are useful for temporarily sharing files between stages or agents.

Example:

```groovy
stash name: 'app', includes: '**/*'
```

Later:

```groovy
unstash 'app'
```

You may also see:

```text
Preserve stashes from completed builds
```

This is useful when you need to reuse stashed data from completed builds, especially with certain restart/replay workflows.

* * *

# 58\. Jenkins Credentials

CI/CD pipelines often need secrets.

Examples:

```text
GitHub Token
Docker Hub Password
AWS Access Key
SSH Private Key
API Token
```

### ❌ Don't do this:

```groovy
docker login -u admin -p MyPassword
```

Your password is exposed in pipeline code.

Instead, use Jenkins Credentials.

* * *

# 59\. Credential Binding

Jenkins can securely store credentials and make them available to a pipeline when needed.

Conceptually:

```text
Jenkins Credentials
        |
        v
Pipeline
        |
        v
Environment Variable
        |
        v
Command
```

Example:

```groovy
withCredentials([
    usernamePassword(
        credentialsId: 'dockerhub-creds',
        usernameVariable: 'DOCKER_USER',
        passwordVariable: 'DOCKER_PASS'
    )
]) {

    sh 'docker login -u "$DOCKER_USER" -p "$DOCKER_PASS"'
}
```

The credentials themselves should not be committed to Git.

* * *

# 60\. Docker + Jenkins

Docker is commonly used with Jenkins.

A typical workflow is:

```text
GitHub
   ↓
Jenkins
   ↓
Checkout
   ↓
Docker Build
   ↓
Docker Image
   ↓
Docker Registry
   ↓
Deployment
```

Example:

```bash
docker build -t myapp:latest .
```

Then:

```bash
docker push myusername/myapp:latest
```

* * *

# 61\. Complete Django CI/CD Example

Now let's create a realistic beginner pipeline.

Suppose our repository is:

```text
django-notes-app/
│
├── app/
├── requirements.txt
├── Dockerfile
├── Jenkinsfile
└── README.md
```

Pipeline:

```text
GitHub
   ↓
Checkout
   ↓
Install/Build
   ↓
Test
   ↓
Docker Build
   ↓
Docker Push
```

* * *

# 62\. Example Jenkinsfile

```groovy
pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/example/django-notes-app.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Django application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t myuser/django-notes-app:latest .'
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Push Docker image to registry'
            }
        }
    }
}
```

This is intentionally simplified.

A production pipeline would add proper credentials, image versioning, tests, scanning, deployment, and error handling.

* * *

# 63\. Pipeline Visualization

Jenkins can display the pipeline approximately like:

```text
┌──────────┐
│ Checkout │
└────┬─────┘
     ↓
┌──────────┐
│  Build   │
└────┬─────┘
     ↓
┌──────────┐
│   Test   │
└────┬─────┘
     ↓
┌──────────────┐
│ Docker Build │
└────┬─────────┘
     ↓
┌─────────────┐
│ Docker Push │
└─────────────┘
```

If one stage fails:

```text
Checkout       ✅
Build          ✅
Test           ❌
Docker Build   ⏭️
Docker Push    ⏭️
```

This makes troubleshooting much easier.

* * *

# 64\. Jenkins Agents — Practical Example

Suppose your company has:

```text
Java Application
Python Application
Node.js Application
```

You can create:

```text
Jenkins Controller
       |
       +── Java Agent
       |
       +── Python Agent
       |
       +── Node Agent
```

Your pipeline can select the appropriate agent.

Example:

```groovy
pipeline {

    agent {
        label 'docker'
    }

    stages {

        stage('Build') {

            steps {
                sh 'docker build -t myapp .'
            }
        }
    }
}
```

* * *

# 65\. Agent Labels

Labels help Jenkins identify suitable agents.

For example:

```text
linux
docker
java
python
production
```

Agent:

```text
Agent-01
Labels:
linux docker
```

Pipeline:

```groovy
agent {
    label 'docker'
}
```

Jenkins looks for an appropriate agent.

* * *

# 66\. Multibranch Pipeline

A **Multibranch Pipeline** automatically discovers branches in a Git repository and creates pipelines for them.

Suppose GitHub contains:

```text
main
develop
feature/login
feature/payment
```

A Multibranch Pipeline can discover these branches.

Conceptually:

```text
GitHub Repository
       |
       +── main
       +── develop
       +── feature/login
       +── feature/payment
```

Jenkins can create corresponding branch jobs.

This is very useful for teams using Git-based development workflows.

* * *

# 67\. Why Multibranch Pipelines Are Useful

Without Multibranch:

```text
Create separate job
for every branch
```

This becomes difficult.

With Multibranch:

```text
Repository
    ↓
Branch Discovery
    ↓
Automatic Pipelines
```

This is one of the important Jenkins concepts to learn for real-world CI/CD.

* * *

# 68\. Organization Folder

An **Organization Folder** can scan an organization or group of repositories and automatically create appropriate Jenkins jobs, such as multibranch pipelines.

Conceptually:

```text
GitHub Organization
       |
       +── repo-A
       +── repo-B
       +── repo-C
       +── repo-D
```

Jenkins can discover repositories and create corresponding jobs.

This becomes useful when an organization manages many repositories.

* * *

# 69\. Folder

A Jenkins **Folder** is used to organize jobs.

For example:

```text
Jenkins
│
├── Development
│   ├── App-A
│   └── App-B
│
├── QA
│   ├── App-A
│   └── App-B
│
└── Production
    ├── App-A
    └── App-B
```

Folders make large Jenkins installations easier to manage.

They also create separate namespaces, so similarly named jobs can exist in different folders.

* * *

# 70\. Multi-Configuration Project

A **Multi-configuration Project** is useful when you need to run a job across many combinations of configurations.

For example:

```text
Operating System:
Linux
Windows

Java:
21
25
```

You could have combinations such as:

```text
Linux + Java 21
Linux + Java 25
Windows + Java 21
Windows + Java 25
```

This is useful for compatibility testing.

For modern CI/CD, Pipeline and matrix-style approaches are often more flexible, but you should still understand this Jenkins project type.

* * *

# 71\. Duplicate Existing Item

Jenkins also allows you to create a new job by copying an existing job configuration.

For example:

```text
Existing Job:
Django-Dev

Copy:
Django-QA
```

This can be useful for quickly creating similar configurations, although Pipeline as Code is generally easier to maintain at scale.

* * *

# 72\. Jenkins Shared Libraries

When multiple teams have multiple Jenkinsfiles, you may notice repeated code.

Example:

```groovy
cloneRepository()
dockerBuild()
dockerPush()
deploy()
```

Instead of copying the same code into every repository, Jenkins Shared Libraries allow you to centralize reusable pipeline code.

Architecture:

```text
                 Shared Library
                      |
        +-------------+-------------+
        |             |             |
        v             v             v
     Project A     Project B     Project C
     Jenkinsfile   Jenkinsfile   Jenkinsfile
```

* * *

# 73\. Example Shared Library Repository

A repository might look like:

```text
jenkins-shared-library/
│
├── vars/
│   ├── clone.groovy
│   ├── dockerBuild.groovy
│   ├── dockerPush.groovy
│   └── deploy.groovy
│
└── README.md
```

Then projects can reuse those functions.

* * *

# 74\. Why Shared Libraries?

Imagine 30 projects have:

```groovy
docker build
docker login
docker push
```

If Docker configuration changes, you would need to modify 30 Jenkinsfiles.

With Shared Libraries:

```text
Shared Library
      ↓
Update once
      ↓
Multiple projects use updated logic
```

Benefits:

*   Reusability
    
*   Standardization
    
*   Less duplicate code
    
*   Easier maintenance
    
*   Centralized pipeline logic
    

* * *

# 75\. Jenkins User Management

Jenkins supports user management and authorization.

For example:

```text
Admin
Developer
Tester
Viewer
```

Different users should have different permissions.

For example:

| Role | Permission |
| --- | --- |
| Admin | Full Jenkins access |
| Developer | Build/deploy selected applications |
| Tester | Run test jobs |
| Viewer | View jobs/logs |

This is called:

> **RBAC — Role-Based Access Control**

The exact RBAC capabilities depend on the authorization strategy/plugins configured in Jenkins.

* * *

# 76\. Jenkins Production Architecture

A more realistic Jenkins architecture might look like:

```text
                         Internet
                            |
                            v
                     Load Balancer
                            |
                            v
                    Reverse Proxy / HTTPS
                            |
                            v
                  +--------------------+
                  | Jenkins Controller |
                  +--------------------+
                    /       |        \
                   /        |         \
                  v         v          v
             Linux Agent  Docker     Kubernetes
                         Agent        Agent
                  |         |           |
                  +---------+-----------+
                            |
                            v
                       Applications
                            |
                            v
                  Monitoring / Logging
```

Jenkins may integrate with:

```text
GitHub
Docker Registry
AWS
Kubernetes
SonarQube
Prometheus
Grafana
Slack
```

* * *

# 77\. Complete DevOps CI/CD Flow

Let's put everything together.

```text
Developer
    |
    | git push
    v
GitHub
    |
    | Webhook
    v
Jenkins Controller
    |
    | Schedule
    v
Jenkins Agent
    |
    +---- Checkout
    |
    +---- Build
    |
    +---- Unit Test
    |
    +---- Security Scan
    |
    +---- Docker Build
    |
    +---- Docker Push
    |
    +---- Deploy
    |
    v
AWS / Kubernetes
    |
    v
Application
    |
    v
Monitoring
```

This is the basic idea behind Jenkins-powered CI/CD.

* * *

# 78\. Beginner Jenkins Project

If you are learning Jenkins, I strongly recommend building the following project.

### Project

```text
GitHub
   ↓
Jenkins
   ↓
Docker
   ↓
Docker Hub
   ↓
AWS EC2
```

### Step 1

Create a GitHub repository.

```text
django-notes-app
```

### Step 2

Add:

```text
Dockerfile
Jenkinsfile
```

### Step 3

Create Jenkins Pipeline.

### Step 4

Configure GitHub repository.

### Step 5

Configure Docker Hub credentials.

### Step 6

Create Docker image.

### Step 7

Push image to Docker Hub.

### Step 8

Deploy container on EC2.

* * *

# 79\. Example End-to-End Pipeline

A more complete conceptual Jenkinsfile:

```groovy
pipeline {

    agent any

    environment {
        IMAGE_NAME = 'myuser/django-notes-app'
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

        stage('Docker Build') {
            steps {
                sh """
                    docker build \
                    -t ${IMAGE_NAME}:${IMAGE_TAG} .
                """
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Pushing Docker image'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}
```

Notice that we use:

```text
BUILD_NUMBER
```

instead of always using:

```text
latest
```

This gives us versioned images.

For example:

```text
myuser/django-notes-app:101
myuser/django-notes-app:102
myuser/django-notes-app:103
```

* * *

# 80\. What is `post`?

The `post` section allows you to define actions after pipeline execution.

Example:

```groovy
post {

    success {
        echo 'Build successful'
    }

    failure {
        echo 'Build failed'
    }

    always {
        echo 'Pipeline finished'
    }
}
```

Common conditions include:

```text
always
success
failure
unstable
aborted
changed
```

* * *

# 81\. Jenkins Pipeline Flow

Remember this simple structure:

```text
Pipeline
   |
   +── Agent
   |
   +── Environment
   |
   +── Parameters
   |
   +── Triggers
   |
   +── Stages
   |      |
   |      +── Stage
   |             |
   |             +── Steps
   |
   +── Post
```

This is one of the most important structures to remember.

* * *

# 82\. Jenkins Job vs Build vs Pipeline

Beginners often confuse these.

### Job

Configuration of a task.

```text
My Application Pipeline
```

### Build

One execution of that job.

```text
Build #25
```

### Pipeline

The complete automation workflow.

```text
Build → Test → Deploy
```

Easy way to remember:

```text
Job = What is configured

Build = One execution

Pipeline = Workflow
```

* * *

# 83\. Jenkins Controller vs Agent

Another common interview question.

| Controller | Agent |
| --- | --- |
| Manages Jenkins | Executes workloads |
| Schedules builds | Runs builds |
| Provides UI | Performs tasks |
| Manages configuration | Uses workspace |
| Manages agents | Runs pipeline steps |

Simple example:

```text
Controller = Manager
Agent = Worker
```

* * *

# 84\. Freestyle vs Pipeline

| Freestyle | Pipeline |
| --- | --- |
| UI based | Code based |
| Easy for beginners | Better for complex workflows |
| Less reusable | Highly reusable |
| Configuration in Jenkins | Jenkinsfile can be stored in Git |
| Difficult to version configuration | Git version control |
| Traditional | Modern CI/CD approach |

For modern production CI/CD, **Pipeline as Code** is generally preferred.

* * *

# 85\. Poll SCM vs Webhook

| Poll SCM | Webhook |
| --- | --- |
| Jenkins checks repository | Repository notifies Jenkins |
| Periodic checking | Event-driven |
| Can create unnecessary requests | More efficient |
| Simple to understand | Common modern approach |

Flow:

### Poll SCM

```text
Jenkins → GitHub
Jenkins → GitHub
Jenkins → GitHub
```

### Webhook

```text
GitHub → Jenkins
```

when an event occurs.

* * *

# 86\. Pipeline Script vs Pipeline from SCM

| Pipeline Script | Pipeline from SCM |
| --- | --- |
| Jenkinsfile written in Jenkins UI | Jenkinsfile stored in Git |
| Easy for learning | Better for real projects |
| Not ideal for version control | Version controlled |
| Quick testing | Recommended for teams |

For real projects:

```text
GitHub
   |
   └── Jenkinsfile
```

is generally the better approach.

* * *

# 87\. Common Beginner Mistakes

### ❌ Running everything on Controller

Better:

```text
Controller
   ↓
Agents
```

* * *

### ❌ Hardcoding passwords

Never write:

```groovy
password = 'MySecret123'
```

Use Jenkins Credentials.

* * *

### ❌ Using only `latest`

Prefer versioned images:

```text
app:101
app:102
app:103
```

* * *

### ❌ No build cleanup

Old builds can consume disk.

Configure build retention.

* * *

### ❌ No automated testing

A CI pipeline should ideally validate code before deployment.

* * *

### ❌ No webhook

Polling can work, but event-driven triggers are often better for Git-based workflows.

* * *

### ❌ Huge Jenkinsfile

If your Jenkinsfile becomes hundreds or thousands of lines, consider:

```text
Shared Libraries
```

or better pipeline design.

* * *

# 88\. Jenkins Best Practices

For production Jenkins:

### 🔐 Security

*   Use HTTPS
    
*   Use strong authentication
    
*   Use least-privilege permissions
    
*   Protect credentials
    
*   Avoid hardcoded secrets
    
*   Restrict network access
    
*   Keep Jenkins and plugins updated
    

### ⚙️ Pipeline

*   Use Jenkinsfile
    
*   Store Jenkinsfile in Git
    
*   Use reusable pipeline code
    
*   Add automated tests
    
*   Add security scanning
    
*   Version Docker images
    
*   Keep pipelines readable
    

### 🖥️ Infrastructure

*   Avoid unnecessary builds on Controller
    
*   Use agents
    
*   Monitor disk usage
    
*   Back up Jenkins configuration
    
*   Monitor Jenkins health
    

* * *

# 89\. Jenkins Learning Roadmap

If you are completely new to Jenkins, follow this order:

```text
                    Jenkins
                       |
          +------------+------------+
          |                         |
        Basics                    CI/CD
          |                         |
      Dashboard                 GitHub
          |                         |
        Jobs                    Webhooks
          |                         |
     Freestyle                Jenkinsfile
          |                         |
       Pipeline                 Docker
          |                         |
        Stages                  AWS
          |                         |
        Agents               Kubernetes
          |
    Shared Libraries
          |
        RBAC
          |
     Production
```

* * *

# 90\. Jenkins Commands You Should Know

Check Jenkins:

```bash
sudo systemctl status jenkins
```

Start:

```bash
sudo systemctl start jenkins
```

Stop:

```bash
sudo systemctl stop jenkins
```

Restart:

```bash
sudo systemctl restart jenkins
```

Enable on startup:

```bash
sudo systemctl enable jenkins
```

View logs:

```bash
sudo journalctl -u jenkins
```

Follow logs:

```bash
sudo journalctl -u jenkins -f
```

Check Java:

```bash
java -version
```

* * *

# 91\. Jenkins Important Files and Directories

A common Jenkins home directory is:

```text
/var/lib/jenkins
```

It may contain:

```text
/var/lib/jenkins/
│
├── jobs/
├── workspace/
├── plugins/
├── secrets/
├── users/
└── config.xml
```

### `jobs/`

Contains job-related data.

### `workspace/`

Contains working directories for builds.

### `plugins/`

Contains installed Jenkins plugins.

### `secrets/`

Contains Jenkins security-related information.

### `users/`

Contains user-related data.

* * *

# 92\. What Are Jenkins Plugins?

Jenkins has a large plugin ecosystem.

Plugins extend Jenkins functionality.

For example:

```text
Git Plugin
Docker Plugin
Pipeline Plugin
Credentials Plugin
GitHub Integration
Kubernetes Plugin
```

Without plugins, Jenkins would have much less functionality.

But:

> Don't install plugins unnecessarily.

Every plugin adds maintenance and security considerations.

* * *

# 93\. Jenkins + GitHub

A common integration is:

```text
Developer
   ↓
Git push
   ↓
GitHub
   ↓
Webhook
   ↓
Jenkins
   ↓
Jenkinsfile
   ↓
Pipeline
```

This is one of the most common CI/CD workflows you should practice.

* * *

# 94\. Jenkins + Docker

Jenkins can execute Docker commands.

Example:

```bash
docker build -t myapp:1.0 .
```

Then:

```bash
docker push myuser/myapp:1.0
```

Then deployment:

```bash
docker pull myuser/myapp:1.0
```

and:

```bash
docker run -d myuser/myapp:1.0
```

* * *

# 95\. Jenkins + AWS

Jenkins can integrate with AWS services such as:

```text
EC2
S3
ECR
ECS
EKS
CloudFormation
CodeDeploy
```

Example architecture:

```text
GitHub
   ↓
Jenkins
   ↓
Docker Build
   ↓
Amazon ECR
   ↓
Amazon EKS
   ↓
Application
```

* * *

# 96\. Jenkins + Kubernetes

In larger environments, Jenkins can use Kubernetes-based agents.

Conceptually:

```text
Jenkins Controller
       |
       v
Kubernetes
       |
       +── Pod → Build
       |
       +── Pod → Test
       |
       +── Pod → Docker/Build Tool
```

Agents can be created dynamically according to workload.

This is an advanced topic that we will cover later in the Jenkins series.

* * *

# 97\. Jenkins + Monitoring

Jenkins itself should also be monitored.

You can integrate Jenkins environments with monitoring and observability tools.

For example:

```text
Jenkins
   |
   +── Logs
   +── Metrics
   +── Build Status
   |
   v
Monitoring
   |
   +── Prometheus
   +── Grafana
```

The important DevOps principle is:

> **Don't just automate deployments; monitor the automation and the applications too.**

* * *

# 98\. Jenkins Interview Questions

If you are preparing for DevOps interviews, these are important questions.

### Q1. What is Jenkins?

Jenkins is an open-source automation server used to automate CI/CD workflows such as building, testing, and deploying applications.

### Q2. What is CI?

Continuous Integration is the practice of frequently integrating code changes into a shared repository and automatically validating them through builds and tests.

### Q3. What is CD?

Continuous Delivery/Deployment automates the process of preparing or deploying applications to environments.

### Q4. What is a Jenkins Pipeline?

A Jenkins Pipeline is a code-defined workflow that automates stages such as build, test, and deployment.

### Q5. What is a Jenkinsfile?

A Jenkinsfile contains the Pipeline definition and is commonly stored in the application's source-code repository.

### Q6. What is a Jenkins Agent?

An Agent is a machine or execution environment where Jenkins runs pipeline tasks.

### Q7. What is a Jenkins Controller?

The Controller manages Jenkins configuration, scheduling, jobs, and agents.

### Q8. What is a Workspace?

The Workspace is the directory where Jenkins checks out source code and performs build activities.

### Q9. Freestyle vs Pipeline?

Freestyle is primarily UI-configured, while Pipeline defines CI/CD workflow as code.

### Q10. What is a webhook?

A webhook allows an external system such as GitHub to notify Jenkins about an event, such as a code push.

* * *

# 99\. Important Jenkins Terms — Quick Revision

Before moving to Part 2, remember these:

```text
Jenkins
   ↓
Automation Server

CI/CD
   ↓
Automated Software Delivery

Controller
   ↓
Manages Jenkins

Agent
   ↓
Runs Jobs

Job
   ↓
Configured Task

Build
   ↓
One Job Execution

Pipeline
   ↓
Automation Workflow

Jenkinsfile
   ↓
Pipeline as Code

Stage
   ↓
Major Pipeline Section

Step
   ↓
Individual Action

Workspace
   ↓
Build Working Directory

Credentials
   ↓
Secure Secrets

SCM
   ↓
Git/GitHub/etc.

Webhook
   ↓
Event-Based Trigger
```

* * *

# 100\. 🎯 Final Jenkins Architecture to Remember

The most important picture from this entire article is:

```text
                         DEVELOPER
                             |
                             | git push
                             v
                          GITHUB
                             |
                             | Webhook
                             v
                  +----------------------+
                  | Jenkins Controller   |
                  |                      |
                  | Jobs                 |
                  | Pipelines            |
                  | Credentials          |
                  | Scheduling            |
                  +----------+-----------+
                             |
                             |
                   Pipeline Execution
                             |
              +--------------+--------------+
              |              |              |
              v              v              v
           Agent 1        Agent 2        Agent 3
           Linux          Docker         Kubernetes
              |              |              |
              +--------------+--------------+
                             |
                             v
                       Build / Test
                             |
                             v
                       Docker Image
                             |
                             v
                    Docker Registry/ECR
                             |
                             v
                       AWS / Kubernetes
                             |
                             v
                       APPLICATION
                             |
                             v
                    MONITORING / LOGS
```

* * *

# 💡 Final Takeaway

If you're a beginner, **don't try to memorize Jenkins syntax immediately**.

First understand this flow:

```text
Developer
    ↓
GitHub
    ↓
Webhook
    ↓
Jenkins
    ↓
Jenkinsfile
    ↓
Agent
    ↓
Build
    ↓
Test
    ↓
Docker
    ↓
Registry
    ↓
Deploy
    ↓
Monitor
```

Once this architecture is clear, Jenkins becomes much easier to understand.

The most important concept to remember is:

> **Jenkins is an automation server that takes your source-code changes and automates the journey from code → build → test → package → deploy.**

And the most important modern Jenkins practice is:

> **Pipeline as Code — define your CI/CD workflow in a Jenkinsfile and keep it in Git.**

* * *

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