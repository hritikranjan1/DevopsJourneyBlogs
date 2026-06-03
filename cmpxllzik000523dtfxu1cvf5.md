---
title: "🚀 DevOps Week 9.– Complete CI/CD Journey with Jenkins & GitHub Actions"
seoTitle: "CI/CD with Jenkins & GitHub Actions | DevOps Week 9"
seoDescription: "Learn CI/CD, Jenkins, Docker Agents, Kubernetes, GitOps, GitHub Actions, and Self-Hosted Runners with practical DevOps examples."
datePublished: 2026-06-03T05:00:00.000Z
cuid: cmpxllzik000523dtfxu1cvf5
slug: devops-week-9-complete-ci-cd-journey-with-jenkins-github-actions
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/db9ee1f6-e7c4-437b-8266-f580647c6904.png
ogImage: https://cdn.hashnode.com/uploads/og-images/66fecde7cb0abd844c1a2f3c/23c5e752-6b86-464c-a5c6-414c1cadb6b4.png
tags: docker, kubernetes, cloud-computing, automation, devops, jenkins, github-actions-1, gitops, argocd, cicd-complete-proccess

---

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/318cc12b-8353-4c5a-95e5-da8538c68293.png align="center")

# 📘 Introduction to CI/CD 🚀

## 🌟 Why Modern Software Needs CI/CD

Imagine a company with hundreds of developers working on the same application. Every day, new features, bug fixes, and security updates are added. If all these changes were tested and deployed manually, software releases would take weeks or even months.

CI/CD solves this problem by automating the software delivery process, allowing teams to release applications faster, safer, and more reliably.

* * *

## 🔹 What is CI/CD? 🤔

CI/CD stands for:

### Continuous Integration (CI)

Continuous Integration is the practice of frequently merging code changes into a shared repository. Every time code is pushed, automated processes build and test the application to ensure everything works correctly.

### Continuous Delivery (CD)

Continuous Delivery is the process of automatically preparing tested code for deployment. It ensures applications can be released quickly and consistently across different environments.

Together, CI/CD helps organizations deliver software faster while maintaining quality and security.

* * *

## 🔹 Traditional Software Delivery vs CI/CD ⚔️

### Without CI/CD

❌ Manual testing

❌ Manual deployments

❌ Slow release cycles

❌ Higher chances of human errors

❌ Difficult troubleshooting

### With CI/CD

✅ Automated testing

✅ Faster deployments

✅ Better software quality

✅ Early bug detection

✅ Improved team productivity

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/30987813-4f99-4e84-b7c0-13dcc15bbf7b.png align="center")

## 🔹 How CI/CD Works? ⚙️

A typical CI/CD workflow looks like this:

Developer Writes Code  
↓  
Pushes Code to GitHub  
↓  
CI/CD Tool Detects Changes  
↓  
Application Build Starts  
↓  
Automated Tests Run  
↓  
Security & Quality Checks  
↓  
Deploy to Development Environment  
↓  
Deploy to Staging Environment  
↓  
Deploy to Production Environment

This entire process can happen automatically whenever code changes are pushed.

* * *

## 🔹 Key Stages of a CI/CD Pipeline 🚀

### Code Commit

Developers write code and push changes to a Git repository such as GitHub.

### Build Stage

The application is compiled or packaged into a deployable artifact.

Examples:

*   Java → JAR File
    
*   Node.js → Build Package
    
*   Docker → Docker Image
    

### Automated Testing

Different tests are executed automatically:

*   Unit Testing
    
*   Integration Testing
    
*   Functional Testing
    
*   End-to-End Testing
    

### Security & Quality Checks

Tools scan the application for:

*   Bugs
    
*   Vulnerabilities
    
*   Coding issues
    

### Deployment

After successful validation, the application is deployed automatically to the target environment.

* * *

## 🔹 Understanding Deployment Environments 🌍

### Development Environment (Dev)

Used by developers to test new features quickly.

### Staging Environment

A production-like environment used for final validation before release.

### Production Environment

The live environment where real users access the application.

* * *

## 🔹 Popular CI/CD Tools 🛠️

### Jenkins

One of the most widely used CI/CD tools with a large plugin ecosystem.

### GitHub Actions

A modern CI/CD solution built directly into GitHub.

### GitLab CI/CD

Integrated CI/CD platform provided by GitLab.

### Azure DevOps

Microsoft's complete DevOps platform for building and deploying applications.

* * *

## 🔹 Legacy CI/CD vs Modern CI/CD ☁️

### Legacy Approach

Earlier, organizations relied on dedicated virtual machines to run Jenkins servers.

Challenges:

*   Expensive infrastructure
    
*   Difficult scaling
    
*   High maintenance effort
    

### Modern Approach

Platforms like GitHub Actions use temporary containers or runners that start only when needed.

Benefits:

*   Lower costs
    
*   Better scalability
    
*   Faster execution
    
*   Reduced operational overhead
    

* * *

## 🔹 Real-World Example 💡

Consider an e-commerce application.

A developer adds a new payment feature and pushes the code to GitHub.

The CI/CD pipeline automatically:

*   Builds the application
    
*   Runs tests
    
*   Performs security scans
    
*   Creates deployment packages
    
*   Deploys the update
    

Within minutes, the feature is available without requiring manual intervention.

* * *

## 🔹 Benefits of CI/CD for DevOps Engineers 🚀

✅ Faster software releases

✅ Improved code quality

✅ Reduced deployment failures

✅ Better collaboration between teams

✅ Automated testing and validation

✅ Consistent deployment process

✅ Enhanced customer experience

* * *

# 🚀 Jenkins Zero to Hero | Complete Beginner Guide to CI/CD, Docker Agents, Kubernetes & GitOps

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/bb296f56-7aa9-41f6-ab2f-6bf65445fc1a.png align="center")

## 📘 Introduction

Jenkins is one of the most popular automation tools used by DevOps Engineers for implementing Continuous Integration (CI) and Continuous Delivery (CI/CD).

In modern software development, manually building, testing, and deploying applications is time-consuming and error-prone. Jenkins automates these tasks and helps teams deliver software faster and more reliably.

In this blog, we will learn:

✅ What Jenkins is

✅ Why Jenkins is important

✅ Jenkins Architecture

✅ Installing Jenkins on AWS EC2

✅ Docker as Jenkins Agents

✅ Jenkins Pipelines

✅ Multi-Stage CI/CD Pipelines

✅ Jenkins + Kubernetes + ArgoCD Workflow

✅ Real-World DevOps Use Cases

✅ Common Jenkins Interview Questions

* * *

# 🌟 Why Jenkins is Important?

Imagine a development team where developers push code multiple times every day.

Without automation:

*   Developers write code
    
*   QA tests manually
    
*   Operations team deploys manually
    

This process is slow and prone to mistakes.

Jenkins automates:

*   Building code
    
*   Running tests
    
*   Creating artifacts
    
*   Deploying applications
    

This enables faster and more reliable software delivery.

* * *

# 🤔 What is Jenkins?

Jenkins is an open-source automation server used for CI/CD.

Its main purpose is to automate software delivery pipelines.

Jenkins can:

*   Pull code from GitHub
    
*   Build applications
    
*   Run tests
    
*   Create Docker images
    
*   Deploy applications
    
*   Monitor delivery workflows
    

Think of Jenkins as a central automation engine that connects development and operations teams.

* * *

# 🔄 What is CI/CD?

### Continuous Integration (CI)

Developers frequently merge code into a shared repository.

Whenever code is pushed:

*   Build starts automatically
    
*   Tests run automatically
    
*   Issues are detected early
    

* * *

### Continuous Delivery (CD)

After successful testing:

*   Applications are prepared for deployment
    
*   Releases become faster and safer
    

* * *

### Continuous Deployment

Every successful change is automatically deployed to production without manual intervention.

* * *

# 🏗 Jenkins Architecture

Jenkins works using a Controller-Agent architecture.

### Jenkins Controller

The controller is the brain of Jenkins.

Responsibilities:

*   Manage pipelines
    
*   Schedule jobs
    
*   Store configurations
    
*   Monitor builds
    

* * *

### Jenkins Agents

Agents execute the actual work.

Examples:

*   Build code
    
*   Run tests
    
*   Create Docker images
    
*   Deploy applications
    

Instead of running everything on one machine, Jenkins distributes workloads across agents.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/1a3a3d08-8528-450b-bfc1-7235570d0f11.png align="center")

# ☁️ Installing Jenkins on AWS EC2

A common industry practice is to install Jenkins on an Ubuntu EC2 instance.

### Basic Steps

Create:

*   AWS EC2 Instance
    
*   Security Groups
    
*   SSH Access
    

Install:

```bash
sudo apt update
sudo apt install openjdk-17-jdk
```

Add Jenkins Repository:

```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
```

Install Jenkins:

```bash
sudo apt install jenkins
```

Start Service:

```bash
sudo systemctl start jenkins
```

Check Status:

```bash
sudo systemctl status jenkins
```

Access Jenkins:

```text
http://<EC2-Public-IP>:8080
```

* * *

# 🔐 Initial Jenkins Setup

After installation:

### Unlock Jenkins

Retrieve Admin Password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

### Install Suggested Plugins

Jenkins automatically recommends essential plugins.

Examples:

*   Git Plugin
    
*   Pipeline Plugin
    
*   Docker Plugin
    
*   Kubernetes Plugin
    

* * *

# 🐳 Why Use Docker as Jenkins Agents?

Traditionally, Jenkins agents were Virtual Machines.

This approach creates challenges:

❌ Expensive

❌ Slow startup

❌ Difficult dependency management

❌ Resource wastage

* * *

Docker solves these issues.

### Benefits of Docker Agents

✅ Lightweight

✅ Fast Startup

✅ Better Isolation

✅ Easy Dependency Management

✅ Lower Infrastructure Costs

* * *

# ⚙️ Jenkins + Docker Workflow

Developer Pushes Code ↓ Jenkins Triggered ↓ Docker Agent Created ↓ Build Executed ↓ Tests Executed ↓ Docker Agent Destroyed

Every build gets a fresh environment.

This ensures consistency across pipelines.

* * *

# 🧱 What is a Jenkins Pipeline?

A pipeline defines the entire CI/CD workflow as code.

Instead of clicking buttons in Jenkins UI, pipelines are written using Groovy syntax.

Benefits:

*   Version Controlled
    
*   Reusable
    
*   Easy to Maintain
    
*   Infrastructure as Code Approach
    

* * *

# 📝 Declarative Pipeline Example

```groovy
pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building Application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying Application'
            }
        }

    }
}
```

* * *

# 🚀 Key Stages in CI/CD Pipeline

### Source Stage

Pull source code from GitHub.

* * *

### Build Stage

Compile application code.

* * *

### Test Stage

Execute automated tests.

* * *

### Package Stage

Create Docker images or build artifacts.

* * *

### Security Scan Stage

Perform:

*   Vulnerability Scanning
    
*   Dependency Checks
    
*   Code Analysis
    

* * *

### Deploy Stage

Deploy application to:

*   Development
    
*   Staging
    
*   Production
    

* * *

# 🏢 Real-World Multi-Stage Pipeline

For enterprise applications:

Stage 1 → Checkout Code

Stage 2 → Build

Stage 3 → Unit Testing

Stage 4 → Security Scan

Stage 5 → Docker Image Creation

Stage 6 → Push Image to Registry

Stage 7 → Kubernetes Deployment

* * *

# ☸️ Jenkins + Kubernetes Integration

Modern organizations deploy applications on Kubernetes.

Jenkins helps automate deployments.

Workflow:

Developer ↓ GitHub ↓ Jenkins Pipeline ↓ Docker Image ↓ Container Registry ↓ Kubernetes Cluster

* * *

# 🔄 Jenkins + GitOps + ArgoCD

Modern DevOps teams increasingly use GitOps.

Instead of Jenkins directly deploying applications:

Jenkins updates deployment manifests in Git.

ArgoCD watches Git repositories.

Whenever changes occur:

ArgoCD automatically syncs them to Kubernetes.

* * *

## GitOps Workflow

Developer Pushes Code ↓ Jenkins Builds Application ↓ Docker Image Created ↓ Manifest Updated ↓ Git Repository Updated ↓ ArgoCD Detects Change ↓ Kubernetes Updated Automatically

* * *

# 🚀 Why GitOps is Better?

Benefits:

✅ Version Control

✅ Easy Rollback

✅ Audit Trail

✅ Declarative Infrastructure

✅ Improved Security

* * *

# 🏢 Real-Life Example

Suppose an E-Commerce Company deploys:

*   Frontend Service
    
*   Backend Service
    
*   Payment Service
    

Whenever developers push changes:

Jenkins:

*   Builds Docker Images
    
*   Runs Tests
    
*   Updates Kubernetes Manifests
    

ArgoCD:

*   Detects Changes
    
*   Deploys Automatically
    

Customers receive updates without downtime.

* * *

# 🎯 Common Jenkins Interview Questions

## What is Jenkins?

Jenkins is an open-source automation server used to implement CI/CD pipelines.

* * *

## What is the Difference Between CI and CD?

CI focuses on integrating and testing code continuously.

CD focuses on delivering and deploying applications continuously.

* * *

## Why Use Docker Agents in Jenkins?

Docker agents provide:

*   Isolation
    
*   Faster execution
    
*   Consistent environments
    
*   Lower infrastructure costs
    

* * *

## What is Jenkins Pipeline?

A Jenkins Pipeline is a series of automated steps defined as code to build, test, and deploy applications.

* * *

## What is Jenkinsfile?

A Jenkinsfile contains pipeline definitions written in Groovy.

It is stored inside the source code repository.

* * *

## What is GitOps?

GitOps is a deployment strategy where Git acts as the source of truth and tools like ArgoCD automatically synchronize infrastructure and applications.

* * *

## How Would You Troubleshoot a Failed Jenkins Build?

Steps:

*   Check Console Logs
    
*   Verify Agent Status
    
*   Check Git Access
    
*   Verify Dependencies
    
*   Review Pipeline Configuration
    

* * *

# 🔥 Best Practices

✅ Use Pipelines as Code

✅ Store Jenkinsfiles in Git

✅ Use Docker Agents

✅ Implement Security Scanning

✅ Integrate with Kubernetes

✅ Follow GitOps Principles

✅ Use Role-Based Access Control (RBAC)

✅ Regularly Backup Jenkins Configuration

* * *

# 🚀 GitHub Actions Complete Guide | GitHub Actions vs Jenkins | CI/CD Projects & Self-Hosted Runners

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/c0d620a2-b9ba-4d41-b4f9-196b5ff685df.png align="center")

## 📘 Introduction

Modern software development requires fast, reliable, and automated delivery of applications. Manually building, testing, and deploying code is slow, error-prone, and difficult to scale.

This is where **GitHub Actions** comes in.

GitHub Actions is GitHub's built-in CI/CD platform that allows developers to automate workflows directly inside their GitHub repositories.

In this blog, we will learn:

✅ What GitHub Actions is

✅ Why GitHub Actions is Popular

✅ How GitHub Actions Works

✅ Workflow Structure

✅ GitHub Hosted vs Self-Hosted Runners

✅ Real CI/CD Projects

✅ Managing Secrets

✅ GitHub Actions vs Jenkins

✅ Interview Questions

✅ Real-World DevOps Use Cases

* * *

# 🌟 Why Modern Software Needs CI/CD?

Imagine a team of developers pushing code multiple times every day.

Without automation:

*   Developers write code
    
*   Manual testing starts
    
*   Operations teams deploy manually
    
*   Bugs reach production
    
*   Releases become slow
    

As applications grow, manual deployments become impossible to manage.

CI/CD solves this problem by automating:

*   Building applications
    
*   Running tests
    
*   Security checks
    
*   Deployments
    

Result:

✅ Faster Releases

✅ Better Quality

✅ Reduced Human Errors

✅ Higher Productivity

* * *

# 🤔 What is GitHub Actions?

GitHub Actions is a CI/CD and automation platform built directly into GitHub.

It allows developers to automate workflows whenever specific events occur.

Examples:

*   Code Push
    
*   Pull Request Creation
    
*   Release Creation
    
*   Scheduled Tasks
    

GitHub Actions automatically executes workflows based on these events.

Think of GitHub Actions as a personal DevOps engineer inside your GitHub repository.

* * *

# 🚀 Why GitHub Actions is Popular?

GitHub Actions has become extremely popular because it is simple and fully integrated with GitHub.

Benefits include:

✅ No Separate Server Required

✅ Easy YAML Configuration

✅ Built-in GitHub Integration

✅ Large Marketplace of Actions

✅ Free for Public Repositories

✅ Supports Multiple Programming Languages

✅ Easy Kubernetes & Cloud Integrations

* * *

# ⚙️ How GitHub Actions Works?

GitHub Actions follows an event-driven approach.

Workflow:

Developer Pushes Code ↓ GitHub Detects Event ↓ Workflow Triggered ↓ Runner Executes Tasks ↓ Build & Test Application ↓ Deploy Application

Everything happens automatically.

* * *

# 🏗 Core Components of GitHub Actions

## Workflow

A workflow is an automated process.

Workflows are stored inside:

```text
.github/workflows/
```

Example:

```text
.github/workflows/ci.yml
```

* * *

## Events

Events trigger workflows.

Common events:

```yaml
on:
  push:
```

```yaml
on:
  pull_request:
```

```yaml
on:
  workflow_dispatch:
```

Examples:

*   Push Code
    
*   Create Pull Request
    
*   Schedule Jobs
    
*   Manual Trigger
    

* * *

## Jobs

A workflow contains one or more jobs.

Example:

*   Build Job
    
*   Test Job
    
*   Deploy Job
    

Each job runs independently.

* * *

## Steps

Each job contains multiple steps.

Example:

*   Checkout Code
    
*   Install Dependencies
    
*   Run Tests
    
*   Build Application
    

* * *

## Actions

Actions are reusable automation components.

Popular Actions:

### Checkout Repository

```yaml
uses: actions/checkout@v4
```

### Setup Python

```yaml
uses: actions/setup-python@v5
```

These actions save time and simplify workflow creation.

* * *

# 📁 Basic Workflow Structure

Example:

```yaml
name: Python CI

on:
  push:

jobs:

  test:

    runs-on: ubuntu-latest

    steps:

    - uses: actions/checkout@v4

    - uses: actions/setup-python@v5

    - run: pip install -r requirements.txt

    - run: pytest
```

Workflow Explanation:

*   Trigger on code push
    
*   Create Ubuntu Runner
    
*   Checkout Repository
    
*   Install Python
    
*   Install Dependencies
    
*   Run Tests
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/f6a84bb6-701f-484a-8c1b-61d6867e10eb.png align="center")

# 🐍 Project 1: Python Application Testing

Goal:

Automatically run unit tests whenever code is pushed.

Workflow:

Developer Push ↓ GitHub Actions Triggered ↓ Install Python ↓ Install Dependencies ↓ Run PyTest ↓ Display Results

Benefits:

✅ Early Bug Detection

✅ Faster Development

✅ Consistent Testing

* * *

# 🐳 Project 2: Build Docker Images Automatically

Workflow:

Developer Push ↓ GitHub Actions ↓ Build Docker Image ↓ Push Image to Docker Hub

Example Steps:

```yaml
docker build
docker push
```

Benefits:

✅ Automated Image Creation

✅ Faster Releases

✅ Consistent Builds

* * *

# ☸️ Project 3: Kubernetes Deployment

Workflow:

Developer Push ↓ GitHub Actions ↓ Build Docker Image ↓ Push to Registry ↓ Update Kubernetes Manifest ↓ Deploy Application

Benefits:

✅ Automated Deployment

✅ GitOps-Friendly Workflow

✅ Reduced Manual Work

* * *

# 🔐 Managing Secrets in GitHub Actions

Applications often require sensitive information.

Examples:

*   API Keys
    
*   Database Passwords
    
*   Kubernetes Config Files
    
*   Cloud Credentials
    

Never store secrets inside code repositories.

Instead use:

GitHub Repository → Settings → Secrets and Variables → Actions

* * *

## Examples of Secrets

```text
DOCKER_USERNAME
```

```text
DOCKER_PASSWORD
```

```text
KUBECONFIG
```

```text
AWS_ACCESS_KEY
```

* * *

![]( align="center")

# 🖥 What is a Runner?

A Runner is the machine that executes workflows.

When GitHub Actions starts:

A Runner performs:

*   Build
    
*   Test
    
*   Deploy
    

operations.

* * *

# ☁️ GitHub Hosted Runners

GitHub provides managed runners.

Examples:

```yaml
runs-on: ubuntu-latest
```

```yaml
runs-on: windows-latest
```

```yaml
runs-on: macos-latest
```

Advantages:

✅ No Infrastructure Management

✅ Fast Setup

✅ Automatically Updated

* * *

# 🏢 What is a Self-Hosted Runner?

A Self-Hosted Runner is a machine managed by your organization.

Examples:

*   EC2 Instance
    
*   Physical Server
    
*   Kubernetes Node
    

GitHub sends jobs to your machine.

* * *

# 🚀 Why Use Self-Hosted Runners?

Use cases:

### High Compute Requirements

Machine Learning Projects

Large Builds

Big Data Workloads

* * *

### Private Network Access

Internal Databases

Private APIs

On-Prem Applications

* * *

### Cost Optimization

Reduce usage of GitHub-hosted runners.

* * *

# ⚙️ How to Configure a Self-Hosted Runner?

Steps:

GitHub Repository ↓ Settings ↓ Actions ↓ Runners ↓ New Self Hosted Runner

GitHub provides commands:

```bash
mkdir actions-runner
```

```bash
./config.sh
```

```bash
./run.sh
```

After setup, workflows can use:

```yaml
runs-on: self-hosted
```

* * *

# ⚔️ GitHub Actions vs Jenkins

| Feature | GitHub Actions | Jenkins |
| --- | --- | --- |
| Hosting | Managed by GitHub | Self Managed |
| Maintenance | Minimal | High |
| Infrastructure | Not Required | Required |
| Setup Complexity | Easy | Medium to High |
| GitHub Integration | Native | Plugin Based |
| Cost | Cost Effective | Infrastructure Cost |
| Plugins | Marketplace Actions | Jenkins Plugins |
| Learning Curve | Easier | Steeper |

* * *

# 🏆 When to Choose GitHub Actions?

Use GitHub Actions when:

✅ Organization Uses GitHub

✅ Want Faster Setup

✅ Want Less Maintenance

✅ Need Modern CI/CD

✅ Prefer Managed Infrastructure

* * *

# 🏢 When to Choose Jenkins?

Use Jenkins when:

✅ Multi-VCS Support Required

✅ Vendor Independence Needed

✅ Complex Enterprise Workflows

✅ Advanced Customization Required

* * *

# 💡 Real-World Example

Suppose a company hosts applications on Kubernetes.

Whenever developers push code:

GitHub Actions:

*   Runs Tests
    
*   Builds Docker Image
    
*   Pushes Image to Registry
    
*   Updates Deployment Files
    

ArgoCD:

*   Detects Changes
    
*   Deploys Automatically
    

Result:

Fully Automated GitOps Pipeline

* * *

# 🎯 Common Interview Questions

## What is GitHub Actions?

GitHub Actions is GitHub's built-in CI/CD platform used to automate software development workflows.

* * *

## Where are workflows stored?

Inside:

```text
.github/workflows/
```

* * *

## What is a Runner?

A runner is a machine that executes GitHub Actions workflows.

* * *

## What is a Self-Hosted Runner?

A self-hosted runner is a machine managed by the organization that executes GitHub Actions jobs.

* * *

## How are secrets managed?

Using:

Repository Settings → Secrets and Variables → Actions

* * *

## GitHub Actions vs Jenkins?

GitHub Actions is easier and fully integrated with GitHub.

Jenkins provides greater flexibility and customization.

* * *

# 🔥 Best Practices

✅ Store Workflows in Git

✅ Use Secrets Instead of Hardcoding Credentials

✅ Keep Workflows Modular

✅ Use Reusable Actions

✅ Automate Testing

✅ Automate Security Scanning

✅ Follow GitOps Principles

✅ Monitor Workflow Failures

* * *