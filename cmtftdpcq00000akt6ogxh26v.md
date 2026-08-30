---
title: "🐳 Dockerizing a Django Notes Application: Complete DevOps Project with Docker Compose, MySQL & Nginx"
seoTitle: "Dockerizing a Django Notes Application with Docker Compose,"
seoDescription: "Learn how to Dockerize a Django Notes App using Docker Compose, MySQL, Nginx, volumes, networking, healthchecks, and environment variables."
datePublished: 2026-08-30T12:57:18.806Z
cuid: cmtftdpcq00000akt6ogxh26v
slug: dockerizing-django-devops-project-docker-compose-mysql-nginx
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/4bf6306b-1b1d-42af-87d6-74897c2438ce.png
tags: docker, mysql, django, nginx, devops, dockerfile, docker-compose, docker-images, devops-articles, docker-network, devops-journey

---

In this project, I containerized a **Django Notes Application** and deployed it using **Docker and Docker Compose**.

The project demonstrates several important DevOps concepts:

*   🐳 Docker Containerization
    
*   ⚙️ Docker Compose
    
*   🐍 Django
    
*   🗄️ MySQL
    
*   🌐 Nginx Reverse Proxy
    
*   🔗 Docker Networking
    
*   💾 Docker Volumes
    
*   ❤️ Healthchecks
    
*   🔐 Environment Variables
    
*   🛡️ Docker Scout
    
*   🚀 Application Deployment
    
*   🔍 Container Troubleshooting
    

The final architecture looks like this:

```text
                    USER / BROWSER
                          |
                          | HTTP :80
                          ↓
                   +--------------+
                   |    NGINX     |
                   | Reverse Proxy|
                   +--------------+
                          |
                          | HTTP :8000
                          ↓
                   +--------------+
                   |    DJANGO    |
                   |   Backend    |
                   +--------------+
                          |
                          | MySQL :3306
                          ↓
                   +--------------+
                   |    MYSQL     |
                   |   Database   |
                   +--------------+
                          |
                          ↓
                    DOCKER VOLUME
```

This project helped me understand how multiple containers can work together as one application.

* * *

# 📌 Table of Contents

1.  [What Are We Building?](#-what-are-we-building)
    
2.  [Project Overview](#-project-overview)
    
3.  [Why Dockerize a Django Application?](#-why-dockerize-a-django-application)
    
4.  [Architecture](#-architecture)
    
5.  [Technology Stack](#-technology-stack)
    
6.  [Project Structure](#-project-structure)
    
7.  [How the Application Works](#-how-the-application-works)
    
8.  [Dockerfile](#-dockerfile)
    
9.  [Environment Variables](#-environment-variables)
    
10.  [MySQL Database](#-mysql-database)
     
11.  [Docker Networking](#-docker-networking)
     
12.  [Docker Volumes](#-docker-volumes)
     
13.  [Docker Compose](#-docker-compose)
     
14.  [Healthchecks](#-healthchecks)
     
15.  [Nginx Reverse Proxy](#-nginx-reverse-proxy)
     
16.  [Setup Requirements](#-setup-requirements)
     
17.  [Clone the Project](#-clone-the-project)
     
18.  [Configure Environment Variables](#-configure-environment-variables)
     
19.  [Build and Start Containers](#-build-and-start-containers)
     
20.  [Check Containers](#-check-running-containers)
     
21.  [Access the Application](#-access-the-application)
     
22.  [Run Django Migrations](#-run-django-migrations)
     
23.  [Connect to MySQL](#-connect-to-mysql)
     
24.  [Useful Docker Commands](#-useful-docker-commands)
     
25.  [Logs and Troubleshooting](#-logs-and-troubleshooting)
     
26.  [Common Problems](#-common-problems)
     
27.  [Docker Scout](#-docker-scout)
     
28.  [Multi-Stage Docker Builds](#-multi-stage-docker-builds)
     
29.  [.dockerignore](#-dockerignore)
     
30.  [Security Best Practices](#-security-best-practices)
     
31.  [DevOps Concepts Demonstrated](#-devops-concepts-demonstrated)
     
32.  [What I Learned](#-what-i-learned)
     
33.  [Interview Explanation](#-interview-explanation)
     
34.  [Future Improvements](#-future-improvements)
     
35.  [Conclusion](#-conclusion)
     

* * *

# 🚀 What Are We Building?

We are taking a Django Notes Application and converting it into a **multi-container Docker application**.

Instead of installing everything directly on the host machine:

```text
Windows/Linux
    |
    +-- Python
    +-- Django
    +-- MySQL
    +-- Nginx
    +-- Dependencies
```

we run the application using separate containers:

```text
Docker
 |
 +-- Django Container
 |
 +-- MySQL Container
 |
 +-- Nginx Container
```

Each component has its own responsibility.

This is one of the fundamental ideas behind containerized application architecture.

* * *

# 📋 Project Overview

The project uses:

*   **Django** for application/backend logic
    
*   **MySQL** for persistent application data
    
*   **Nginx** as a reverse proxy
    
*   **Docker** for containerization
    
*   **Docker Compose** for multi-container orchestration
    
*   `.env` for configuration
    
*   **Docker Volumes** for persistent database storage
    
*   **Healthchecks** to verify service readiness
    

The project follows a simple three-tier architecture:

```text
User
 |
 ↓
Nginx
 |
 ↓
Django
 |
 ↓
MySQL
 |
 ↓
Docker Volume
```

The project structure and components are based on the uploaded project documentation.

* * *

# 🤔 Why Dockerize a Django Application?

Without Docker, developers may need to manually install:

```text
Python
Django
MySQL
Nginx
Python packages
System dependencies
```

This can create the classic problem:

> "It works on my machine."

For example:

```text
Developer Machine
      |
      | Different Python version
      | Different packages
      | Different database configuration
      ↓
Application works differently
```

Docker solves much of this by packaging the application and its environment into reproducible containers.

The same Docker image can be used across:

```text
Development
     ↓
Testing
     ↓
Staging
     ↓
Production
```

* * *

# 🏗️ Architecture

Our application contains three primary services.

## 1️⃣ Django Container

Django is responsible for the application logic.

It:

*   Handles requests
    
*   Processes application logic
    
*   Communicates with MySQL
    
*   Runs migrations
    
*   Runs through Gunicorn
    

The internal application port is:

```text
8000
```

* * *

## 2️⃣ MySQL Container

MySQL stores application data.

It runs on:

```text
3306
```

The database configuration can look like:

```env
DB_NAME=test_db
DB_USER=root
DB_PASSWORD=root
DB_HOST=db_cont
DB_PORT=3306
```

An important Docker concept here is:

```text
db_cont
```

is the hostname used by Django to reach the MySQL container.

It is **not** the MySQL username.

The project documentation specifically uses `db_cont` as the database hostname.

* * *

## 3️⃣ Nginx Container

Nginx acts as the reverse proxy.

It accepts traffic on:

```text
Port 80
```

and forwards requests to Django:

```text
Nginx :80
      |
      ↓
Django :8000
```

So users don't need to directly access Django.

* * *

# 🧰 Technology Stack

| Technology | Purpose |
| --- | --- |
| Docker | Containerization |
| Docker Compose | Multi-container orchestration |
| Django | Backend/Application |
| Python | Programming language |
| MySQL | Database |
| Nginx | Reverse Proxy |
| Gunicorn | Django application server |
| Docker Network | Container communication |
| Docker Volume | Persistent storage |
| `.env` | Environment configuration |
| Docker Scout | Vulnerability scanning |

* * *

# 📁 Project Structure

A typical project structure looks like this:

```text
docker-devops-project/
│
├── app/
│   ├── backend/
│   │   ├── manage.py
│   │   ├── requirements.txt
│   │   ├── <django-project>/
│   │   └── <django-app>/
│   │
│   └── frontend/
│       ├── public/
│       └── src/
│
├── nginx/
│   └── nginx.conf
│
├── Dockerfile
├── docker-compose.yml
├── .env
├── .dockerignore
└── README.md
```

The exact directory names can vary depending on the repository implementation.

* * *

# 🔄 How the Application Works

When a user opens:

```text
http://localhost
```

the request follows this path:

```text
Browser
   |
   ↓
Nginx :80
   |
   ↓
Django/Gunicorn :8000
   |
   ↓
Django processes request
   |
   ↓
MySQL :3306
   |
   ↓
Database returns data
   |
   ↓
Django generates response
   |
   ↓
Nginx
   |
   ↓
Browser
```

This separation makes the application easier to maintain, troubleshoot and scale.

* * *

# 🐳 Dockerfile

A Dockerfile tells Docker how to build the application image.

The basic process is:

```text
Base Python Image
       ↓
Install System Dependencies
       ↓
Install Python Dependencies
       ↓
Copy Application
       ↓
Configure Application
       ↓
Start Django/Gunicorn
```

A Dockerfile typically contains instructions such as:

```dockerfile
FROM python:3.9

WORKDIR /app/backend

COPY requirements.txt /app/backend
RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y gcc default-libmysqlclient-dev pkg-config \
    && rm -rf /var/lib/apt/lists/*


# Install app dependencies
RUN pip install mysqlclient
RUN pip install --no-cache-dir -r requirements.txt

COPY . /app/backend

EXPOSE 8000
CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000"]
#RUN python manage.py migrate
#RUN python manage.py makemigrations
```

The exact Dockerfile should follow the application's actual dependency and startup requirements.

The important DevOps concept is that the Dockerfile turns the application source code into a reproducible Docker image.

* * *

# 🔐 Environment Variables

Hardcoding configuration inside application code is not a good practice.

Instead, configuration can be stored in:

```text
.env
```

For example:

```env
DB_NAME=test_db
DB_USER=root
DB_PASSWORD=root
DB_PORT=3306
DB_HOST=db_cont
```

MySQL can use compatible variables such as:

```env
MYSQL_DATABASE=test_db
MYSQL_ROOT_PASSWORD=root
```

### What does each variable mean?

| Variable | Meaning |
| --- | --- |
| `DB_NAME` | Database name |
| `DB_USER` | Database username |
| `DB_PASSWORD` | Database password |
| `DB_HOST` | Database hostname |
| `DB_PORT` | Database port |

The `.env` file keeps configuration separate from application source code.

### ⚠️ Important Security Rule

Never commit real credentials to GitHub.

Add:

```text
.env
```

to:

```gitignore
.env
```

For production, use a proper secrets-management solution.

* * *

# 🗄️ MySQL Database

The database runs inside its own Docker container.

Example:

```text
MySQL Container
      |
      ↓
test_db
```

Django connects to MySQL through the Docker network.

Example:

```env
DB_HOST=db_cont
DB_PORT=3306
```

Notice that we don't use:

```text
localhost
```

for the Django-to-MySQL connection.

Why?

Because inside the Django container:

```text
localhost
```

means:

```text
Django container itself
```

It does not mean the MySQL container.

Instead, Docker provides service/container-name based communication:

```text
Django Container
       |
       ↓
db_cont:3306
       |
       ↓
MySQL Container
```

* * *

# 🔗 Docker Networking

Docker Compose creates a network that allows containers to communicate.

For example:

```text
django_cont
     |
     | Docker Network
     |
     ↓
db_cont:3306
```

This means Django can connect to MySQL using:

```text
db_cont
```

rather than a hardcoded IP address.

This is much more reliable because container IP addresses can change.

Docker's internal DNS resolves the container/service name.

* * *

# 💾 Docker Volumes

One of the most important concepts in this project is **persistent storage**.

Containers are temporary.

Imagine:

```text
MySQL Container
      |
      ↓
Database Data
```

If the container is deleted without persistent storage:

```text
Container deleted
       ↓
Potential data loss
```

A Docker volume solves this problem.

```text
MySQL Container
       |
       ↓
Docker Volume
       |
       ↓
Persistent Data
```

Example:

```yaml
volumes:
  mysql_data:
```

and:

```yaml
services:
  db:
    volumes:
      - mysql_data:/var/lib/mysql
```

Now:

```text
Container removed
      ↓
Volume remains
      ↓
Database data remains
```

This is extremely important for databases.

* * *

# ⚙️ Docker Compose

Docker Compose is the central part of this project.

Instead of manually running several commands:

```bash
docker run ...
docker run ...
docker run ...
```

we define the complete architecture inside:

```text
docker-compose.yml
```

Compose can define:

*   Services
    
*   Images
    
*   Builds
    
*   Ports
    
*   Environment variables
    
*   Networks
    
*   Volumes
    
*   Dependencies
    
*   Healthchecks
    
*   Restart policies
    

Conceptually:

```yaml
version: "3.8"

services:
  nginx:
    build: ./nginx
    image: nginx
    container_name: "nginx_cont"
    ports:
      - "80:80"
    restart: always
    depends_on:
      - django_app
    networks:
      - notes-app-nw

  django_app:
    build:
      context: .
    image: django_app
    container_name: "django_cont"
    ports:
      - "8000:8000"
    command: sh -c "python manage.py migrate --noinput && gunicorn notesapp.wsgi --bind 0.0.0.0:8000"
    env_file:
      - ".env"
    depends_on:
      - db
    restart: always
    healthcheck:
      test: ["CMD-SHELL", "curl -f http://localhost:8000/admin || exit 1"]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 30s
    networks:
      - notes-app-nw

  db:
    image: mysql
    container_name: "db_cont"
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=root
      - MYSQL_DATABASE=test_db
    volumes:
      - ./data/mysql/db:/var/lib/mysql
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost", "-uroot", "-proot"]
      interval: 10s
      timeout: 5s
      retries: 5
      start_period: 60s
    networks:
      - notes-app-nw

networks:
  notes-app-nw:
```

The project documentation identifies Compose as the blueprint for the complete application stack.

* * *

# ❤️ Healthchecks

A common problem with multi-container applications is **startup order**.

Suppose:

```text
MySQL starts
       ↓
Django starts immediately
       ↓
Django tries connecting to MySQL
       ↓
MySQL is still initializing
       ↓
Connection fails
```

This can cause Django to restart.

A healthcheck allows Docker to determine whether MySQL is actually ready.

Example:

```yaml
healthcheck:
  test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
  interval: 5s
  timeout: 5s
  retries: 10
```

The flow becomes:

```text
MySQL starts
     ↓
Healthcheck
     ↓
MySQL ready
     ↓
Healthy
     ↓
Django starts/connects
```

This is different from simply checking whether the MySQL container is running.

A container can be **running** but its application may not yet be **ready**.

That's why healthchecks are useful.

* * *

# 🌐 Nginx Reverse Proxy

Nginx is the public entry point of our application.

Without Nginx:

```text
User
  ↓
Django
```

With Nginx:

```text
User
  ↓
Nginx
  ↓
Django
```

Nginx listens on:

```text
80
```

and forwards traffic to:

```text
Django :8000
```

### Why use Nginx?

Nginx can provide:

*   Reverse proxy
    
*   Static file serving
    
*   Centralized traffic handling
    
*   SSL/TLS termination
    
*   Access control
    
*   Caching
    
*   Better production architecture
    
*   Easier future scaling
    

The project therefore exposes the application through Nginx instead of making Django the primary public entry point.

* * *

# 💻 Setup & Installation

Before starting the project, install:

1.  Docker Desktop
    
2.  Git
    
3.  VS Code or another code editor
    

Check Docker:

```bash
docker --version
```

Check Docker Compose:

```bash
docker compose version
```

Check Git:

```bash
git --version
```

* * *

# 📥 Clone the Project

Clone the repository:

```bash
git clone https://github.com/hritikranjan1/django-notes-app.git
```

Move into the project directory:

```bash
cd django-notes-app
```

* * *

# 🔐 Configure Environment Variables

Create:

```text
.env
```

Example:

```env
DB_NAME=test_db
DB_USER=root
DB_PASSWORD=root
DB_PORT=3306
DB_HOST=db_cont
```

The MySQL service should use compatible configuration:

```env
MYSQL_DATABASE=test_db
MYSQL_ROOT_PASSWORD=root
```

Make sure both Django and MySQL use matching database configuration.

For learning purposes, simple values can be used.

For production, use:

*   Strong passwords
    
*   Dedicated database users
    
*   Secret managers
    
*   Environment-specific configuration
    

* * *

# 🏗️ Build and Start Containers

The recommended modern Docker Compose command is:

```bash
docker compose up -d --build
```

Let's understand what happens.

### `docker compose`

Runs Docker Compose.

### `up`

Creates and starts the services.

### `-d`

Runs containers in detached mode.

### `--build`

Builds the application image before starting.

So:

```bash
docker compose up -d --build
```

will:

```text
Build Images
     ↓
Create Network
     ↓
Create Volume
     ↓
Create Containers
     ↓
Start MySQL
     ↓
Check Health
     ↓
Start Django
     ↓
Start Nginx
```

* * *

# 🔍 Check Running Containers

Run:

```bash
docker ps
```

You should see containers similar to:

```text
db_cont
django_cont
nginx_cont
```

You can also use:

```bash
docker compose ps
```

Example:

```text
NAME          STATUS
db_cont       Up (healthy)
django_cont   Up
nginx_cont    Up
```

The project documentation uses these container names for the three-service architecture.

* * *

# 🌍 Access the Application

The recommended URL is:

```text
http://localhost
```

because traffic goes through Nginx.

If Django port `8000` is exposed, you may also test:

```text
http://localhost:8000
```

But this bypasses Nginx.

The architecture we want users to follow is:

```text
Browser
   ↓
localhost:80
   ↓
Nginx
   ↓
Django:8000
```

* * *

# 🧪 Test Django

On Windows PowerShell:

```powershell
curl.exe http://localhost:8000
```

A successful application should return an HTTP success response such as:

```text
HTTP/1.1 200 OK
```

* * *

# 🌐 Test Nginx

Run:

```powershell
curl.exe http://localhost
```

Then open:

```text
http://localhost
```

in your browser.

If the application loads, the basic architecture is working.

* * *

# 🗄️ Connect to MySQL

If the MySQL container is:

```text
db_cont
```

connect using:

```bash
docker exec -it db_cont mysql -uroot -proot
```

Once inside MySQL:

```sql
SHOW DATABASES;
```

Select the database:

```sql
USE test_db;
```

Check tables:

```sql
SHOW TABLES;
```

Exit:

```sql
exit;
```

This is useful when debugging database-related problems.

* * *

# 🔄 Run Django Migrations

Django migrations create and update the database schema required by the application.

Enter the Django container:

```bash
docker exec -it django_cont sh
```

Then:

```bash
python manage.py migrate
```

You can check migration status:

```bash
python manage.py showmigrations
```

Exit:

```bash
exit
```

You can also run migration directly:

```bash
docker exec -it django_cont python manage.py migrate
```

The project documentation specifically uses migrations to initialize the application's database tables.

* * *

# 📜 Logs and Troubleshooting

Logs are one of the most important tools when working with Docker.

## View all Compose logs

```bash
docker compose logs
```

Follow logs continuously:

```bash
docker compose logs -f
```

* * *

## Django Logs

```bash
docker logs django_cont
```

Follow:

```bash
docker logs -f django_cont
```

* * *

## MySQL Logs

```bash
docker logs db_cont
```

* * *

## Nginx Logs

```bash
docker logs nginx_cont
```

* * *

# 🔎 Check Container Status

Use:

```bash
docker compose ps
```

or:

```bash
docker ps
```

For deeper investigation:

```bash
docker inspect django_cont
```

This can show:

*   Network configuration
    
*   Environment
    
*   Mounts
    
*   Container settings
    
*   IP information
    
*   Runtime configuration
    

* * *

# 🛑 Stop the Project

To stop the application:

```bash
docker compose down
```

This removes the containers and Compose network.

Named volumes are normally preserved.

* * *

# ▶️ Start the Project Again

After stopping:

```bash
docker compose up -d
```

If code or Docker configuration changed:

```bash
docker compose up -d --build
```

* * *

# 🧹 Remove Containers and Volumes

To remove containers and volumes:

```bash
docker compose down -v
```

⚠️ **Be careful.**

Removing the MySQL volume can remove persistent database data.

Use:

```bash
docker compose down -v
```

only when you intentionally want to delete the stored database data.

* * *

# 🔄 Rebuild From Scratch

If you need a clean image rebuild:

```bash
docker compose down
```

Then:

```bash
docker compose build --no-cache
```

Then:

```bash
docker compose up -d
```

Avoid using:

```bash
docker compose down -v
```

unless you intentionally want to delete the database volume.

* * *

# 🧰 Useful Docker Commands

## List running containers

```bash
docker ps
```

## List all containers

```bash
docker ps -a
```

## List images

```bash
docker images
```

## List volumes

```bash
docker volume ls
```

## List networks

```bash
docker network ls
```

## Inspect container

```bash
docker inspect django_cont
```

## Enter Django container

```bash
docker exec -it django_cont sh
```

## Restart Django

```bash
docker compose restart django
```

## Stop Django

```bash
docker compose stop django
```

## Start Django

```bash
docker compose start django
```

* * *

# 🐞 Common Problems

## ❌ Problem 1: Django Cannot Connect to MySQL

You may see:

```text
django.db.utils.OperationalError:
Can't connect to server on 'db_cont'
```

### Possible reason

MySQL may still be initializing.

Check:

```bash
docker compose ps
```

Then:

```bash
docker logs db_cont
```

Look for:

```text
ready for connections
```

If MySQL is not ready, Django may fail to connect.

Healthchecks and dependency configuration can help solve this startup timing issue.

* * *

# ❌ Problem 2: Django Container Keeps Restarting

Check:

```bash
docker logs django_cont
```

Possible causes:

*   Database unavailable
    
*   Incorrect `.env`
    
*   Missing Python package
    
*   Migration failure
    
*   Incorrect Django settings
    
*   Incorrect startup command
    

Always start troubleshooting with the logs.

* * *

# ❌ Problem 3: Nginx Is Running But Application Does Not Open

First check:

```bash
docker logs nginx_cont
```

Then:

```bash
docker logs django_cont
```

Test Django directly:

```powershell
curl.exe http://localhost:8000
```

If:

```text
localhost:8000
```

works but:

```text
localhost
```

does not work, investigate the Nginx configuration.

* * *

# ❌ Problem 4: Port Already in Use

You may see:

```text
port is already allocated
```

On Windows, check port 80:

```powershell
netstat -ano | findstr :80
```

Check port 8000:

```powershell
netstat -ano | findstr :8000
```

This helps identify whether another process is already using the port.

* * *

# ❌ Problem 5: Database Exists But Tables Are Missing

Run:

```bash
docker exec -it django_cont python manage.py migrate
```

Then connect to MySQL:

```bash
docker exec -it db_cont mysql -uroot -proot
```

Run:

```sql
USE test_db;
SHOW TABLES;
```

If migrations were successful, the required Django tables should be present.

* * *

# ❌ Problem 6: `.env` Changes Are Not Reflected

After changing environment variables, recreate the services:

```bash
docker compose down
```

Then:

```bash
docker compose up -d --build
```

If required:

```bash
docker compose up -d --force-recreate
```

This ensures the containers are recreated with the updated configuration.

* * *

# 🛡️ Docker Scout

Security is an important part of DevOps.

Docker Scout can be used to inspect Docker images for vulnerabilities.

Run:

```bash
docker scout quickview
```

You can also scan an image:

```bash
docker scout cves <image-name>
```

The goal is to identify vulnerable packages and update the relevant base images or dependencies.

A useful DevSecOps flow is:

```text
Dockerfile
    ↓
Build Image
    ↓
Docker Scout
    ↓
Vulnerability Analysis
    ↓
Fix Vulnerabilities
    ↓
Build Again
```

* * *

# 🏭 Multi-Stage Docker Builds

For larger applications, multi-stage builds can reduce the final image size.

The basic concept is:

```text
BUILD STAGE
-----------
Install build tools
Install dependencies
Build application
       |
       ↓
RUNTIME STAGE
-------------
Copy required output
Run application
```

Benefits include:

*   Smaller images
    
*   Fewer unnecessary packages
    
*   Reduced attack surface
    
*   Faster deployments
    

The project documentation lists multi-stage builds as a potential optimization concept.

* * *

# 📦 .dockerignore

A `.dockerignore` file prevents unnecessary files from being sent to Docker during the build.

Example:

```text
.git
.gitignore
.env
__pycache__
*.pyc
venv
node_modules
README.md
```

Why is this useful?

Because we don't want unnecessary files inside our Docker build context.

It can:

*   Reduce build context size
    
*   Improve build performance
    
*   Avoid copying unnecessary files
    
*   Help prevent sensitive files from entering the build context
    

The project README includes `.dockerignore` as part of the recommended project setup.

* * *

# 🔐 Security Best Practices

For learning purposes, simple credentials such as:

```env
DB_USER=root
DB_PASSWORD=root
```

may be used.

But never use this approach for a real production system.

For production:

### 1\. Don't use MySQL root

Create a dedicated application user.

### 2\. Use strong passwords

Avoid:

```text
root
password
123456
```

### 3\. Don't commit `.env`

Add:

```text
.env
```

to:

```text
.gitignore
```

### 4\. Use secrets management

Examples include cloud secret-management solutions.

### 5\. Scan Docker images

Use Docker Scout or another image scanning solution.

### 6\. Keep images updated

Use maintained base images and update dependencies.

### 7\. Follow least privilege

Give applications only the permissions they actually need.

### 8\. Expose only required ports

Avoid unnecessarily exposing the database publicly.

### 9\. Use HTTPS

Production applications should use SSL/TLS.

### 10\. Keep the database internal

The database should generally communicate through the internal Docker network instead of being directly exposed to the internet.

These security recommendations are also included in the project's documentation.

* * *

# 🎯 DevOps Concepts Demonstrated

This project is more than just a Django application.

It demonstrates several real DevOps concepts.

## 🐳 Containerization

```text
Application
     ↓
Docker Image
     ↓
Container
```

* * *

## ⚙️ Orchestration

```text
Docker Compose
      ↓
Django + MySQL + Nginx
```

* * *

## 🔗 Networking

```text
django_cont
      ↓
Docker Network
      ↓
db_cont:3306
```

* * *

## 🌐 Reverse Proxy

```text
Client
  ↓
Nginx
  ↓
Django
```

* * *

## 💾 Persistent Storage

```text
MySQL Container
      ↓
Docker Volume
      ↓
Persistent Database Data
```

* * *

## ❤️ Healthchecks

```text
MySQL
  ↓
Healthcheck
  ↓
Healthy
  ↓
Django
```

* * *

## 🔐 Configuration

```text
.env
  ↓
Docker Compose
  ↓
Container
```

* * *

## 🛡️ Image Security

```text
Docker Image
     ↓
Docker Scout
     ↓
Vulnerability Analysis
```

The project's documentation explicitly identifies these as the key DevOps concepts demonstrated by the deployment.

* * *

# 🧠 What I Learned From This Project

After completing this project, I gained practical understanding of:

*   What Docker is
    
*   Why containers are useful
    
*   Difference between Docker image and container
    
*   What Docker Compose does
    
*   How multiple containers communicate
    
*   How Docker networking works
    
*   Why service names can act as hostnames
    
*   Why databases require persistent storage
    
*   Why Docker volumes are important
    
*   Why healthchecks matter
    
*   What `depends_on` is used for
    
*   Why Nginx is used as a reverse proxy
    
*   How Django connects to MySQL
    
*   How environment variables are passed to containers
    
*   How to inspect container logs
    
*   How to troubleshoot startup failures
    
*   How to expose ports
    
*   How to rebuild containers
    
*   How to perform Django migrations inside a container
    
*   How to scan container images for vulnerabilities
    

This turned Docker from a collection of commands into a practical deployment workflow.

* * *

# 💼 How to Explain This Project in an Interview

If an interviewer asks:

> **"Explain your Docker project."**

You can answer:

> "I created a multi-container Django Notes Application using Docker and Docker Compose. The application uses Django as the backend, MySQL for persistent data storage, and Nginx as a reverse proxy. Docker Compose manages the complete application stack, including networking, volumes, environment variables, service dependencies, and healthchecks. Django communicates with MySQL through the Docker network using the database container name as the hostname. I used Docker volumes to persist database data and healthchecks to ensure MySQL is ready before the application depends on it. Nginx acts as the public entry point on port 80 and forwards requests to the Django application running on port 8000."

This explanation covers the major DevOps concepts implemented in the project.

* * *

# 🔥 Important Interview Questions

## 1\. Why did you use Docker Compose?

Because the application contains multiple services.

Instead of manually managing each container, Docker Compose allows us to define and manage the entire stack using one configuration file.

* * *

## 2\. Why did you use a Docker volume?

Because database data needs to survive container recreation.

```text
Container
   ↓
Volume
   ↓
Persistent Data
```

* * *

## 3\. Why can't Django use `localhost` to connect to MySQL?

Because Django and MySQL run in separate containers.

Inside the Django container:

```text
localhost
```

refers to the Django container itself.

Therefore Django uses:

```text
db_cont:3306
```

to communicate with MySQL.

* * *

## 4\. Why is Nginx used?

Nginx acts as a reverse proxy and provides a single public entry point.

```text
User
 ↓
Nginx
 ↓
Django
```

* * *

## 5\. Why are healthchecks required?

Because a container being started does not always mean the application inside it is ready.

MySQL may need several seconds before accepting connections.

Healthchecks help verify readiness.

* * *

## 6\. What happens when you run `docker compose down`?

It stops and removes the Compose-managed containers and network.

Named volumes are normally preserved.

* * *

## 7\. What happens with `docker compose down -v`?

It also removes the associated volumes.

For a database, this can mean losing persistent data.

* * *

## 8\. How do you troubleshoot a container?

First:

```bash
docker compose ps
```

Then check logs:

```bash
docker logs <container>
```

For example:

```bash
docker logs django_cont
docker logs db_cont
docker logs nginx_cont
```

* * *

# 📊 Complete Project Flow

The complete deployment can be visualized as:

```text
                    ┌───────────────────┐
                    │      Browser      │
                    └─────────┬─────────┘
                              │
                           HTTP :80
                              │
                              ▼
                    ┌───────────────────┐
                    │       Nginx       │
                    │  Reverse Proxy    │
                    └─────────┬─────────┘
                              │
                           :8000
                              │
                              ▼
                    ┌───────────────────┐
                    │      Django       │
                    │     Gunicorn      │
                    └─────────┬─────────┘
                              │
                           :3306
                              │
                              ▼
                    ┌───────────────────┐
                    │       MySQL       │
                    │      test_db      │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │   Docker Volume   │
                    │ Persistent Storage│
                    └───────────────────┘
```

This is the overall flow implemented by the project.

* * *

# 📋 Quick Docker Command Cheat Sheet

```bash
# Build and start
docker compose up -d --build

# Check containers
docker compose ps

# View all logs
docker compose logs -f

# Django logs
docker logs -f django_cont

# MySQL logs
docker logs -f db_cont

# Nginx logs
docker logs -f nginx_cont

# Enter Django container
docker exec -it django_cont sh

# Run migrations
docker exec -it django_cont python manage.py migrate

# Connect to MySQL
docker exec -it db_cont mysql -uroot -proot

# Stop application
docker compose down

# Start application
docker compose up -d

# Rebuild
docker compose up -d --build

# Remove volumes
docker compose down -v
```

⚠️ Remember: use `docker compose down -v` carefully because database volumes contain persistent data.

* * *

# 🌐 Application URLs

When running locally:

### Application through Nginx

```text
http://localhost
```

### Django direct access

```text
http://localhost:8000
```

### MySQL

```text
localhost:3306
```

The preferred browser URL is:

```text
http://localhost
```

because it represents the intended Nginx reverse-proxy architecture.

* * *

# ✅ Project Success Checklist

Before considering the deployment successful, verify:

```text
[ ] Docker installed
[ ] Docker Compose available
[ ] Repository cloned
[ ] .env configured
[ ] Dockerfile available
[ ] docker-compose.yml available
[ ] Nginx configuration available
[ ] Images built successfully
[ ] MySQL container running
[ ] MySQL container healthy
[ ] Django container running
[ ] Nginx container running
[ ] Database migrations completed
[ ] Database volume configured
[ ] http://localhost works
[ ] Django logs show no critical errors
```

* * *

# 🔧 Troubleshooting Flow

When something doesn't work, don't randomly change configurations.

Follow a structured troubleshooting process:

```text
1. Check Docker
       ↓
docker --version

2. Check containers
       ↓
docker compose ps

3. Check MySQL
       ↓
docker logs db_cont

4. Check Django
       ↓
docker logs django_cont

5. Check Nginx
       ↓
docker logs nginx_cont

6. Test Django
       ↓
curl.exe http://localhost:8000

7. Test Nginx
       ↓
curl.exe http://localhost

8. Check database
       ↓
docker exec -it db_cont mysql -uroot -proot
```

This approach helps identify whether the problem is related to:

```text
Database
   ↓
Backend
   ↓
Networking
   ↓
Nginx
   ↓
Application Configuration
```

* * *

# 🚀 Future Improvements

This project can be extended into a more production-ready DevOps project.

## 1\. Add HTTPS

Configure SSL/TLS for secure communication.

```text
HTTPS
 ↓
Nginx
 ↓
Django
```

* * *

## 2\. Use a Non-Root Database User

Instead of:

```text
root
```

create a dedicated application user with only the required permissions.

* * *

## 3\. Add Redis

Redis can be introduced for:

*   Caching
    
*   Session storage
    
*   Background jobs
    

* * *

## 4\. Add Celery

Celery can handle background tasks asynchronously.

Architecture:

```text
Django
  ↓
Celery
  ↓
Redis
```

* * *

## 5\. Add CI/CD

The project can be connected to:

*   GitHub Actions
    
*   Jenkins
    

Example:

```text
Git Push
   ↓
CI Pipeline
   ↓
Run Tests
   ↓
Build Docker Image
   ↓
Security Scan
   ↓
Push Image
   ↓
Deploy
```

* * *

## 6\. Push Images to a Registry

For example:

```text
Docker Hub
```

or:

```text
Amazon ECR
```

* * *

## 7\. Deploy to AWS

The application could be deployed using:

```text
AWS EC2
```

or:

```text
AWS ECS
```

* * *

## 8\. Add Monitoring

Add:

```text
Prometheus
     +
Grafana
```

for monitoring and visualization.

* * *

## 9\. Centralized Logging

A production environment should have centralized logging so that application and infrastructure logs can be searched and analyzed.

* * *

## 10\. Kubernetes

A natural next step would be converting the Docker Compose architecture into Kubernetes manifests.

For example:

```text
Docker Compose
      ↓
Kubernetes
      ↓
Deployments
Services
ConfigMaps
Secrets
Persistent Volumes
```

These improvements are listed in the project's documentation as possible next steps.

* * *

# 📚 What This Project Taught Me About DevOps

The biggest lesson from this project is that **Docker is not just about creating containers**.

A real application requires several components to work together:

```text
Application
     +
Database
     +
Networking
     +
Persistent Storage
     +
Reverse Proxy
     +
Healthchecks
     +
Configuration
     +
Security
```

Docker Compose allows us to define this complete architecture in a repeatable way.

The result is:

```text
One Application
       ↓
Multiple Containers
       ↓
One Managed Architecture
```

This is much closer to how modern applications are deployed than simply running a single Docker container.

* * *

# 🏆 Why This Is a Good DevOps Portfolio Project

A basic Docker project might only demonstrate:

```bash
docker build
docker run
```

This project goes much further.

It demonstrates:

```text
🐳 Containerization
        +
⚙️ Orchestration
        +
🔗 Networking
        +
💾 Persistent Storage
        +
🌐 Reverse Proxy
        +
❤️ Healthchecks
        +
🔐 Environment Configuration
        +
🛡️ Security Scanning
```

That makes it a useful beginner-to-intermediate DevOps portfolio project.

It gives you something practical to discuss during interviews instead of only saying:

> "I know Docker."

You can explain:

> "I containerized a Django application, connected it to MySQL through a Docker network, persisted database data using volumes, placed Nginx in front of Django as a reverse proxy, configured service healthchecks, managed the entire stack with Docker Compose, and performed container troubleshooting and image security scanning."

That is a much stronger project explanation.

* * *

# 🎥 Reference Tutorial

This project was built while learning from the Docker-focused tutorial by **Train with Shubham**.

YouTube:

https://youtu.be/9bSbNNH4Nqw

The project documentation also references this tutorial as the learning source.

* * *

# 💻 Project Repository

GitHub:

https://github.com/hritikranjan1/django-notes-app.git

You can explore the complete Dockerized Django project, configuration files, Docker setup and documentation there.

* * *

# 📝 Conclusion

Building this Django Notes Application helped me understand how Docker can be used to deploy a complete multi-container application.

The final architecture contains:

```text
                    Browser
                       ↓
                     Nginx
                       ↓
                  Django/Gunicorn
                       ↓
                     MySQL
                       ↓
                 Docker Volume
```

And Docker Compose manages the complete environment.

The most important concepts I learned were:

*   Docker containerization
    
*   Docker images
    
*   Docker Compose
    
*   Container networking
    
*   Environment variables
    
*   Docker volumes
    
*   Database persistence
    
*   Healthchecks
    
*   Nginx reverse proxy
    
*   Django migrations
    
*   Container troubleshooting
    
*   Docker image security
    

This project also provides a strong foundation for moving toward more advanced DevOps technologies such as:

```text
CI/CD
 ↓
AWS
 ↓
Jenkins / GitHub Actions
 ↓
Monitoring
 ↓
Kubernetes
```

If you are a beginner learning Docker, I highly recommend building a project like this instead of only memorizing Docker commands.

**Learn → Build → Break → Troubleshoot → Improve.**

That's where the real DevOps learning happens. 🚀

* * *

# 🔗 Connect With Me

💼 LinkedIn: https://www.linkedin.com/in/hritikranjan1/

🌐 Website: https://hritikranjan.in

📝 DevOps Blogs: https://blogs.hritikranjan.in

💻 GitHub: https://github.com/hritikranjan1

* * *

⭐ If you found this project useful, consider giving the repository a Star!

🚀 **Built with Docker • Django • MySQL • Nginx • DevOps**

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