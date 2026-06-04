---
title: "Week  9.2 - CICD Interview Questions | GitHub Repo with Q&A"
seoTitle: "CI/CD Interview Questions & Answers for DevOps Engineers"
seoDescription: "Master CI/CD interviews with real-world scenario questions, detailed answers, Jenkins, GitHub Actions, and DevOps best practices.
"
datePublished: 2026-06-04T13:31:22.610Z
cuid: cmpzjaeee000e1shae8pq0fle
slug: week-9-2-cicd-interview-questions-github-repo-with-q-a
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/91d053de-075b-4ef3-9eb1-a1da34efa267.png
tags: devops, jenkins, interview-questions, github-actions-1, cicd-jenkins-goal

---

# 🚀 CI/CD Interview Questions & Answers for Beginners

## 1\. What is CI/CD?

### Answer:

CI/CD stands for **Continuous Integration** and **Continuous Delivery/Deployment**.

*   **Continuous Integration (CI)** means developers frequently merge their code into a shared repository where automated builds and tests are executed.
    
*   **Continuous Delivery/Deployment (CD)** means automatically deploying tested code to development, staging, or production environments.
    

### Real-Life Example:

Imagine a team of 10 developers working on the same application. Instead of manually building and testing after every code change, CI/CD automates the entire process, reducing errors and speeding up releases.

* * *

## 2\. Explain the CI/CD Process in Your Current Project.

### Answer:

In our project, we use:

*   GitHub
    
*   Jenkins
    
*   Maven
    
*   SonarQube
    
*   AppScan/Trivy
    
*   ArgoCD
    
*   Kubernetes
    
*   Prometheus & Grafana
    

### CI/CD Workflow:

**Step 1:** Developer pushes code to GitHub.

**Step 2:** Jenkins pipeline gets triggered automatically.

**Step 3:** Maven builds the application and executes unit tests.

**Step 4:** SonarQube performs code quality analysis.

**Step 5:** Security tools scan for vulnerabilities.

**Step 6:** Docker image is created.

**Step 7:** Image is pushed to a container registry.

**Step 8:** ArgoCD deploys the application to Kubernetes.

**Step 9:** Prometheus and Grafana monitor the application.

### Real-Life Scenario:

Whenever developers commit code, the complete build, testing, scanning, and deployment process happens automatically without manual intervention.

* * *

## 3\. What are the Different Ways to Trigger a Jenkins Pipeline?

### Answer:

### Webhook Trigger

GitHub sends an event to Jenkins whenever code is pushed.

**Most commonly used method.**

### Poll SCM

Jenkins checks the repository periodically.

Example:

```bash
H/5 * * * *
```

Checks every 5 minutes.

### Build Trigger

One Jenkins job can trigger another Jenkins job.

### Manual Trigger

Users manually click **Build Now**.

### Scheduled Trigger

Jobs can run at specific times using Cron syntax.

### Real-Life Scenario

Whenever a developer pushes code to GitHub, a webhook immediately triggers Jenkins to start the pipeline.

* * *

## 4\. How Do You Backup Jenkins?

### Answer:

Important Jenkins components to backup:

### Jenkins Home Directory

```bash
/var/lib/jenkins
```

Contains:

*   Jobs
    
*   Plugins
    
*   Credentials
    
*   Build History
    
*   Configurations
    

### Plugin Backup

```bash
JENKINS_HOME/plugins
```

### Job Backup

```bash
JENKINS_HOME/jobs
```

### Best Practice

Schedule automatic backups using:

*   Cron Jobs
    
*   AWS Backup
    
*   Snapshots
    
*   Cloud Storage
    

### Real-Life Scenario

If Jenkins server crashes, backup helps restore all pipelines and configurations quickly.

* * *

## 5\. How Do You Store Secrets in Jenkins?

### Answer:

### Jenkins Credentials Plugin

Used to securely store:

*   Passwords
    
*   API Keys
    
*   SSH Keys
    
*   Certificates
    

### HashiCorp Vault

Enterprise-level secret management.

### Cloud Secret Managers

Examples:

*   AWS Secrets Manager
    
*   Azure Key Vault
    
*   Google Secret Manager
    

### Avoid

❌ Hardcoding passwords in Jenkinsfiles.

### Real-Life Scenario

Instead of writing database passwords in code, Jenkins retrieves them securely from Vault during deployment.

* * *

## 6\. What is the Latest Version of Jenkins You Are Using?

### Answer:

Interviewers ask this question to verify whether you actually work with Jenkins regularly.

You should always know:

*   Current Jenkins Version
    
*   LTS Version
    
*   Recently used version in your project
    

### Example Answer:

"We are currently using Jenkins LTS version in our production environment."

* * *

## 7\. What are Shared Libraries in Jenkins?

### Answer:

Shared Libraries allow reusable pipeline code across multiple projects.

Instead of writing the same pipeline logic repeatedly, teams store common functions in one location.

### Benefits

*   Reusability
    
*   Consistency
    
*   Easy Maintenance
    
*   Reduced Duplication
    

### Real-Life Scenario

A deployment function can be written once and used by 50 different projects.

* * *

## 8\. Can Jenkins Build Applications with Multiple Programming Languages?

### Answer:

Yes.

Jenkins supports multiple agents and environments.

Example:

### Stage 1

Java Application

```bash
mvn clean package
```

### Stage 2

Node.js Application

```bash
npm install
npm test
```

### Stage 3

Python Application

```bash
pytest
```

### Real-Life Scenario

A microservices application may contain:

*   Java Backend
    
*   Node.js Frontend
    
*   Python Automation Scripts
    

Jenkins can build all of them using different agents.

* * *

## 9\. How Can You Set Up Auto Scaling for Jenkins in AWS?

### Answer:

### High-Level Steps

1.  Create EC2 Instance
    
2.  Install Jenkins
    
3.  Create AMI
    
4.  Create Launch Template
    
5.  Create Auto Scaling Group
    
6.  Configure Scaling Policies
    
7.  Attach Load Balancer
    
8.  Monitor using CloudWatch
    

### Benefits

*   High Availability
    
*   Automatic Scaling
    
*   Better Performance
    

### Real-Life Scenario

During heavy deployment hours, AWS automatically launches additional Jenkins agents.

* * *

## 10\. How Do You Add a New Worker Node in Jenkins?

### Answer:

### Steps

1.  Manage Jenkins
    
2.  Manage Nodes
    
3.  New Node
    
4.  Configure Node Name
    
5.  Add SSH Credentials
    
6.  Launch Agent
    

### Why Worker Nodes?

Worker nodes distribute build workloads and improve scalability.

### Real-Life Scenario

Instead of running all builds on a single Jenkins server, builds run on multiple worker machines.

* * *

## 11\. What is JNLP in Jenkins?

### Answer:

JNLP stands for:

**Java Network Launch Protocol**

It allows Jenkins agents to connect to the Jenkins Controller remotely.

### Why Use JNLP?

*   Remote Agents
    
*   Cloud Agents
    
*   Dynamic Scaling
    
*   Kubernetes Agents
    

### Real-Life Scenario

A Jenkins agent running inside Kubernetes can connect back to the Jenkins Controller using JNLP.

* * *

## 12\. What Are Some Common Jenkins Plugins You Use?

### Answer:

### Git Plugin

Source code integration.

### Pipeline Plugin

Pipeline support.

### Docker Plugin

Docker builds and containers.

### Kubernetes Plugin

Dynamic Kubernetes agents.

### SonarQube Plugin

Code quality analysis.

### Slack Plugin

Notifications.

### Blue Ocean

Modern Jenkins UI.

### Real-Life Scenario

A CI/CD pipeline often uses Git, SonarQube, Docker, and Slack plugins together.

* * *

## 13\. GitHub Actions vs Jenkins?

### Answer:

| Feature | Jenkins | GitHub Actions |
| --- | --- | --- |
| Hosting | Self-hosted | GitHub Managed |
| Setup | Complex | Easy |
| Maintenance | High | Low |
| Cost | Infrastructure Required | Free for Public Repositories |
| Plugins | Large Ecosystem | Marketplace Actions |
| Integration | Multiple Platforms | GitHub Focused |

* * *

## 14\. What Are the Advantages of GitHub Actions?

### Answer:

### Easy Setup

Create:

```bash
.github/workflows/
```

and start building workflows.

### No Server Maintenance

GitHub manages infrastructure.

### Cost Effective

Free for public repositories.

### Better Integration

Works seamlessly with GitHub repositories.

### Real-Life Scenario

Small startups often choose GitHub Actions because they don't want to maintain Jenkins servers.

* * *

## 15\. What Are the Advantages of Jenkins?

### Answer:

### Platform Independent

Supports:

*   GitHub
    
*   GitLab
    
*   Bitbucket
    
*   Azure DevOps
    

### Huge Plugin Ecosystem

Thousands of plugins available.

### Highly Customizable

Suitable for enterprise environments.

### Real-Life Scenario

Large organizations prefer Jenkins because it can integrate with almost any tool.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/262cb67a-a84f-4769-a62a-c51cb9c1b73a.png align="center")

# 🎯 Real-Time Scenario Based Interview Questions

## 16\. Your Deployment Failed After a Code Merge. What Will You Do?

### Answer:

1.  Check Jenkins Console Logs.
    
2.  Verify Git Changes.
    
3.  Review SonarQube Reports.
    
4.  Check Docker Build Logs.
    
5.  Verify Kubernetes Pods.
    

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

6.  Rollback Deployment if needed.
    

```bash
kubectl rollout undo deployment/app
```

* * *

## 17\. How Would You Secure a CI/CD Pipeline?

### Answer:

*   Store secrets in Vault or Credentials Manager.
    
*   Enable RBAC.
    
*   Use Security Scanning Tools.
    
*   Restrict Production Access.
    
*   Encrypt Sensitive Data.
    
*   Enable Audit Logs.
    

### Real-Life Scenario

A leaked API key can compromise the entire infrastructure. Proper secret management prevents such incidents.

* * *

## 18\. Why Do Companies Use ArgoCD with Jenkins?

### Answer:

Jenkins handles CI tasks:

*   Build
    
*   Test
    
*   Security Scan
    
*   Docker Image Creation
    

ArgoCD handles CD tasks:

*   Kubernetes Deployment
    
*   GitOps
    
*   Rollbacks
    
*   Desired State Management
    

### Real-Life Scenario

Developer pushes code → Jenkins builds image → Git repo updated → ArgoCD automatically deploys to Kubernetes.

* * *

* * *

# 🚀 Continue Your Learning Journey

Thank you for taking the time to read this article.

Technology is evolving rapidly, and continuous learning is one of the most valuable investments you can make in your career. Whether you're exploring **DevOps, Cloud Computing, Artificial Intelligence, Cybersecurity, Software Development, Data Science, or Career Growth**, the resources below can help you deepen your knowledge and stay ahead in the industry.

* * *

# 🎓 Recommended Learning Platforms

## 🚀 Coursera

Learn from world-renowned universities and industry leaders including Google, IBM, Stanford, Microsoft, Meta, and many more.

✔ Professional Certificates ✔ Career-focused Learning Paths ✔ AI & Machine Learning Programs ✔ Cloud & DevOps Certifications ✔ Business & Leadership Courses

🔗 [https://imp.i384100.net/k0KvbV](https://imp.i384100.net/k0KvbV)

* * *

## 💻 Udemy

One of the largest online learning platforms with practical, hands-on courses covering:

✔ DevOps & Kubernetes ✔ Docker & Cloud Computing ✔ AWS, Azure & GCP ✔ Programming & Development ✔ Cybersecurity & Ethical Hacking

🔗 [https://trk.udemy.com/MAL2MY](https://trk.udemy.com/MAL2MY)

* * *

## 📊 DataCamp

A great platform for anyone interested in:

✔ Python Programming ✔ SQL & Databases ✔ Data Analytics ✔ Machine Learning ✔ Artificial Intelligence

Interactive learning paths and hands-on projects make it ideal for beginners and professionals alike.

🔗 [https://datacamp.pxf.io/nX4kER](https://datacamp.pxf.io/nX4kER)

* * *

## 🎓 edX

Access high-quality courses and certifications from leading institutions such as:

✔ Harvard University ✔ MIT ✔ Berkeley ✔ Microsoft

Perfect for learners seeking university-level education online.

🔗 [https://edx.sjv.io/POvVeN](https://edx.sjv.io/POvVeN)

* * *

## 🎨 Domestika

Enhance your creative skills with courses on:

✔ Graphic Design ✔ Video Editing ✔ Animation ✔ Digital Marketing ✔ Content Creation

🔗 [https://domestika.sjv.io/dynKAW](https://domestika.sjv.io/dynKAW)

* * *

# 🛠️ Recommended Tools & Resources

## 🔥 AppSumo

Discover exclusive lifetime deals on:

✔ AI Tools ✔ Productivity Software ✔ Developer Utilities ✔ Marketing Platforms ✔ Business Applications

A must-have resource for developers, creators, freelancers, and entrepreneurs looking to save money while accessing premium tools.

🔗 [https://appsumo.8odi.net/L04a33](https://appsumo.8odi.net/L04a33)

* * *

## 🛒 Shopify

Looking to start an online business or launch an eCommerce store?

Shopify provides everything you need to build, manage, and scale an online business.

✔ Online Store Builder ✔ Payment Integration ✔ Inventory Management ✔ Marketing Tools

🔗 [https://shopify.pxf.io/Vxv09k](https://shopify.pxf.io/Vxv09k)

* * *

## 🌐 WordPress, WooCommerce & Jetpack

Create professional websites, blogs, and online stores with one of the most trusted web ecosystems in the world.

Ideal for:

✔ Personal Blogs ✔ Portfolio Websites ✔ Business Websites ✔ eCommerce Stores

🔗 [https://automattic.pxf.io/Z6vR5W](https://automattic.pxf.io/Z6vR5W)

* * *

# 🌍 Language Learning Resources

## 🗣️ Preply

Learn English and other languages through personalized one-on-one tutoring sessions with experts from around the world.

🔗 [https://preply.sjv.io/o4gBDY](https://preply.sjv.io/o4gBDY)

* * *

## 📚 British Council English Online

Improve your professional communication skills and English fluency through structured learning programs.

🔗 [https://englishonline.sjv.io/9VOGa4](https://englishonline.sjv.io/9VOGa4)

* * *

## 🧠 Rosetta Stone

One of the most recognized language-learning platforms for immersive language acquisition.

🔗 [https://aff.rosettastone.com/X4OyqG](https://aff.rosettastone.com/X4OyqG)

* * *

# 🧪 Science & Educational Resources

## 🔬 MEL Science

Interactive science kits and educational experiences designed to make STEM learning engaging and practical.

🔗 [https://imp.i328067.net/bk2beg](https://imp.i328067.net/bk2beg)

* * *

## 📖 Carson Dellosa Education

Educational materials and learning resources for students, teachers, and lifelong learners.

🔗 [https://carsondellosaeducation.sjv.io/E0JbjW](https://carsondellosaeducation.sjv.io/E0JbjW)

* * *

# ❤️ Support My Work

Creating detailed technical content, tutorials, guides, and learning resources takes significant time and effort.

If you find my articles helpful and would like to support my work, you can do so through the following platforms:

## ⭐ Become a GitHub Sponsor

Support my open-source contributions, technical content, and community projects.

🔗 [https://github.com/sponsors/hritikranjan1](https://github.com/sponsors/hritikranjan1)

* * *

## ☕ Buy Me a Chai

Enjoying my content? Consider buying me a chai and supporting future tutorials, guides, and educational resources.

🔗 [https://www.chai4.me/hritikranjan](https://www.chai4.me/hritikranjan)

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

✅ Share it with your network  
✅ Bookmark it for future reference  
✅ Follow for more DevOps, AI, Cloud, Cybersecurity, and Software Engineering content

Thank you for reading and being part of this learning journey.

**Keep Learning. Keep Building. Keep Growing. 🚀**