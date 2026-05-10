---
title: "📘 DevOps Week 2 – Linux OS Fundamentals & Shell Scripting"
seoTitle: "Linux Shell Scripting & AWS Resource Tracker Guide"
seoDescription: "Learn Linux commands, shell scripting & build an AWS resource tracker to automate tasks and optimize cloud costs."
datePublished: 2026-04-11T15:23:11.095Z
cuid: cmnuhi6pa01jm29ka7hbiasik
slug: devops-week-2-linux-os-fundamentals-shell-scripting
canonical: https://hritikdevopsjourney.hashnode.dev/
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/228b5828-c4ab-4d97-b6ab-1975816681c4.png
tags: programming-blogs, linux, aws, cloud-computing, automation, cli, devops, shell-scripting, beginnersguide

---

* * *

## 🔹 1. What is an Operating System (OS)?

*   OS = **Interface between Hardware & Software**
    

👉 It acts as a **bridge**:

*   Hardware (CPU, RAM, Disk)
    
*   Software (Applications, Programs)
    

* * *

## 🎯 Functions of OS:

*   Process management
    
*   Memory management
    
*   File system management
    
*   Device control
    

👉 Example OS:

*   Linux
    
*   Windows
    
*   macOS
    

* * *

# 🔹 2. What is Linux?

*   Linux = **Open-source Operating System**
    
*   Widely used in:
    
    *   Servers
        
    *   Cloud (AWS, Azure)
        
    *   DevOps
        

* * *

## ✔ Why Linux is Important

*   Free & open source
    
*   Secure
    
*   Lightweight
    
*   Most servers run on Linux
    

* * *

## 🔹 3. Linux Architecture (Basic Idea)

```plaintext
User → Shell → Kernel → Hardware
```

## ✔ Components:

*   **Kernel** → Core of OS (controls hardware)
    
*   **Shell** → Interface to interact with system
    
*   **File System** → Organizes data
    

* * *

# 🔹 4. What is Shell?

*   Shell = **Command Line Interface (CLI)**
    

👉 It allows:

*   Running commands
    
*   Managing files
    
*   Executing scripts
    

* * *

## ✔ Types of Shell:

*   Bash (most common)
    
*   Sh
    
*   Zsh
    

* * *

### 📘 Linux & Shell Scripting

* * *

### 🔹 1. Introduction

*   This video teaches:
    
    *   Basic Linux commands
        
    *   File handling
        
    *   Shell scripting basics
        
    *   Automation concepts
        

👉 Focus: **Learn Linux + start scripting**

* * *

## 🔹 2. Purpose of Scripting & Automation

*   Instead of doing tasks manually:  
    👉 Use scripts to automate
    

## ✔ Example:

*   Backup files
    
*   Run multiple commands at once
    

👉 Benefit:

*   Saves time
    
*   Reduces errors
    

* * *

## 🔹 3. How to Create a File?

```plaintext
touch file.txt
```

👉 Creates empty file

* * *

## 🔹 4. List Files & Folders

```plaintext
ls
```

👉 Shows all files

* * *

## 🔹 5. `man` Command

```plaintext
man ls
```

👉 Shows manual/help of command

* * *

## 🔹 6. vi / vim Editor (Write File)

```plaintext
vim file.txt
```

👉 Used to:

*   Create file
    
*   Edit file
    

* * *

## Modes in vim:

*   Insert mode → write text
    
*   Command mode → run commands
    

* * *

## 🔹 7. Difference: touch vs vim

| touch | vim |
| --- | --- |
| Creates file only | Create + edit file |
| No content | Can write content |

* * *

## 🔹 8. Copy Content in Linux

```plaintext
cp file1 file2
```

👉 Copy file

* * *

## 🔹 9. `#!/bin/bash` or `#!/bin/sh`

*   Called **Shebang**
    

👉 Purpose:

*   Tells system: 👉 Which shell to use to run script
    

* * *

## 🔹 10. Difference: bash, ksh, dash

| Shell | Use |
| --- | --- |
| bash | Most common |
| ksh | Advanced scripting |
| dash | Lightweight & fast |

* * *

## 🔹 11. Insert Command (vim)

*   Press `i` → enter insert mode
    
*   Start writing
    

* * *

## 🔹 12. echo Command

```plaintext
echo "Hello"
```

👉 Print output

* * *

## 🔹 13. Execute Shell Script

```plaintext
./script.sh
```

* * *

## 🔹 14. Grant Permissions

```plaintext
chmod +x script.sh
```

👉 Makes script executable

* * *

## 🔹 15. chmod Command

```plaintext
chmod 777 file.txt
```

👉 Change file permissions

* * *

## Permission Types:

*   r = read
    
*   w = write
    
*   x = execute
    

* * *

## 🔹 16. Check Command History

```plaintext
history
```

👉 Shows previously used commands

* * *

## 🔹 17. Create Folder

```plaintext
mkdir foldername
```

* * *

## 🔹 18. Change Directory

```plaintext
cd foldername
```

* * *

## 🔹 19. Simple Shell Script

```plaintext
#!/bin/bash
echo "Hello World"
```

* * *

## 🔹 20. Purpose of Shell Scripting in DevOps

*   Automate tasks
    
*   Deploy applications
    
*   Run pipelines
    

👉 Very important in DevOps

* * *

## 🔹 21. Check CPU & RAM

```plaintext
free -h
```

👉 Shows RAM

* * *

```plaintext
lscpu
```

👉 Shows CPU info

* * *

## 🔹 22. Top Command

```plaintext
top
```

👉 Shows:

*   Running processes
    
*   CPU usage
    
*   Memory usage
    

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/0e2d13e2-72d3-46cb-9a2f-ce39f4485674.png align="center")

* * *

## 📘 Node Health, Debugging, Pipes, AWK, Advanced Scripting

* * *

### 🔹 1. DevOps Use Case: Node Health Check

👉 Goal: Check if a server (node) is healthy or not

### ✔ What to check:

*   CPU usage
    
*   Memory (RAM)
    
*   Disk space
    
*   Running processes
    

* * *

### 🔹 2. Sample Node Health Script (Basic Idea)

```bash
#!/bin/bash
echo "Checking system health..."
top
free -h
df -h
```

👉 This script checks:

*   CPU → `top`
    
*   RAM → `free -h`
    
*   Disk → `df -h`
    

* * *

### 🔹 3. Good Practices in Scripting

*   Use **clear variable names**
    
*   Add **comments**
    
*   Use **echo statements**
    
*   Handle errors properly
    

👉 Makes script readable & professional

* * *

### 🔹 4. Improve Script Readability

```bash
echo "Checking CPU usage..."
echo "Checking Memory..."
```

👉 Helps understand output clearly

* * *

### 🔹 5. Debug Mode

```bash
set -x
```

👉 Shows:

*   Each command before execution
    

👉 Used for debugging

* * *

### 🔹 6. What are Processes?

*   Process = Running program
    

### ✔ List Processes:

```bash
ps
```

### ✔ Find Process ID:

```bash
ps -ef
```

* * *

### 🔹 7. grep & Pipe (|) – VERY IMPORTANT 🔥

### ✔ Pipe:

*   Pass output of one command → another
    

```bash
ps -ef | grep nginx
```

👉 Find specific process

* * *

## 🎯 Interview Point:

👉 Pipe = connects multiple commands

* * *

### 🔹 8. AWK Command

*   Used for:
    
    *   Filtering
        
    *   Extracting specific columns
        

```bash
ps -ef | awk '{print $2}'
```

👉 Prints process ID

* * *

### 🔹 9. set -e (Error Handling)

```bash
set -e
```

👉 Script stops if error occurs

* * *

### 🔹 10. set -o pipefail

```bash
set -o pipefail
```

👉 If any command in pipeline fails → script fails

👉 Important for production scripts

* * *

### 🔹 11. DevOps Use Case: Search Errors in Logs

```bash
grep "error" logfile.txt
```

👉 Used to:

*   Debug issues
    
*   Find failures
    

* * *

### 🔹 12. wget Command

```bash
wget <url>
```

👉 Download files from internet

* * *

### 🔹 13. CURL vs WGET

| CURL | WGET |
| --- | --- |
| API calls | File download |
| More flexible | Simple download |

* * *

### 🔹 14. find Command

```bash
find . -name "file.txt"
```

👉 Search files

* * *

### 🔹 15. sudo vs su

| Command | Use |
| --- | --- |
| sudo | Run as admin |
| su | Switch user |

* * *

### 🔹 16. If-Else in Shell

```bash
if [ $a -gt $b ]
then
 echo "A is greater"
else
 echo "B is greater"
fi
```

* * *

### 🔹 17. For Loop

```bash
for i in 1 2 3
do
 echo $i
done
```

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/6c70b96e-5a97-4568-b46e-c2086285f2ee.png align="center")

📘AWS Resource Tracker Project

* * *

## 🔹 1. Project Goal

👉 Build script to:

*   Track AWS resources
    
*   Reduce cost
    

* * *

## ✔ Why Important?

### Cloud = Pay-as-you-go

*   Unused resources = Money waste
    

👉 Example:

*   Unused EC2
    
*   Orphaned EBS
    

* * *

## 🔹 2. Tools Used

*   AWS CLI
    
*   Bash scripting
    
*   Cron jobs
    

* * *

### 🔹 3. Resource Tracking Commands

### ✔ S3 Buckets:

```bash
aws s3 ls
```

✔ EC2 Instances:

```bash
aws ec2 describe-instances
```

✔ Lambda:

```bash
aws lambda list-functions
```

✔ IAM Users:

```bash
aws iam list-users
```

* * *

## 🔹 4. Debug Mode

```bash
set -x
```

👉 Used to debug script

* * *

## 🔹 5. JSON Parsing using JQ

```bash
jq '.Reservations[].Instances[].InstanceId'
```

👉 Extract specific data from JSON

* * *

## 🔹 6. Automation using Cron Job

```bash
crontab -e
```

👉 Schedule script

## ✔ Example:

```bash
0 9 * * * /home/script.sh
```

👉 Runs daily at 9 AM

* * *

## 🔹 7. Full Workflow

1.  Write script
    
2.  Fetch AWS data
    
3.  Filter using JQ
    
4.  Generate report
    
5.  Automate using cron
    

* * *

## 🔹 8. Real DevOps Use Case

### 👉 Companies use this to:

*   Track unused resources
    
*   Save cost
    
*   Monitor infrastructure
    

* * *

Project link - [https://github.com/hritikranjan1/shell-scripting-projects.git](https://github.com/hritikranjan1/shell-scripting-projects.git)

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/2cb2ec19-6ae0-470c-854d-3804967d9e5a.png align="center")

* * *

# 📘 Git, GitHub, Branching & GitHub API (Simple Flow)

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/a529de49-1c62-449d-8bcb-fb3717992a85.png align="center")

* * *

### 🔹 1. Problem Statement (Real DevOps Scenario)

As a DevOps Engineer 👇

*   You manage multiple repositories
    
*   Many users have access
    

👉 Problem:

*   Checking access manually from GitHub UI is **slow & inefficient**
    
*   Especially during **employee offboarding**
    

👉 Solution:

*   Use **GitHub API + Automation Script**
    

* * *

## 🔹 2. API vs CLI (Important Concept)

### ✔ CLI (Command Line Interface)

*   Direct commands in terminal 👉 Example:
    

```bash
kubectl get pods
```

* * *

✔ API (Application Programming Interface)

*   Communicate with apps using:
    
    *   HTTP requests
        
    *   JSON data
        

👉 Example:

```bash
curl https://api.github.com/repos
```

* * *

## 🎯 Difference:

| CLI | API |
| --- | --- |
| Easy to use | More flexible |
| Limited control | Full control |
| Manual usage | Automation friendly |

* * *

## 🔹 3. GitHub API Integration (Main Concept)

👉 GitHub provides APIs to:

*   Get repo details
    
*   List users
    
*   Check PRs & issues
    

* * *

## ✔ How it works:

1.  Send request using `curl`
    
2.  Get response in JSON
    
3.  Filter using `jq`
    

* * *

## 📌 Example:

```bash
curl https://api.github.com/repos/user/repo
```

* * *

## ✔ Parsing Data:

```bash
jq '.[] | .login'
```

👉 Extract useful data from JSON

* * *

# 🔹 4. Script Flow (Project)

👉 Steps used in video:

1.  Clone script
    
2.  Add GitHub token (for authentication)
    
3.  Run script
    
4.  Fetch repo data
    
5.  Filter users
    
6.  Show authorized users
    

* * *

## ✔ Tools Used:

*   curl
    
*   jq
    
*   Bash scripting
    

* * *

## ✔ Improvement Tips:

*   Use functions
    
*   Add comments
    
*   Handle errors
    

* * *

## 🔹 5. Introduction to Version Control (VCS)

👉 VCS = Track changes in code

* * *

## ✔ Why we need VCS?

*   Multiple developers work together
    
*   Track changes/history
    
*   Go back to old version
    

* * *

## 🔹 6. Types of Version Control

## ✔ Centralized (Old)

*   Example: SVN
    
*   One central server
    

👉 Problem:

*   If server down → work stops
    

* * *

## ✔ Distributed (Git)

*   Each user has full copy
    

👉 Benefit:

*   Work even offline
    

* * *

## 🔹 7. Git vs GitHub

| Git | GitHub |
| --- | --- |
| Tool | Platform |
| Local system | Cloud |
| Version control | Collaboration |

* * *

## 🔹 8. Git Basic Workflow (Very Important 🔥)

👉 Git lifecycle:

```text
Working Directory → Staging → Repository
```

* * *

## ✔ Commands:

### 1\. Initialize repo

```bash
git init
```

* * *

### 2\. Check status

```bash
git status
```

* * *

### 3\. Add files

```bash
git add .
```

* * *

### 4\. Commit changes

```bash
git commit -m "message"
```

* * *

### 5\. View history

```bash
git log
```

* * *

### 6\. See changes

```bash
git diff
```

* * *

## 🔹 9. Push Code to GitHub

```bash
git push
```

👉 Upload local code to GitHub

* * *

## 🔹 10. Clone vs Fork

## ✔ Clone:

```bash
git clone <repo-url>
```

👉 Download repo locally

* * *

## ✔ Fork:

👉 Copy repo on GitHub

👉 Used for:

*   Open-source contribution
    

* * *

## 🔹 11. Branching Concept (VERY IMPORTANT 🔥)

## ✔ Why Branching?

*   Work on new feature safely
    
*   Don’t break main code
    

* * *

## ✔ Main Branch:

*   `main` / `master` 👉 Production-ready code
    

* * *

## ✔ Other Branches:

*   **Feature Branch** → New feature
    
*   **Release Branch** → Prepare release
    
*   **Hotfix Branch** → Fix urgent bug
    

* * *

## 🔹 12. Branch Workflow

## 👉 Steps:

1.  Create branch
    
2.  Work on feature
    
3.  Test code
    
4.  Merge to main
    

* * *

## 🔹 13. Merge Strategies

* * *

## ✔ Git Merge

*   Combine branches
    
*   Keeps history
    

* * *

## ✔ Git Rebase

*   Clean linear history
    

👉 Preferred in large projects

* * *

## ✔ Git Cherry-pick

*   Copy specific commit
    

* * *

## 🔹 14. Git Lifecycle (Full Flow)

```text
git init → git add → git commit → git push
```

* * *

## 🔹 15. Important Git Commands

*   `git pull` → Get latest code
    
*   `git remote` → Manage repo link
    
*   `git branch` → Show branches
    

* * *

## 🔹 16. Real DevOps Workflow

1.  Developer writes code
    
2.  Create feature branch
    
3.  Commit changes
    
4.  Push to GitHub
    
5.  Create PR (Pull Request)
    
6.  Review & merge
    

* * *

## 🔹 17. Key Takeaways

*   Git = Version control
    
*   GitHub = Collaboration platform
    
*   Branching = Safe development
    
*   API = Automation
    
*   Scripts = Save time
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/cdf6b0c1-a817-4c70-a43e-55fba87a3cf8.png align="center")