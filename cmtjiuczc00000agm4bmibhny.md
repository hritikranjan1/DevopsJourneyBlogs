---
title: "🐳 Dockerizing a Three-Tier Java Spring Boot Application with Docker Compose & MySQL"
seoTitle: "Dockerizing Spring Boot with Docker Compose & MySQL"
seoDescription: "Learn how to Dockerize a Java Spring Boot application with MySQL using Docker Compose, multi-stage builds, networking, volumes, and healthchecks."
datePublished: 2026-09-01T05:00:00.000Z
cuid: cmtjiuczc00000agm4bmibhny
slug: docker-spring-boot-mysql-docker-compose
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/f2e2abff-04b5-4ae3-8049-a77b6a7cfb2f.png
tags: docker, java, maven, devops, spring-boot, java-programming, dockerfile, docker-compose, docker-images, devops-articles, docker-network, devops-journey, docker-volume, devopscommunity, spring-boot-development

---

In this project, I deployed a **three-tier Java Spring Boot application** using **Docker and Docker Compose**.

The application contains:

*   ☕ Java Spring Boot backend
    
*   🗄️ MySQL database
    
*   🐳 Docker containers
    
*   ⚙️ Docker Compose
    
*   📦 Maven
    
*   🔗 Docker networking
    
*   💾 Docker volumes
    
*   ❤️ Healthchecks
    
*   🔐 Environment variables
    
*   🏗️ Multi-stage Docker build
    
*   🔄 Automatic restart policies
    

The goal was not simply to run a Java application inside Docker.

The goal was to understand how a **Java application, database, networking, configuration, persistence, and container orchestration** work together.

* * *

# 📌 Table of Contents

1.  [What Are We Building?](#-what-are-we-building)
    
2.  [Project Overview](#-project-overview)
    
3.  [Why Dockerize a Spring Boot Application?](#-why-dockerize-a-spring-boot-application)
    
4.  [Application Architecture](#-application-architecture)
    
5.  [Technology Stack](#-technology-stack)
    
6.  [How the Application Works](#-how-the-application-works)
    
7.  [Project Structure](#-project-structure)
    
8.  [Spring Boot Application](#-spring-boot-application)
    
9.  [Maven and pom.xml](#-maven-and-pomxml)
    
10.  [Application Properties](#-application-properties)
     
11.  [Environment Variables](#-environment-variables)
     
12.  [Dockerfile](#-dockerfile)
     
13.  [Why Use a Multi-Stage Dockerfile?](#-why-use-a-multi-stage-dockerfile)
     
14.  [Docker Build Stage](#-docker-build-stage)
     
15.  [Docker Runtime Stage](#-docker-runtime-stage)
     
16.  [MySQL Database](#-mysql-database)
     
17.  [Docker Networking](#-docker-networking)
     
18.  [Docker Volumes](#-docker-volumes)
     
19.  [Docker Compose](#-docker-compose)
     
20.  [Healthchecks](#-healthchecks)
     
21.  [Restart Policies](#-restart-policies)
     
22.  [Complete Setup](#-complete-setup)
     
23.  [Clone the Project](#-clone-the-project)
     
24.  [Build and Start Containers](#-build-and-start-containers)
     
25.  [Check Running Containers](#-check-running-containers)
     
26.  [Access the Application](#-access-the-application)
     
27.  [Check Application Logs](#-check-application-logs)
     
28.  [Check MySQL Logs](#-check-mysql-logs)
     
29.  [Connect to MySQL](#-connect-to-mysql)
     
30.  [Useful Docker Commands](#-useful-docker-commands)
     
31.  [Troubleshooting](#-troubleshooting)
     
32.  [Common Problems](#-common-problems)
     
33.  [Security Best Practices](#-security-best-practices)
     
34.  [Why Multi-Stage Builds Matter](#-why-multi-stage-builds-matter)
     
35.  [DevOps Concepts Demonstrated](#-devops-concepts-demonstrated)
     
36.  [Interview Explanation](#-interview-explanation)
     
37.  [Interview Questions](#-interview-questions)
     
38.  [Future Improvements](#-future-improvements)
     
39.  [What I Learned](#-what-i-learned)
     
40.  [Conclusion](#-conclusion)
     

* * *

# 🚀 What Are We Building?

We are taking a **Java Spring Boot application** and converting it into a containerized application.

The final architecture contains two main Docker services:

```text
                    USER
                     |
                     ↓
              Spring Boot App
                     |
                     ↓
                  MySQL
                     |
                     ↓
              Docker Volume
```

Docker Compose manages these services.

Instead of installing Java, Maven and MySQL directly on the host machine, we package the application and database into containers.

The result is a reproducible environment that can be started with a single command.

* * *

# 📋 Project Overview

This project demonstrates how to deploy a Spring Boot application using Docker Compose.

The architecture contains:

### ☕ Application

A Java Spring Boot application built using Maven.

### 🗄️ Database

A MySQL database responsible for storing application data.

### 🐳 Docker

Docker packages the application and its environment into containers.

### ⚙️ Docker Compose

Docker Compose manages the complete multi-container environment.

### 💾 Volume

A Docker volume keeps MySQL data persistent.

### ❤️ Healthcheck

A healthcheck verifies whether MySQL is actually ready.

* * *

# 🤔 Why Dockerize a Spring Boot Application?

Normally, deploying a Spring Boot application requires:

```text
Java
Maven
Application dependencies
MySQL
Database configuration
Environment configuration
```

Different machines can have different versions of these components.

For example:

```text
Developer Machine
Java 17
Maven version A
MySQL version X

        ↓

Production Machine
Java 21
Maven version B
MySQL version Y
```

This can create compatibility problems.

Docker allows us to package the application environment into reproducible containers.

The deployment becomes:

```text
Source Code
     ↓
Docker Image
     ↓
Container
     ↓
Application
```

The same image can then be used in:

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

# 🏗️ Application Architecture

The project follows a simple three-tier architecture:

```text
┌─────────────────────────┐
│          USER           │
│       Web Browser       │
└────────────┬────────────┘
             │
             │ HTTP
             ↓
┌─────────────────────────┐
│     SPRING BOOT APP     │
│                         │
│        Java             │
│        Spring Boot      │
│        Thymeleaf        │
└────────────┬────────────┘
             │
             │ MySQL :3306
             ↓
┌─────────────────────────┐
│          MYSQL          │
│                         │
│       Database          │
└────────────┬────────────┘
             │
             ↓
┌─────────────────────────┐
│     DOCKER VOLUME       │
│   Persistent Database   │
│          Data           │
└─────────────────────────┘
```

Docker Compose manages the application and database services.

* * *

# 🧰 Technology Stack

| Technology | Purpose |
| --- | --- |
| Java | Programming language |
| Spring Boot | Application framework |
| Maven | Build and dependency management |
| Thymeleaf | Server-side UI templating |
| MySQL | Relational database |
| Docker | Containerization |
| Docker Compose | Container orchestration |
| Docker Network | Service communication |
| Docker Volume | Persistent storage |
| Healthcheck | Service readiness |
| Environment Variables | Configuration management |

* * *

# 🔄 How the Application Works

When the user opens the application:

```text
Browser
   |
   ↓
Spring Boot Container
   |
   ↓
Spring Boot processes request
   |
   ↓
Application communicates with MySQL
   |
   ↓
MySQL returns data
   |
   ↓
Spring Boot processes data
   |
   ↓
Thymeleaf generates response
   |
   ↓
Browser
```

The important part is that the Java application and MySQL database are running in separate containers.

* * *

# 📁 Project Structure

A typical structure can look like:

```text
java-docker-project/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   └── resources/
│   │       ├── templates/
│   │       └── application.properties
│   │
│   └── test/
│
├── pom.xml
├── Dockerfile
├── docker-compose.yml
└── README.md
```

The most important files are:

```text
pom.xml
Dockerfile
docker-compose.yml
application.properties
```

Each file has a different responsibility.

* * *

# ☕ Spring Boot Application

Spring Boot provides the main application framework.

It handles:

*   HTTP requests
    
*   Business logic
    
*   Database communication
    
*   Application configuration
    
*   Dependency management
    
*   Web interface
    

The application can use Thymeleaf for server-side HTML rendering.

The architecture is therefore:

```text
Browser
   ↓
Spring Boot
   ↓
Thymeleaf
   ↓
MySQL
```

* * *

# 📦 Maven and pom.xml

Maven is the build and dependency management tool used by the Java application.

The main configuration file is:

```text
pom.xml
```

The POM defines project information and dependencies.

For example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>3.2.2</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.Spring-Boot-MVC</groupId>
	<artifactId>ExpensesTracker</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>ExpensesTracker</name>
	<description>Demo project for Spring Boot</description>
	<properties>
		<java.version>17</java.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-data-jpa</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-security</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-thymeleaf</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-validation</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>
		<dependency>
			<groupId>org.thymeleaf.extras</groupId>
			<artifactId>thymeleaf-extras-springsecurity6</artifactId>
		</dependency>

		<dependency>
			<groupId>com.mysql</groupId>
			<artifactId>mysql-connector-j</artifactId>
			<scope>runtime</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.springframework.security</groupId>
			<artifactId>spring-security-test</artifactId>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

The exact dependencies depend on the application.

* * *

# 🔨 Maven Build

Maven can compile and package the application.

A common command is:

```bash
mvn clean install
```

Let's understand it.

### `clean`

Removes previously generated build files.

### `install`

Compiles, tests and packages the application and installs the generated artifact into the local Maven repository.

The final output is generally a JAR file:

```text
target/
    application.jar
```

This JAR file is what we ultimately need in the runtime Docker container.

* * *

# ⚙️ Application Properties

Spring Boot commonly stores configuration in:

```text
application.properties
```

For example:

```properties
spring.datasource.url=jdbc:mysql://db:3306/testdb
spring.datasource.username=root
spring.datasource.password=root

spring.jpa.hibernate.ddl-auto=update
```

Here:

```text
db
```

is the MySQL service name.

This is important.

Inside Docker Compose:

```text
Spring Boot Container
        |
        ↓
      db:3306
        |
        ↓
MySQL Container
```

We don't normally use:

```text
localhost
```

for the database hostname when the database is in another container.

* * *

# 🔐 Environment Variables

Hardcoding database credentials inside source code is not recommended.

Instead, Spring Boot properties can be overridden using environment variables.

For example:

```properties
spring.datasource.url
```

can be mapped to:

```text
SPRING_DATASOURCE_URL
```

Similarly:

```properties
spring.datasource.username
```

becomes:

```text
SPRING_DATASOURCE_USERNAME
```

and:

```properties
spring.datasource.password
```

becomes:

```text
SPRING_DATASOURCE_PASSWORD
```

The naming convention is:

```text
spring.datasource.url
        ↓
SPRING_DATASOURCE_URL
```

```text
spring.datasource.username
        ↓
SPRING_DATASOURCE_USERNAME
```

```text
spring.datasource.password
        ↓
SPRING_DATASOURCE_PASSWORD
```

This is a very useful Spring Boot + Docker concept.

* * *

# 🐳 Dockerfile

The Dockerfile describes how the Java application image is built.

Instead of creating a single huge image, this project uses a **multi-stage Docker build**.

The architecture is:

```text
Stage 1
Maven Builder
      ↓
Compile Application
      ↓
Create JAR
      ↓
Stage 2
Runtime Image
      ↓
Run JAR
```

This is an important Docker optimization technique.

* * *

# 🏗️ Why Use a Multi-Stage Dockerfile?

Suppose we use one image for everything:

```text
Java
+
Maven
+
Source Code
+
Build Tools
+
Dependencies
+
JAR
```

The final image may become unnecessarily large.

But the production container only needs:

```text
Java Runtime
+
Application JAR
```

Therefore, multi-stage builds separate:

```text
BUILD ENVIRONMENT
```

from:

```text
RUNTIME ENVIRONMENT
```

* * *

# 🔨 Docker Build Stage

The first stage uses a Maven image.

Conceptually:

```dockerfile
# Stage 1: Build JAR
FROM maven:3.9-eclipse-temurin-17-alpine AS builder
WORKDIR /app

COPY . .

# Build the executable jar (skipping unit tests)
RUN mvn clean package -DskipTests

# Stage 2: Run Application
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

COPY --from=builder /app/target/*.jar /app/expenseapp.jar

EXPOSE 8080

CMD ["java", "-jar", "expenseapp.jar"]
```

The builder stage:

1.  Starts with Maven
    
2.  Sets working directory
    
3.  Copies project files
    
4.  Downloads dependencies
    
5.  Compiles the application
    
6.  Runs the Maven build
    
7.  Produces the JAR file
    

The result may look like:

```text
target/
   └── application.jar
```

* * *

# 🚀 Docker Runtime Stage

The second stage uses a smaller Java runtime image.

Conceptually:

```dockerfile
FROM eclipse-temurin:...-jre

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
```

The important line is:

```dockerfile
COPY --from=builder
```

This means:

> Copy the required application artifact from the builder stage into the runtime stage.

The final image doesn't need:

```text
Maven
Source Code
Build Tools
```

It only needs the application runtime and JAR.

* * *

# 📦 Multi-Stage Build Flow

The complete process is:

```text
pom.xml
   |
   ↓
Maven Builder Container
   |
   ↓
mvn clean install
   |
   ↓
application.jar
   |
   ↓
Runtime Java Image
   |
   ↓
Java + application.jar
```

This produces a cleaner and more efficient final image.

* * *

# 🗄️ MySQL Database

MySQL runs in its own container.

For example:

```text
MySQL Container
      |
      ↓
Database
```

The Spring Boot application communicates with MySQL through the Docker network.

Example:

```text
Spring Boot
     |
     ↓
db:3306
     |
     ↓
MySQL
```

The default MySQL port is:

```text
3306
```

* * *

# 🔗 Docker Networking

Docker Compose creates a network for the services.

For example:

```text
┌───────────────────────────────────┐
│          Docker Network           │
│                                   │
│  ┌─────────────┐   ┌───────────┐ │
│  │ Spring Boot │──→│   MySQL   │ │
│  │    app      │   │    db     │ │
│  └─────────────┘   └───────────┘ │
│                                   │
└───────────────────────────────────┘
```

The application can connect using:

```text
db:3306
```

instead of using a hardcoded container IP.

Docker's internal DNS resolves the service name.

This is one of the biggest advantages of Compose networking.

* * *

# 💾 Docker Volumes

Database persistence is extremely important.

Without a volume:

```text
MySQL Container
       ↓
Database Data
```

If the container is removed, database data can be lost.

With a volume:

```text
MySQL Container
       ↓
Docker Volume
       ↓
Persistent Data
```

For example:

```yaml
volumes:
  mysql_data:
```

Then:

```yaml
services:

  db:
    volumes:
      - mysql_data:/var/lib/mysql
```

Now the lifecycle becomes:

```text
Container Deleted
       ↓
Volume Remains
       ↓
Database Data Remains
```

This is why Docker volumes are critical for stateful services such as databases.

* * *

# ⚙️ Docker Compose

Docker Compose is the central orchestration file.

Usually:

```text
docker-compose.yml
```

contains:

```yaml
services:

version: "3.8"

services:
  mysql_db:
    image: mysql:8.0
    container_name: mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: "Test@123"
      MYSQL_DATABASE: expenses_tracker
    ports:
      - "3306:3306"
    networks:
      - expense-app-nw
    healthcheck:
      test: ["CMD-SHELL", "mysqladmin ping -pTest@123 --silent"]
      interval: 5s
      timeout: 5s
      retries: 10
      start_period: 30s
    volumes:
      - mysql_data:/var/lib/mysql

  java_app:
    build:
      context: .
    container_name: expenseapp
    restart: always
    ports:
      - "8081:8080"
    environment:
      SPRING_DATASOURCE_URL: "jdbc:mysql://mysql_db:3306/expenses_tracker?allowPublicKeyRetrieval=true&useSSL=false"
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: "Test@123"
    depends_on:
      mysql_db:
        condition: service_healthy
    networks:
      - expense-app-nw

networks:
  expense-app-nw:
    driver: bridge

volumes:
  mysql_data:
```

Compose can define:

*   Services
    
*   Images
    
*   Builds
    
*   Ports
    
*   Environment variables
    
*   Networks
    
*   Volumes
    
*   Healthchecks
    
*   Dependencies
    
*   Restart policies
    

Instead of manually running multiple Docker commands, Compose lets us define the entire application architecture as code.

* * *

# 🧩 Example Docker Compose Structure

A simplified example:

```yaml
services:

  app:
    build: .
    container_name: java_app
    ports:
      - "8080:8080"

    environment:
      SPRING_DATASOURCE_URL: jdbc:mysql://db:3306/testdb
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: root

    depends_on:
      db:
        condition: service_healthy

    restart: always

  db:
    image: mysql:8
    container_name: mysql_db

    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: testdb

    volumes:
      - mysql_data:/var/lib/mysql

    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
      interval: 10s
      timeout: 5s
      retries: 5

    restart: always

volumes:
  mysql_data:
```

This is a simplified example. Adjust image versions, credentials, database names and application configuration according to your actual project.

* * *

# ❤️ Healthchecks

One of the most important parts of this project is the MySQL healthcheck.

Simply checking:

```text
Container = Running
```

does not necessarily mean:

```text
MySQL = Ready
```

MySQL may take some time to initialize.

Without a healthcheck:

```text
MySQL Container Starts
        ↓
Spring Boot Starts
        ↓
Spring Boot Connects
        ↓
MySQL Not Ready
        ↓
Connection Failure
```

With a healthcheck:

```text
MySQL Starts
    ↓
Healthcheck
    ↓
MySQL Ready?
    ↓
YES
    ↓
Spring Boot Starts
```

* * *

# 🩺 MySQL Healthcheck

A common healthcheck is:

```yaml
healthcheck:
  test: ["CMD", "mysqladmin", "ping", "-h", "localhost"]
  interval: 10s
  timeout: 5s
  retries: 5
```

The command:

```bash
mysqladmin ping
```

checks whether MySQL is responding.

* * *

# 🔄 depends\_on with Healthcheck

Docker Compose can use the health status:

```yaml
depends_on:
  db:
    condition: service_healthy
```

This tells Compose:

> Start the application after the database service reports a healthy status.

This is better than relying only on container startup order.

* * *

# 🔁 Restart Policies

A container may stop because of:

*   Application crash
    
*   Temporary failure
    
*   Server issue
    
*   Unexpected error
    

A restart policy can automatically restart it.

For example:

```yaml
restart: always
```

This means Docker should restart the container when appropriate.

Restart policies improve application resilience.

However, restart policies are not a replacement for proper monitoring and troubleshooting.

* * *

# 💻 Complete Setup

Let's now deploy the application.

* * *

# 1️⃣ Install Docker

First install Docker Desktop or Docker Engine depending on your operating system.

Verify:

```bash
docker --version
```

Then:

```bash
docker compose version
```

* * *

# 2️⃣ Clone the Repository

Clone the project:

```bash
git clone https://github.com/hritikranjan1/Expenses-Tracker-WebApp.git
```

Move into the project:

```bash
cd Expenses-Tracker-WebApp
```

* * *

# 3️⃣ Check Project Files

Verify:

```text
pom.xml
Dockerfile
docker-compose.yml
src/
```

For example:

```bash
ls
```

On Windows:

```powershell
dir
```

* * *

# 4️⃣ Configure Database Properties

Configure Spring Boot to use the MySQL service.

For example:

```properties
spring.datasource.url=jdbc:mysql://db:3306/testdb
spring.datasource.username=root
spring.datasource.password=root
```

Or provide these through environment variables.

* * *

# 5️⃣ Build and Start Containers

Run:

```bash
docker compose up -d --build
```

This command:

```text
Reads docker-compose.yml
        ↓
Builds Spring Boot image
        ↓
Pulls MySQL image
        ↓
Creates network
        ↓
Creates volume
        ↓
Creates containers
        ↓
Starts MySQL
        ↓
Runs healthcheck
        ↓
Starts Spring Boot
```

* * *

# 🔍 Check Running Containers

Run:

```bash
docker compose ps
```

or:

```bash
docker ps
```

You should see something similar to:

```text
NAME        STATUS
java_app    Up
mysql_db    Up (healthy)
```

The important thing is that MySQL should eventually show:

```text
healthy
```

* * *

# 🌍 Access the Application

If Spring Boot exposes port 8080:

```text
http://localhost:8080
```

Open it in your browser.

The request flow becomes:

```text
Browser
   ↓
localhost:8080
   ↓
Spring Boot Container
   ↓
MySQL Container
```

* * *

# 📜 Check Application Logs

To see Spring Boot logs:

```bash
docker logs java_app
```

Follow logs:

```bash
docker logs -f java_app
```

You may see Spring Boot startup information.

Look for messages indicating that the application has successfully started.

* * *

# 🗄️ Check MySQL Logs

Run:

```bash
docker logs mysql_db
```

Follow:

```bash
docker logs -f mysql_db
```

Look for messages indicating MySQL is ready to accept connections.

* * *

# 🔌 Connect to MySQL

You can enter the MySQL container:

```bash
docker exec -it mysql_db mysql -uroot -p
```

Enter the configured password.

Then:

```sql
SHOW DATABASES;
```

Select the application database:

```sql
USE testdb;
```

Check tables:

```sql
SHOW TABLES;
```

Exit:

```sql
exit;
```

* * *

# 🧪 Test the Application

Testing should happen at multiple levels.

## Test 1 — Container

```bash
docker ps
```

## Test 2 — MySQL

```bash
docker exec -it mysql_db mysqladmin ping -uroot -p
```

## Test 3 — Spring Boot

Open:

```text
http://localhost:8080
```

## Test 4 — Logs

```bash
docker logs java_app
```

This gives a structured way to verify the deployment.

* * *

# 🧰 Useful Docker Commands

## Build image

```bash
docker compose build
```

## Start containers

```bash
docker compose up -d
```

## Build and start

```bash
docker compose up -d --build
```

## Stop containers

```bash
docker compose stop
```

## Stop and remove containers

```bash
docker compose down
```

## Remove containers and volumes

```bash
docker compose down -v
```

⚠️ Be careful with:

```bash
docker compose down -v
```

because it can remove the MySQL volume and therefore the persistent database data.

* * *

# 📦 Image Commands

List Docker images:

```bash
docker images
```

Remove an image:

```bash
docker rmi <image-name>
```

Build manually:

```bash
docker build -t springboot-app .
```

Run manually:

```bash
docker run -p 8080:8080 springboot-app
```

For this project, Docker Compose is preferred because we have multiple services.

* * *

# 🔎 Container Inspection

Inspect the application container:

```bash
docker inspect java_app
```

Inspect MySQL:

```bash
docker inspect mysql_db
```

This can help investigate:

*   Network
    
*   Volumes
    
*   Environment
    
*   Container configuration
    
*   IP addresses
    
*   Mounts
    

* * *

# 🌐 Check Docker Network

List networks:

```bash
docker network ls
```

Inspect a network:

```bash
docker network inspect <network-name>
```

This can show which containers are connected.

For example:

```text
java_app
   |
   +------ Docker Network ------+
                              |
                              ↓
                           mysql_db
```

* * *

# 💾 Check Docker Volumes

List volumes:

```bash
docker volume ls
```

Inspect a volume:

```bash
docker volume inspect <volume-name>
```

The volume is responsible for keeping MySQL data persistent.

* * *

# 🐞 Troubleshooting

Troubleshooting is an important DevOps skill.

When the application doesn't work, don't immediately rebuild everything.

Follow a structured process.

* * *

# ❌ Problem 1: Spring Boot Cannot Connect to MySQL

Possible error:

```text
Communications link failure
```

or:

```text
Connection refused
```

Check MySQL:

```bash
docker compose ps
```

Then:

```bash
docker logs mysql_db
```

Make sure MySQL is healthy.

Also verify:

```text
Database hostname
Database port
Database name
Username
Password
```

* * *

# ❌ Problem 2: Using localhost for MySQL

A common mistake is:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/testdb
```

If MySQL is in another container, this may not work as expected.

Instead use the Compose service name:

```properties
spring.datasource.url=jdbc:mysql://db:3306/testdb
```

The concept is:

```text
Spring Boot Container
       |
       ↓
       db:3306
       |
       ↓
MySQL Container
```

* * *

# ❌ Problem 3: MySQL Is Running But Application Still Fails

Check:

```bash
docker compose ps
```

A running container does not always mean the service is ready.

Check health:

```bash
docker inspect mysql_db
```

Check logs:

```bash
docker logs mysql_db
```

This is where healthchecks become useful.

* * *

# ❌ Problem 4: Port 8080 Already in Use

You may see:

```text
Bind for 0.0.0.0:8080 failed
```

This means another application is using port 8080.

You can change:

```yaml
ports:
  - "8081:8080"
```

Now access:

```text
http://localhost:8081
```

The important distinction is:

```text
Host Port : Container Port
```

So:

```text
8081:8080
```

means:

```text
Host → 8081
Container → 8080
```

* * *

# ❌ Problem 5: Docker Build Fails

Check:

```bash
docker compose build
```

Look carefully at the error.

Common causes:

*   Incorrect Maven dependency
    
*   Network issue while downloading dependencies
    
*   Incorrect Java version
    
*   Invalid Dockerfile
    
*   Incorrect source path
    
*   Build failure in Maven
    

You can test Maven locally:

```bash
mvn clean install
```

If the Maven build fails outside Docker, fix the application first.

* * *

# ❌ Problem 6: Container Keeps Restarting

Check:

```bash
docker ps -a
```

Then:

```bash
docker logs java_app
```

The logs usually provide the actual reason.

Possible causes:

```text
Application crash
Database connection failure
Configuration error
Missing environment variable
Incorrect Java version
Incorrect JAR path
```

* * *

# ❌ Problem 7: Database Data Disappears

Check whether a volume is configured:

```bash
docker volume ls
```

If MySQL is running without persistent storage, removing the container may remove the database data.

Use:

```yaml
volumes:
  - mysql_data:/var/lib/mysql
```

and define:

```yaml
volumes:
  mysql_data:
```

* * *

# 🔐 Security Best Practices

For learning, you may see configurations such as:

```text
root
root
```

But this should not be used in production.

Production systems should follow stronger security practices.

### 1\. Don't use root for the application

Create a dedicated MySQL user.

### 2\. Use strong passwords

Never use simple credentials in production.

### 3\. Don't commit secrets

Never push:

```text
.env
```

or credentials into GitHub.

### 4\. Use secrets management

Use a proper secret-management system in production.

### 5\. Keep database private

Don't expose MySQL publicly unless there is a specific requirement.

### 6\. Use HTTPS

Production web applications should use TLS.

### 7\. Scan Docker images

Use image scanning tools to identify vulnerabilities.

### 8\. Keep dependencies updated

Regularly update:

```text
Java
Spring Boot
Maven dependencies
MySQL
Docker base images
```

### 9\. Use non-root containers

Where practical, run applications using a non-root user.

* * *

# 🏭 Why Multi-Stage Builds Matter

Multi-stage builds are one of the most useful Docker optimization techniques for compiled applications such as Java applications.

Without multi-stage builds:

```text
Final Image
|
+-- Maven
+-- JDK
+-- Source Code
+-- Build Dependencies
+-- JAR
```

With multi-stage builds:

```text
Builder Image
|
+-- Maven
+-- JDK
+-- Source
+-- Dependencies
|
↓
JAR
|
↓
Runtime Image
|
+-- JRE
+-- JAR
```

Benefits:

*   Smaller final image
    
*   Faster deployment
    
*   Less unnecessary software
    
*   Reduced attack surface
    
*   Cleaner production containers
    

This is one of the major reasons to use multi-stage Docker builds for Java applications.

* * *

# 🎯 DevOps Concepts Demonstrated

This project demonstrates several important DevOps concepts.

## 🐳 Containerization

```text
Java Application
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
Spring Boot + MySQL
```

* * *

## 🔗 Networking

```text
Spring Boot
      ↓
Docker Network
      ↓
MySQL
```

* * *

## 💾 Persistent Storage

```text
MySQL
  ↓
Docker Volume
  ↓
Persistent Data
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
Spring Boot
```

* * *

## 🔐 Configuration Management

```text
Environment Variables
        ↓
Docker Compose
        ↓
Spring Boot
```

* * *

## 🏗️ Build Optimization

```text
Maven Builder
      ↓
JAR
      ↓
Lightweight Runtime Image
```

* * *

# 🧠 Complete Deployment Flow

The entire project can be represented as:

```text
                Developer
                    |
                    ↓
               Source Code
                    |
                    ↓
             Dockerfile
                    |
                    ↓
          Multi-Stage Build
                    |
           ┌────────┴────────┐
           ↓                 ↓
      Maven Builder      Runtime Image
           |                 |
           ↓                 ↓
      application.jar    Java Runtime
                             |
                             ↓
                     Spring Boot App
                             |
                             ↓
                       Docker Network
                             |
                             ↓
                          MySQL
                             |
                             ↓
                      Docker Volume
```

Docker Compose manages the runtime architecture.

* * *

# 💼 How to Explain This Project in an Interview

If an interviewer asks:

> **"Explain your Docker project."**

You can answer:

> "I deployed a three-tier Java Spring Boot application using Docker and Docker Compose. The application uses Spring Boot for the backend, Maven for dependency management and building the application, and MySQL for persistent data storage. I created a multi-stage Dockerfile where the first stage uses Maven to build the application and generate the JAR file, while the second stage uses a lightweight Java runtime image to run only the required JAR. Docker Compose manages the application and database services, networking, environment variables, healthchecks, restart policies, and persistent volumes. The Spring Boot application connects to MySQL through the Docker network using the database service name rather than localhost. I also configured a MySQL healthcheck so the application doesn't attempt to connect before the database is ready."

This answer demonstrates that you understand both Docker commands and the underlying architecture.

* * *

# ❓ Interview Questions

## 1\. Why did you use Docker Compose?

Because the project contains multiple services.

Docker Compose provides a simple way to define and manage those services together.

* * *

## 2\. Why did you use a multi-stage Dockerfile?

To separate the build environment from the runtime environment and keep the final image smaller and cleaner.

* * *

## 3\. What is the purpose of the Maven stage?

The Maven stage compiles the Java source code, downloads dependencies, runs the build and generates the JAR file.

* * *

## 4\. Why don't you copy the complete source code into the runtime image?

The runtime container only needs the generated application artifact and Java runtime.

Keeping build tools and source code out of the runtime image reduces image size and attack surface.

* * *

## 5\. Why does Spring Boot connect to `db` instead of `localhost`?

Because MySQL is running in a separate container.

Docker Compose provides service-name-based DNS, so the application can connect to:

```text
db:3306
```

* * *

## 6\. Why is a healthcheck needed?

Because MySQL may take time to become ready after its container starts.

The healthcheck lets Compose determine whether the database is actually ready.

* * *

## 7\. Why use a Docker volume?

Because MySQL is stateful.

The volume keeps database data persistent even if the MySQL container is recreated.

* * *

## 8\. What does `restart: always` do?

It tells Docker to restart the container when it stops according to the restart policy.

* * *

## 9\. What is the purpose of `pom.xml`?

It defines the Maven project configuration, dependencies, plugins and build information.

* * *

## 10\. How can Spring Boot properties be passed through Docker?

Using environment variables.

For example:

```text
spring.datasource.url
```

can be represented as:

```text
SPRING_DATASOURCE_URL
```

* * *

# 🚀 Future Improvements

This project can be extended into a complete production-style DevOps project.

## 1\. Add Nginx

Architecture:

```text
User
 ↓
Nginx
 ↓
Spring Boot
 ↓
MySQL
```

* * *

## 2\. Add HTTPS

Configure SSL/TLS for secure communication.

* * *

## 3\. Add CI/CD

For example:

```text
GitHub
   ↓
GitHub Actions
   ↓
Maven Tests
   ↓
Docker Build
   ↓
Security Scan
   ↓
Docker Registry
   ↓
Deployment
```

* * *

## 4\. Push Image to Docker Hub

Build:

```bash
docker build -t username/springboot-app .
```

Login:

```bash
docker login
```

Push:

```bash
docker push username/springboot-app
```

* * *

## 5\. Deploy on AWS

The application can be deployed using:

```text
AWS EC2
```

or container services such as:

```text
Amazon ECS
```

* * *

## 6\. Add Monitoring

Use:

```text
Prometheus
+
Grafana
```

to monitor:

*   CPU
    
*   Memory
    
*   Application metrics
    
*   Request count
    
*   Response time
    

* * *

## 7\. Add Centralized Logging

Production environments can use centralized logging solutions to collect logs from containers.

* * *

## 8\. Move to Kubernetes

The Docker Compose architecture can be converted into Kubernetes resources:

```text
Docker Compose
      ↓
Kubernetes
      ↓
Deployment
      ↓
Service
      ↓
ConfigMap
      ↓
Secret
      ↓
PersistentVolume
```

This would be the next step toward a more advanced cloud-native deployment.

* * *

# 📚 What I Learned From This Project

This project helped me understand that Docker is not simply:

```bash
docker build
docker run
```

A real application requires:

```text
Application
    +
Database
    +
Networking
    +
Storage
    +
Configuration
    +
Healthchecks
    +
Security
    +
Build Optimization
```

The most important concepts I practiced were:

*   Docker containerization
    
*   Docker images
    
*   Docker Compose
    
*   Spring Boot containerization
    
*   Maven builds
    
*   Multi-stage Dockerfiles
    
*   Docker networking
    
*   MySQL containers
    
*   Docker volumes
    
*   Healthchecks
    
*   Environment variables
    
*   Restart policies
    
*   Container logs
    
*   Container troubleshooting
    
*   Database persistence
    

* * *

# 🏆 Why This Is a Good DevOps Portfolio Project

A basic Docker project might only demonstrate:

```bash
docker build
docker run
```

But this project demonstrates much more:

```text
☕ Spring Boot
       +
📦 Maven
       +
🐳 Docker
       +
⚙️ Docker Compose
       +
🗄️ MySQL
       +
🔗 Networking
       +
💾 Volumes
       +
❤️ Healthchecks
       +
🔐 Environment Variables
       +
🏗️ Multi-Stage Builds
```

This makes it a strong beginner-to-intermediate DevOps portfolio project.

Instead of telling an interviewer:

> "I know Docker."

you can explain a complete architecture and the problems you solved.

* * *

# 📋 Final Architecture

```text
                         USER
                           |
                           ↓
                  ┌─────────────────┐
                  │  Spring Boot    │
                  │     App         │
                  │                 │
                  │ Java + Maven    │
                  └────────┬────────┘
                           |
                           | Docker Network
                           |
                           ↓
                  ┌─────────────────┐
                  │      MySQL      │
                  │    Database     │
                  └────────┬────────┘
                           |
                           ↓
                  ┌─────────────────┐
                  │ Docker Volume   │
                  │ Persistent Data │
                  └─────────────────┘
```

Docker Compose manages the complete stack.

* * *

# 🎯 Final Checklist

Before considering the project complete:

```text
[✓] Java application created
[✓] Maven dependencies configured
[✓] pom.xml configured
[✓] Spring Boot properties configured
[✓] Dockerfile created
[✓] Multi-stage Docker build configured
[✓] MySQL service configured
[✓] Docker network configured
[✓] Environment variables configured
[✓] Docker volume configured
[✓] MySQL healthcheck configured
[✓] Restart policy configured
[✓] Docker Compose configured
[✓] Application image built
[✓] Containers started
[✓] MySQL verified
[✓] Application tested
[✓] Logs checked
```

* * *

# 🎥 Reference Tutorial

This project was learned and implemented as part of a Docker/DevOps learning series.

The relevant section starts around:

**03:51:00**

YouTube:

https://youtu.be/9bSbNNH4Nqw?t=13860

* * *

# 📝 Conclusion

This project gave me practical experience with deploying a **Java Spring Boot application using Docker and Docker Compose**.

The final environment contains:

```text
Spring Boot
     ↓
Docker Container
     ↓
Docker Network
     ↓
MySQL Container
     ↓
Docker Volume
```

The most valuable part was understanding how all these components work together.

I learned that containerization is not just about packaging an application.

A production-oriented containerized application also needs:

*   Reliable networking
    
*   Persistent storage
    
*   Proper configuration
    
*   Database readiness
    
*   Healthchecks
    
*   Restart policies
    
*   Optimized images
    
*   Security practices
    
*   Troubleshooting strategies
    

The multi-stage Docker build was particularly useful because it separates the Maven build environment from the runtime environment and helps keep the final image lightweight.

The next logical steps for this project are:

```text
Docker
   ↓
CI/CD
   ↓
AWS
   ↓
Monitoring
   ↓
Kubernetes
```

For anyone learning DevOps, I highly recommend building projects like this.

Don't just learn Docker commands.

**Build something. Break it. Troubleshoot it. Automate it. Deploy it.**

That's where real DevOps learning begins. 🚀

* * *

# 🔗 Connect With Me

💼 LinkedIn: https://www.linkedin.com/in/hritikranjan1/

🌐 Website: https://hritikranjan.in

📝 DevOps Blogs: https://blogs.hritikranjan.in

💻 GitHub: https://github.com/hritikranjan1

* * *

⭐ If you found this project useful, consider giving the repository a Star!

🚀 **Built with Java • Spring Boot • Maven • Docker • Docker Compose • MySQL**

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