---
title: "🚀 Git & GitHub for DevOps: Complete Beginner's Guide with Commands, Branching, Git Hooks & GitHub Actions"
seoTitle: "Git & GitHub for DevOps: Beginner's Guide & Commands"
seoDescription: "Learn Git and GitHub for DevOps with essential commands, branching, merging, Git Hooks, Pull Requests, GitHub Actions, and CI/CD workflows."
datePublished: 2026-09-06T06:13:41.944Z
cuid: cmtpf1m6c00000agm56u7cnw2
slug: git-github-for-devops-complete-guide
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/e9d5150c-a133-45c2-ac13-bae0e029686e.png
tags: github, git, devops, github-actions, github-actions-1, devops-articles, gitcommands, devops-journey, devopscommunity, cicdpipeline

---

Almost every modern DevOps workflow starts with source code.

Developers write code → Git tracks the changes → GitHub stores and collaborates on the code → CI/CD tools test and deploy it.

A simple DevOps workflow looks like this:

```text
Developer
    ↓
Git
    ↓
GitHub
    ↓
GitHub Actions / CI Pipeline
    ↓
Build
    ↓
Test
    ↓
Deploy
    ↓
Production
```

In this blog, we will understand **Git and GitHub from the basics to practical DevOps workflows**.

We will cover:

*   What is Version Control?
    
*   What is Git?
    
*   What is GitHub?
    
*   Git vs GitHub
    
*   Git installation and configuration
    
*   Git repository
    
*   Git working areas
    
*   Git status
    
*   Git add
    
*   Git commit
    
*   Git log
    
*   Git diff
    
*   Git reset
    
*   Git revert
    
*   Git restore
    
*   Git clone
    
*   Git remote
    
*   Git push
    
*   Git pull
    
*   Git fetch
    
*   Git branches
    
*   Git merge
    
*   Git rebase
    
*   Git stash
    
*   Git tags
    
*   GitHub repositories
    
*   Pull Requests
    
*   Git Hooks
    
*   Pre-commit hooks
    
*   GitHub Actions
    
*   CI/CD
    
*   Common Git problems
    
*   Git interview questions
    
*   Complete Git workflow
    

Let's start from the beginning.

* * *

# 📌 Table of Contents

1.  What is Version Control?
    
2.  Why Do We Need Version Control?
    
3.  What is Git?
    
4.  What is GitHub?
    
5.  Git vs GitHub
    
6.  Git Installation
    
7.  Configure Git
    
8.  What is a Git Repository?
    
9.  Git Working Areas
    
10.  `git status`
     
11.  `git init`
     
12.  `git add`
     
13.  `git commit`
     
14.  `git log`
     
15.  `git show`
     
16.  `git diff`
     
17.  `git restore`
     
18.  `git reset`
     
19.  `git revert`
     
20.  `git clone`
     
21.  `git remote`
     
22.  `git push`
     
23.  `git pull`
     
24.  `git fetch`
     
25.  Git Branches
     
26.  Creating Branches
     
27.  Switching Branches
     
28.  Deleting Branches
     
29.  Git Merge
     
30.  Git Rebase
     
31.  Git Stash
     
32.  Git Tags
     
33.  GitHub Repository
     
34.  Pull Requests
     
35.  Code Review
     
36.  Git Hooks
     
37.  Pre-Commit Hooks
     
38.  GitHub Actions
     
39.  GitHub Actions Workflow
     
40.  CI/CD with GitHub Actions
     
41.  `.gitignore`
     
42.  Git Aliases
     
43.  Common Git Errors
     
44.  Recommended Git Workflow
     
45.  DevOps Git Workflow
     
46.  Git Cheat Sheet
     
47.  Interview Questions
     
48.  What I Learned
     
49.  Conclusion
     

* * *

# 🔄 What is Version Control?

A **Version Control System (VCS)** is a system that tracks changes made to files over time.

Imagine you are working on a project.

Initially:

```text
project/
└── app.py
```

You modify it.

Then you modify it again.

Without version control, you might create:

```text
app-final.py
app-final-new.py
app-final-new-2.py
app-final-latest.py
app-final-latest-working.py
```

😅 This quickly becomes difficult to manage.

Version control solves this problem.

It keeps a history of your changes.

```text
Version 1
   ↓
Version 2
   ↓
Version 3
   ↓
Version 4
```

You can see what changed and, when necessary, return to an earlier version.

* * *

# 🤔 Why Do We Need Version Control?

Version control provides several benefits.

### 1\. Track Changes

You can see who changed what and when.

### 2\. Collaboration

Multiple developers can work on the same project.

### 3\. Backup

The code history is preserved.

### 4\. Branching

Developers can work on different features independently.

### 5\. Rollback

You can undo unwanted changes.

### 6\. Code Review

Teams can review changes before merging them.

### 7\. CI/CD Integration

Git repositories can trigger automated testing and deployment.

* * *

# 🐙 What is Git?

**Git** is a distributed version control system.

Git runs on your local machine and tracks changes to your project.

You can use Git without GitHub.

For example:

```text
Your Computer
     |
     ↓
Git Repository
     |
     ↓
Commits
```

Git stores your project's history locally.

* * *

# ☁️ What is GitHub?

**GitHub** is a platform for hosting Git repositories and collaborating on software projects.

It provides features such as:

*   Remote repositories
    
*   Pull Requests
    
*   Code Reviews
    
*   Issues
    
*   Discussions
    
*   GitHub Actions
    
*   Project management
    
*   Collaboration
    

The relationship can be understood as:

```text
Git
 ↓
Version Control

GitHub
 ↓
Hosting + Collaboration + Automation
```

* * *

# ⚔️ Git vs GitHub

| Git | GitHub |
| --- | --- |
| Version control tool | Cloud development platform |
| Runs locally | Primarily hosted online |
| Tracks file changes | Hosts Git repositories |
| Creates commits | Stores remote repositories |
| Creates branches | Provides Pull Requests |
| Can work offline | Requires network for remote operations |
| Open-source software | Platform/service |

In simple words:

> **Git manages your code history. GitHub helps you store, share, review, and automate that Git-based project online.**

* * *

# 💻 Installing Git

Check whether Git is installed:

```bash
git --version
```

Example:

```text
git version 2.x.x
```

If Git is not installed, install it for your operating system and run the command again.

* * *

# ⚙️ Configure Git

Before making commits, configure your identity.

Set your username:

```bash
git config --global user.name "Your Name"
```

Set your email:

```bash
git config --global user.email "you@example.com"
```

Check configuration:

```bash
git config --list
```

You can also check individual values:

```bash
git config user.name
```

```bash
git config user.email
```

* * *

# 📦 What is a Git Repository?

A Git repository is a project directory that Git tracks.

Create a project:

```bash
mkdir my-project
```

Move inside:

```bash
cd my-project
```

Initialize Git:

```bash
git init
```

Git creates a hidden directory:

```text
.git/
```

This directory contains Git's internal information and history.

* * *

# 🧩 Git Working Areas

One of the most important concepts for beginners is understanding Git's working areas.

```text
Working Directory
       ↓
   git add
       ↓
Staging Area
       ↓
 git commit
       ↓
Local Repository
```

Let's understand each one.

* * *

## 1️⃣ Working Directory

This is where you create or modify files.

Example:

```text
my-project/
└── app.py
```

You edit:

```text
app.py
```

Git detects the modification.

* * *

## 2️⃣ Staging Area

You tell Git:

> I want this change to be included in my next commit.

Command:

```bash
git add app.py
```

* * *

## 3️⃣ Local Repository

You permanently record the staged changes:

```bash
git commit -m "Add application file"
```

* * *

# 🔍 `git status`

One of the most frequently used Git commands is:

```bash
git status
```

It shows:

*   Current branch
    
*   Modified files
    
*   Untracked files
    
*   Staged files
    
*   Files ready to commit
    

Example:

```bash
git status
```

You might see:

```text
Untracked files:
    app.py
```

After:

```bash
git add app.py
```

the file becomes staged.

Run:

```bash
git status
```

again.

Now Git will show that the file is ready to be committed.

* * *

# 🆕 `git init`

Create a new Git repository:

```bash
git init
```

Example:

```bash
mkdir devops-project
cd devops-project
git init
```

Output may indicate that an empty Git repository has been initialized.

* * *

# ➕ `git add`

Add one file:

```bash
git add app.py
```

Add multiple files:

```bash
git add app.py index.html
```

Add all changed files:

```bash
git add .
```

Another common form:

```bash
git add -A
```

### Example

Suppose:

```text
app.py
README.md
Dockerfile
```

You can stage everything:

```bash
git add .
```

Then check:

```bash
git status
```

* * *

# 💾 `git commit`

A commit saves staged changes into Git history.

```bash
git commit -m "Add initial application"
```

A good commit message should describe what changed.

Good:

```bash
git commit -m "Add login functionality"
```

Bad:

```bash
git commit -m "changes"
```

Better commit messages make project history easier to understand.

* * *

# 📜 `git log`

View commit history:

```bash
git log
```

A shorter format:

```bash
git log --oneline
```

Example:

```text
a82f123 Add login functionality
7bc1234 Add database configuration
3af4567 Initial commit
```

* * *

# 👀 `git show`

Display information about a particular commit:

```bash
git show <commit-id>
```

Example:

```bash
git show a82f123
```

It shows information about the commit and the changes introduced by it.

* * *

# 🔎 `git diff`

`git diff` shows changes that have not been staged.

Suppose you modify:

```text
app.py
```

Run:

```bash
git diff
```

Git shows the differences.

After staging:

```bash
git add app.py
```

use:

```bash
git diff --staged
```

to see staged changes.

* * *

# ↩️ `git restore`

`git restore` can discard changes in the working directory.

For example:

```bash
git restore app.py
```

This restores the working-tree version of the file from Git's tracked version.

⚠️ Be careful because this can discard local changes.

To unstage a file:

```bash
git restore --staged app.py
```

The file remains modified but is removed from the staging area.

* * *

# 🔄 `git reset`

`git reset` moves the current branch to another commit and can modify the staging area or working tree depending on the option.

View recent commits:

```bash
git log --oneline
```

Then, for example:

```bash
git reset --soft HEAD~1
```

This moves HEAD back one commit while keeping the changes staged.

A common option:

```bash
git reset --mixed HEAD~1
```

keeps the changes in the working directory but unstages them.

Another option:

```bash
git reset --hard HEAD~1
```

can discard local changes.

⚠️ `--hard` should be used carefully.

* * *

# ↩️ `git revert`

`git revert` creates a **new commit that reverses an earlier commit**.

Example:

```bash
git revert <commit-id>
```

This is often safer for shared branches because it doesn't rewrite existing commit history.

Conceptually:

```text
Commit A
   ↓
Commit B
   ↓
Commit C
   ↓
Revert B
   ↓
New Commit D
```

The original commit remains in history.

* * *

# 📥 `git clone`

`git clone` downloads an existing remote repository.

Example:

```bash
git clone https://github.com/username/project.git
```

Then:

```bash
cd project
```

Now you have a local copy of the repository.

* * *

# 🔗 `git remote`

A remote is a reference to a remote Git repository.

Check remotes:

```bash
git remote -v
```

Add GitHub as `origin`:

```bash
git remote add origin https://github.com/username/project.git
```

Check again:

```bash
git remote -v
```

You may see:

```text
origin  https://github.com/username/project.git (fetch)
origin  https://github.com/username/project.git (push)
```

* * *

# ⬆️ `git push`

`git push` sends your local commits to a remote repository.

Example:

```bash
git push origin main
```

The first push for a branch is often:

```bash
git push -u origin main
```

The `-u` option establishes the upstream relationship, making later pushes simpler:

```bash
git push
```

* * *

# ⬇️ `git pull`

`git pull` retrieves changes from a remote repository and integrates them into your current branch.

```bash
git pull origin main
```

In simple terms:

```text
Remote Repository
       ↓
     pull
       ↓
Local Repository
```

It generally performs a fetch followed by an integration step.

* * *

# 📡 `git fetch`

`git fetch` downloads information from a remote repository without automatically integrating those changes into your current branch.

```bash
git fetch origin
```

You can then inspect the remote changes before deciding what to merge or rebase.

A useful difference:

```text
git fetch
    ↓
Download remote changes
    ↓
Do not automatically integrate

git pull
    ↓
Fetch
    ↓
Integrate
```

* * *

# 🌿 What is a Git Branch?

A branch allows you to work on changes independently.

Suppose the main project is:

```text
main
 |
 +-- Production Code
```

You want to develop a login feature.

Create:

```text
feature/login
```

Now:

```text
main
 |
 +-- Production Code

feature/login
 |
 +-- Login Development
```

Your feature work does not have to directly modify `main`.

* * *

# 🌱 Create a Branch

Create:

```bash
git branch feature-login
```

List branches:

```bash
git branch
```

The current branch is usually marked with `*`.

* * *

# 🔀 Create and Switch to a Branch

Traditional command:

```bash
git checkout -b feature-login
```

Modern command:

```bash
git switch -c feature-login
```

The second command is easier to understand:

```text
switch -c
     ↓
create + switch
```

* * *

# 🔄 Switch Branch

Using:

```bash
git switch main
```

or:

```bash
git checkout main
```

* * *

# 🗑️ Delete a Branch

Delete a local branch:

```bash
git branch -d feature-login
```

Force deletion:

```bash
git branch -D feature-login
```

Use `-D` carefully because it can delete a branch containing unmerged work.

* * *

# 🌍 Push a New Branch to GitHub

Create:

```bash
git switch -c feature-login
```

Make changes.

Then:

```bash
git add .
```

```bash
git commit -m "Add login feature"
```

Push:

```bash
git push -u origin feature-login
```

Now the branch exists on GitHub.

* * *

# 🔀 Git Merge

Suppose:

```text
main
 |
 A---B

feature
 |
 A---B---C---D
```

After completing the feature, switch to main:

```bash
git switch main
```

Then:

```bash
git merge feature
```

The feature changes are integrated into `main`.

* * *

# ⚠️ Merge Conflicts

Sometimes two branches modify the same part of a file.

Example:

```text
main:
username = "Hritik"

feature:
username = "Developer"
```

Git may not know which version should be used.

You may see:

```text
<<<<<<< HEAD
username = "Hritik"
=======
username = "Developer"
>>>>>>> feature
```

You must manually decide which code should remain.

Then:

```bash
git add <file>
```

and:

```bash
git commit
```

The conflict is resolved.

* * *

# 🔄 Git Rebase

Rebase moves or reapplies commits onto another base.

Example:

```text
Before:

main:
A---B---C

feature:
     \
      D---E
```

After rebasing the feature onto the latest main:

```text
A---B---C---D'---E'
```

Command:

```bash
git switch feature
git rebase main
```

Rebase can create a cleaner linear history, but it rewrites commit history.

⚠️ Avoid rebasing shared public history unless you understand the consequences.

* * *

# 📦 Git Stash

Sometimes you are working on something but need to switch branches before committing.

Instead of committing incomplete work, you can temporarily stash it.

```bash
git stash
```

Your working changes are stored temporarily.

Switch branch:

```bash
git switch main
```

Do your work.

Return:

```bash
git switch feature
```

Restore stashed changes:

```bash
git stash pop
```

List stashes:

```bash
git stash list
```

* * *

# 🏷️ Git Tags

Tags are commonly used to mark releases.

For example:

```text
v1.0.0
v1.1.0
v2.0.0
```

Create a tag:

```bash
git tag v1.0.0
```

List tags:

```bash
git tag
```

Push a tag:

```bash
git push origin v1.0.0
```

Push all tags:

```bash
git push origin --tags
```

Tags are useful for release management.

* * *

# 🚫 `.gitignore`

`.gitignore` tells Git which files should not be tracked.

Example:

```text
node_modules/
.env
*.log
__pycache__/
target/
.idea/
.vscode/
```

For example:

```text
.env
```

may contain secrets.

You generally don't want it committed to a public repository.

* * *

# 🧹 Example `.gitignore`

For a Java project:

```gitignore
target/
*.class
*.log
.env
.idea/
.vscode/
```

For a Python project:

```gitignore
__pycache__/
*.pyc
.env
.venv/
```

For Node.js:

```gitignore
node_modules/
.env
dist/
```

* * *

# ☁️ Creating a GitHub Repository

A common workflow is:

```text
Create GitHub Repository
          ↓
Clone Repository
          ↓
Create/Edit Files
          ↓
git add
          ↓
git commit
          ↓
git push
```

After creating a repository on GitHub, connect your local project:

```bash
git remote add origin <repository-url>
```

Then:

```bash
git branch -M main
```

and:

```bash
git push -u origin main
```

* * *

# 🔀 What is a Pull Request?

A **Pull Request (PR)** is a GitHub feature used to propose changes from one branch to another.

Typical workflow:

```text
Developer
    ↓
Feature Branch
    ↓
Push to GitHub
    ↓
Pull Request
    ↓
Code Review
    ↓
Tests
    ↓
Approval
    ↓
Merge
    ↓
main
```

For example:

```text
main
  ↑
  |
feature/login
```

A developer creates a PR from:

```text
feature/login
```

to:

```text
main
```

* * *

# 👀 Why Are Pull Requests Important?

Pull Requests provide:

### Code Review

Other developers can inspect the changes.

### Discussion

Team members can comment on specific lines.

### Automated Testing

CI pipelines can run automatically.

### Quality Control

Changes can be verified before merging.

### Collaboration

Multiple developers can work safely on the same project.

* * *

# 🔍 Code Review

A reviewer may check:

```text
✓ Code quality
✓ Functionality
✓ Security
✓ Tests
✓ Performance
✓ Naming
✓ Documentation
```

Only after the required checks pass should the PR be merged.

* * *

# 🪝 What are Git Hooks?

Git Hooks are scripts that Git runs automatically when specific Git events occur.

Examples:

```text
pre-commit
post-commit
pre-push
post-checkout
```

Hooks are located inside:

```text
.git/hooks/
```

They can automate checks before code is committed or pushed.

* * *

# 🛡️ Pre-Commit Hooks

A pre-commit hook runs before a commit is created.

Example workflow:

```text
Developer
   ↓
git commit
   ↓
Pre-commit Hook
   ↓
Lint / Security Check
   ↓
Pass?
  / \
Yes  No
 |    |
 ↓    ↓
Commit Blocked
```

For example, a Python project can run a linting tool before allowing a commit.

* * *

# 🧪 Example Pre-Commit Concept

Suppose you have:

```text
app.py
```

You attempt:

```bash
git commit -m "Update application"
```

The hook can run:

```bash
flake8 .
```

If the check fails:

```text
Linting failed
Commit blocked
```

The developer fixes the issue and tries again.

This helps prevent low-quality code from entering the repository history.

* * *

# 🔐 Git Hooks for Secret Detection

Hooks can also help detect accidental secrets.

For example:

```text
AWS_ACCESS_KEY
API_KEY
PASSWORD
PRIVATE_KEY
TOKEN
```

before they are committed.

Conceptually:

```text
git commit
    ↓
Secret Scan
    ↓
Secret Found?
   / \
 Yes  No
  |    |
Block  Commit
```

However, local hooks should be considered a helpful layer, not the only security control.

* * *

# 🤖 What is GitHub Actions?

GitHub Actions is GitHub's automation and CI/CD platform.

It allows you to automatically run workflows when events occur in your repository.

For example:

```text
git push
   ↓
GitHub
   ↓
GitHub Actions
   ↓
Build
   ↓
Test
   ↓
Docker Build
   ↓
Deploy
```

* * *

# 📂 GitHub Actions Directory

Workflows are stored in:

```text
.github/workflows/
```

Example:

```text
.github/
└── workflows/
    └── ci.yml
```

Workflow files use YAML.

* * *

# 📝 Simple GitHub Actions Workflow

Example:

```yaml
name: CI

on:
  push:
    branches:
      - main

  pull_request:
    branches:
      - main

jobs:
  test:

    runs-on: ubuntu-latest

    steps:

      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run tests
        run: echo "Running tests..."
```

Let's understand it.

* * *

# 🧩 GitHub Actions Workflow Explained

## `name`

```yaml
name: CI
```

Name of the workflow.

* * *

## `on`

```yaml
on:
  push:
    branches:
      - main
```

Defines when the workflow runs.

For example:

```text
push
pull_request
workflow_dispatch
```

* * *

## `jobs`

```yaml
jobs:
```

Defines the work that GitHub Actions should perform.

* * *

## `runs-on`

```yaml
runs-on: ubuntu-latest
```

Defines the runner environment.

* * *

## `steps`

```yaml
steps:
```

Defines individual commands/actions.

* * *

## Checkout

```yaml
- uses: actions/checkout@v4
```

This checks out the repository code into the runner.

* * *

# 🔄 GitHub Actions CI Workflow

A more realistic Java workflow could look like:

```yaml
name: Java CI

on:
  push:
    branches:
      - main

  pull_request:
    branches:
      - main

jobs:

  build:

    runs-on: ubuntu-latest

    steps:

      - name: Checkout code
        uses: actions/checkout@v4

      - name: Set up Java
        uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - name: Build with Maven
        run: mvn clean test
```

The workflow becomes:

```text
Developer Push
      ↓
GitHub
      ↓
GitHub Actions
      ↓
Ubuntu Runner
      ↓
Checkout Code
      ↓
Install Java
      ↓
Maven Test
      ↓
PASS / FAIL
```

* * *

# 🚀 GitHub Actions for Docker

GitHub Actions can also build Docker images.

Conceptually:

```text
Git Push
   ↓
GitHub Actions
   ↓
Checkout
   ↓
Run Tests
   ↓
Docker Build
   ↓
Docker Image
   ↓
Docker Registry
   ↓
Deployment
```

This creates the foundation of a CI/CD pipeline.

* * *

# 🔐 GitHub Actions Secrets

Never hardcode sensitive credentials directly into workflow files.

GitHub provides repository/environment secrets.

Examples:

```text
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
DOCKER_USERNAME
DOCKER_PASSWORD
```

A workflow can reference secrets using:

```yaml
${{ secrets.SECRET_NAME }}
```

This is safer than writing credentials directly into YAML.

* * *

# 🔁 Complete Git + GitHub Workflow

A beginner-friendly workflow looks like:

```text
1. Create project
       ↓
2. git init
       ↓
3. Create files
       ↓
4. git status
       ↓
5. git add .
       ↓
6. git commit
       ↓
7. git remote add origin
       ↓
8. git push
       ↓
9. Create feature branch
       ↓
10. Make changes
       ↓
11. git add
       ↓
12. git commit
       ↓
13. git push
       ↓
14. Create Pull Request
       ↓
15. Code Review
       ↓
16. GitHub Actions
       ↓
17. Tests
       ↓
18. Merge
       ↓
19. Deploy
```

* * *

# 🧑‍💻 Complete Practical Example

Let's build a small project from scratch.

Create:

```bash
mkdir git-demo
cd git-demo
```

Initialize:

```bash
git init
```

Create a file:

```bash
echo "# Git Demo" > README.md
```

Check:

```bash
git status
```

Stage:

```bash
git add README.md
```

Commit:

```bash
git commit -m "Add README"
```

Create a branch:

```bash
git switch -c feature-update
```

Modify the README.

Then:

```bash
git add .
```

```bash
git commit -m "Update README"
```

Push:

```bash
git push -u origin feature-update
```

Create a Pull Request on GitHub.

After review:

```text
feature-update
      ↓
Pull Request
      ↓
Review
      ↓
GitHub Actions
      ↓
Merge
      ↓
main
```

* * *

# 🧰 Essential Git Commands Cheat Sheet

| Command | Purpose |
| --- | --- |
| `git --version` | Check Git version |
| `git config` | Configure Git |
| `git init` | Create repository |
| `git status` | Check repository status |
| `git add` | Stage changes |
| `git commit` | Create commit |
| `git log` | View history |
| `git show` | Show commit details |
| `git diff` | View changes |
| `git restore` | Restore/un-staging changes |
| `git reset` | Move/reset HEAD and staging |
| `git revert` | Create reversing commit |
| `git clone` | Clone repository |
| `git remote` | Manage remotes |
| `git push` | Upload commits |
| `git pull` | Fetch + integrate |
| `git fetch` | Download remote changes |
| `git branch` | Manage branches |
| `git switch` | Switch branches |
| `git checkout` | Older multi-purpose branch command |
| `git merge` | Merge branches |
| `git rebase` | Reapply commits onto another base |
| `git stash` | Temporarily store changes |
| `git tag` | Create release tags |
| `git clean` | Remove untracked files |
| `git reflog` | View reference history |

* * *

# 🧹 `git clean`

`git clean` removes untracked files.

First preview what would be removed:

```bash
git clean -n
```

Then remove untracked files:

```bash
git clean -f
```

⚠️ Use carefully because it can permanently remove untracked files.

* * *

# 🧭 `git reflog`

`git reflog` records updates to local references such as HEAD.

```bash
git reflog
```

It can be extremely useful when you accidentally reset or move a branch and need to locate previous states.

Example:

```text
HEAD@{0}
HEAD@{1}
HEAD@{2}
```

This is one of the most useful Git recovery commands to learn.

* * *

# 📚 Recommended Git Workflow for Beginners

Don't try to memorize hundreds of commands.

Start with these:

```text
git status
git add
git commit
git log
git branch
git switch
git merge
git clone
git pull
git push
```

Once these become comfortable, learn:

```text
git fetch
git stash
git rebase
git reset
git revert
git reflog
git tag
```

* * *

# 🏢 Git Workflow in a DevOps Team

A professional development workflow may look like:

```text
Developer
    |
    ↓
Feature Branch
    |
    ↓
Code Changes
    |
    ↓
git add
    |
    ↓
git commit
    |
    ↓
git push
    |
    ↓
Pull Request
    |
    ↓
Code Review
    |
    ↓
Automated Tests
    |
    ↓
Security Scan
    |
    ↓
Build
    |
    ↓
Merge
    |
    ↓
CI/CD Pipeline
    |
    ↓
Deployment
```

Git is therefore not just a version control tool.

It becomes an important part of the complete DevOps lifecycle.

* * *

# 🔥 Git in CI/CD

A modern pipeline can look like:

```text
GitHub
   ↓
Push / Pull Request
   ↓
GitHub Actions
   ↓
Lint
   ↓
Unit Tests
   ↓
Build
   ↓
Docker Build
   ↓
Security Scan
   ↓
Push Image
   ↓
Deploy
```

This creates a connection between:

```text
Source Control
      +
Automation
      +
Testing
      +
Deployment
```

* * *

# 🐳 Git + Docker + DevOps

For a Docker project, the repository may contain:

```text
project/
│
├── src/
├── Dockerfile
├── docker-compose.yml
├── .gitignore
├── README.md
└── .github/
    └── workflows/
        └── ci.yml
```

Then:

```text
Developer
   ↓
Git Commit
   ↓
GitHub
   ↓
GitHub Actions
   ↓
Docker Build
   ↓
Docker Registry
   ↓
Server
```

This is a very common DevOps pattern.

* * *

# ⚠️ Common Git Mistakes

## Mistake 1 — Forgetting to check status

Always start with:

```bash
git status
```

* * *

## Mistake 2 — Committing secrets

Never commit:

```text
.env
passwords
API keys
private keys
cloud credentials
```

Use `.gitignore` and proper secret management.

* * *

## Mistake 3 — Using meaningless commit messages

Avoid:

```text
update
changes
test
final
```

Prefer:

```text
Add login validation
Fix database connection
Update Docker configuration
Add CI workflow
```

* * *

## Mistake 4 — Working directly on main

For team projects, use feature branches.

```text
main
  ↑
feature/login
```

* * *

## Mistake 5 — Using `git reset --hard` carelessly

This can permanently discard local changes.

Understand the command before using it.

* * *

## Mistake 6 — Force pushing shared branches

Commands such as:

```bash
git push --force
```

can overwrite remote history.

Use force push only when you understand the consequences and have a valid reason.

* * *

# 🔐 Git Security Best Practices

### Never commit secrets

Use:

```text
.env
```

with `.gitignore`, and use a proper secret manager for production.

### Use Pull Requests

Don't allow unreviewed changes into important branches.

### Enable branch protection

Protect your main branch.

### Require CI checks

Require tests to pass before merging.

### Use secret scanning

Detect accidentally committed credentials.

### Keep dependencies updated

Security vulnerabilities can exist in dependencies even when your own code is secure.

* * *

# 🎯 Git Interview Questions

## 1\. What is Git?

Git is a distributed version control system used to track changes and manage source code history.

* * *

## 2\. What is GitHub?

GitHub is a platform for hosting Git repositories and providing collaboration and automation features.

* * *

## 3\. What is the difference between Git and GitHub?

Git is the version control system.

GitHub is a platform that hosts Git repositories and provides collaboration and automation features.

* * *

## 4\. What is a repository?

A repository is a project tracked by Git, including its files and version history.

* * *

## 5\. What is staging?

Staging is the process of selecting changes that should be included in the next commit.

Command:

```bash
git add .
```

* * *

## 6\. What is a commit?

A commit records a set of staged changes in Git history.

* * *

## 7\. What is a branch?

A branch is an independent line of development.

* * *

## 8\. What is a Pull Request?

A Pull Request is a proposal to merge changes from one branch into another, usually with review and automated checks.

* * *

## 9\. What is `git pull`?

It fetches remote changes and integrates them into the current branch.

* * *

## 10\. What is `git fetch`?

It downloads remote changes without automatically integrating them into the current branch.

* * *

## 11\. What is `git merge`?

It combines the histories of two branches.

* * *

## 12\. What is `git rebase`?

It reapplies commits onto another base commit and can create a more linear history.

* * *

## 13\. What is Git Stash?

Git stash temporarily stores local changes so you can work on something else without committing incomplete work.

* * *

## 14\. What are Git Hooks?

Scripts automatically triggered by Git events such as commits or pushes.

* * *

## 15\. What is GitHub Actions?

GitHub Actions is a platform for automating workflows such as testing, building, security checks and deployment.

* * *

# 💡 The Most Important Git Concept

If you remember only one workflow from this blog, remember:

```text
                Git Workflow

        Working Directory
                |
                | git add
                ↓
          Staging Area
                |
                | git commit
                ↓
        Local Repository
                |
                | git push
                ↓
       Remote GitHub Repository
                |
                | Pull Request
                ↓
            Code Review
                |
                ↓
        GitHub Actions / CI
                |
                ↓
             Deploy
```

Once you understand this flow, most Git concepts become much easier.

* * *

# 📈 From Git to DevOps

Git is one of the foundations of DevOps.

A typical learning path can be:

```text
Git
 ↓
GitHub
 ↓
Linux
 ↓
Shell Scripting
 ↓
Docker
 ↓
CI/CD
 ↓
AWS / Cloud
 ↓
Kubernetes
 ↓
Monitoring
```

Git comes first because CI/CD systems need a reliable source code repository.

* * *

# 🧠 What I Learned

From this Git and GitHub workshop, I learned how version control fits into the DevOps lifecycle.

The important concepts include:

*   Version Control
    
*   Git
    
*   GitHub
    
*   Repository management
    
*   Working directory
    
*   Staging area
    
*   Commits
    
*   Branches
    
*   Merging
    
*   Rebasing
    
*   Remote repositories
    
*   Push and Pull
    
*   Fetch
    
*   Pull Requests
    
*   Code Review
    
*   Git Hooks
    
*   Pre-commit checks
    
*   GitHub Actions
    
*   CI/CD automation
    

The biggest takeaway is that Git is much more than a collection of commands.

It provides the foundation for collaborative development and automated DevOps workflows.

* * *

# 🚀 Complete DevOps Workflow

Let's put everything together:

```text
                DEVELOPER
                    |
                    ↓
               Local Git
                    |
              git add/commit
                    |
                    ↓
              Feature Branch
                    |
                git push
                    ↓
                 GitHub
                    |
              Pull Request
                    |
                    ↓
               Code Review
                    |
                    ↓
             GitHub Actions
                    |
          ┌─────────┴─────────┐
          ↓                   ↓
       Testing              Build
          |                   |
          └─────────┬─────────┘
                    ↓
              Security Scan
                    |
                    ↓
              Docker Image
                    |
                    ↓
             Container Registry
                    |
                    ↓
                 Deploy
                    |
                    ↓
               Production
```

This is where Git becomes an important part of DevOps.

* * *

# 🎬 Workshop Reference

These notes are based on the Git & GitHub for DevOps workshop session through approximately **02:54:02**.

The session covered:

*   Version control fundamentals
    
*   Git and GitHub
    
*   Git workflow
    
*   Commits
    
*   Branches
    
*   Merging
    
*   Pull Requests
    
*   Git Hooks
    
*   Pre-commit checks
    
*   GitHub Actions
    
*   CI/CD concepts
    

🎥 **Workshop: Git & GitHub for DevOps**

https://www.youtube.com/live/DyqAdz96mok?si=yTWM7TqpWvtRsDTU

* * *

# 🏁 Conclusion

Git and GitHub are essential skills for anyone entering DevOps.

Git helps us:

```text
Track
Manage
Branch
Merge
Rollback
Collaborate
```

GitHub adds:

```text
Remote Repositories
Pull Requests
Code Reviews
Issues
Automation
CI/CD
```

And when GitHub is combined with GitHub Actions, Docker, cloud platforms and deployment tools, we can build complete automated DevOps pipelines.

The journey looks like:

```text
Git
 ↓
GitHub
 ↓
GitHub Actions
 ↓
Docker
 ↓
Cloud
 ↓
CI/CD
 ↓
Production
```

So don't just memorize Git commands.

**Create a repository, make changes, create branches, open Pull Requests, resolve conflicts, write GitHub Actions workflows, and build real projects.**

That's how Git becomes a real DevOps skill. 🚀

* * *

## ⭐ Quick Git Command Reference

```bash
# Configuration
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Repository
git init
git clone <url>

# Status & Changes
git status
git diff
git diff --staged

# Staging
git add <file>
git add .

# Commit
git commit -m "message"

# History
git log
git log --oneline
git show <commit>

# Undo / Recovery
git restore <file>
git restore --staged <file>
git reset
git revert <commit>
git reflog

# Remote
git remote -v
git remote add origin <url>

# Sync
git fetch
git pull
git push

# Branches
git branch
git branch <name>
git switch <name>
git switch -c <name>
git branch -d <name>

# Integration
git merge <branch>
git rebase <branch>

# Temporary Work
git stash
git stash list
git stash pop

# Releases
git tag
git tag v1.0.0
git push origin v1.0.0

# Cleanup
git clean -n
git clean -f
```

**Save this section — it works as a quick Git reference while practicing.** 🚀

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