---
title: "🐳 All Docker Commands Explained with Examples (2026 Complete Reference)"
seoTitle: "Docker Commands Cheat Sheet: Complete Guide with Examples"
seoDescription: "Learn essential Docker commands with examples for containers, images, volumes, networks, Docker Compose, cleanup, debugging, and more."
datePublished: 2026-08-27T04:53:19.968Z
cuid: cmtb1rquc00000ai19wq21u85
slug: docker-commands-cheat-sheet
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/24bb2900-39ab-4e00-8ca2-3aad51856e26.png
tags: docker, devops, dockerfile, docker-compose, docker-images, docker-cli, devops-articles, docker-network, devops-journey, docker-volume

---

Docker is one of the most important technologies for modern software development, DevOps, cloud engineering, and CI/CD.

If you are learning **DevOps, AWS, Kubernetes, CI/CD, or cloud computing**, Docker is one of the tools you should become comfortable with.

But when beginners start learning Docker, one problem appears again and again:

> **There are so many Docker commands. Which command should I use, and when?**

This guide is designed to solve that problem.

Instead of simply giving you a list of commands, we will understand:

*   What each Docker command does
    
*   Why we use it
    
*   When we should use it
    
*   Command syntax
    
*   Real-world examples
    
*   Important options
    
*   Common mistakes
    
*   Beginner tips
    
*   Docker Compose commands
    
*   Docker networking
    
*   Docker volumes
    
*   Docker image management
    
*   Docker registry commands
    
*   Docker Buildx
    
*   Docker Swarm
    
*   Troubleshooting commands
    
*   A final Docker cheat sheet
    

By the end of this article, you should be able to use the Docker CLI confidently in your development and DevOps projects.

* * *

# 📌 Table of Contents

1.  [What Is Docker?](#-what-is-docker)
    
2.  [Docker Architecture in Simple Words](#-docker-architecture-in-simple-words)
    
3.  [Docker Command Syntax](#-docker-command-syntax)
    
4.  [Check Docker Installation](#-1-check-docker-installation)
    
5.  [Docker Container Commands](#-2-docker-container-commands)
    
6.  [Docker Image Commands](#-3-docker-image-commands)
    
7.  [Docker Registry Commands](#-4-docker-registry-commands)
    
8.  [Docker Logs and Debugging](#-5-docker-logs-and-debugging)
    
9.  [Docker Volume Commands](#-6-docker-volume-commands)
    
10.  [Docker Network Commands](#-7-docker-network-commands)
     
11.  [Docker Container Interaction](#-8-interact-with-a-running-container)
     
12.  [Docker File Copy Commands](#-9-copy-files-between-host-and-container)
     
13.  [Docker Cleanup Commands](#-10-docker-cleanup-commands)
     
14.  [Docker Commit, Export and Import](#-11-docker-commit-export-and-import)
     
15.  [Docker Compose Commands](#-12-docker-compose-commands)
     
16.  [Docker Compose Example Project](#-13-real-world-docker-compose-example)
     
17.  [Docker Context Commands](#-14-docker-context-commands)
     
18.  [Docker Buildx Commands](#-15-docker-buildx-commands)
     
19.  [Docker Manifest Commands](#-16-docker-manifest-commands)
     
20.  [Docker Swarm Commands](#-17-docker-swarm-commands)
     
21.  [Docker Plugin Commands](#-18-docker-plugin-commands)
     
22.  [Useful Docker Filters](#-19-useful-docker-filters)
     
23.  [Useful Docker Formatting Commands](#-20-useful-docker-formatting-commands)
     
24.  [Common Docker Errors](#-21-common-docker-errors)
     
25.  [Docker Commands Beginners Should Memorize](#-22-docker-commands-beginners-should-memorize)
     
26.  [Docker Cheat Sheet](#-23-docker-cheat-sheet)
     
27.  [Docker Learning Roadmap](#-24-docker-learning-roadmap)
     
28.  [Conclusion](#-conclusion)
     

* * *

# 🐳 What Is Docker?

Docker is a platform used to **build, package, distribute, and run applications inside containers**.

A container packages an application together with the dependencies it needs to run.

For example, imagine your application requires:

```text
Application
    +
Python
    +
Required Libraries
    +
Environment Variables
    +
System Dependencies
```

Docker allows you to package these requirements into an image and run that image as a container.

A simple way to remember the relationship is:

```text
Dockerfile
     ↓
Docker Image
     ↓
Docker Container
```

### Dockerfile

A Dockerfile contains instructions for creating an image.

### Docker Image

An image is a reusable package/template containing the application and its required environment.

### Docker Container

A container is a running instance of an image.

* * *

# 🏗️ Docker Architecture in Simple Words

A simplified Docker architecture looks like this:

```text
                Docker CLI
                    |
                    ↓
              Docker Engine
                    |
          ---------------------
          |         |         |
       Images   Containers  Networks
                    |
                 Volumes
```

When you run:

```bash
docker run nginx
```

Docker approximately performs this flow:

```text
Docker CLI
   ↓
Check local image
   ↓
Image not available?
   ↓
Pull image from registry
   ↓
Create container
   ↓
Start container
```

The Docker documentation describes `docker run` as creating and running a new container from an image; if the image is unavailable locally, Docker can pull it first.

* * *

# 💻 Docker Command Syntax

Most Docker commands follow this pattern:

```bash
docker <command> <options> <arguments>
```

For example:

```bash
docker run -d -p 8080:80 nginx
```

Here:

```text
docker       → Docker CLI
run          → command
-d           → run in detached mode
-p            → publish a port
8080:80      → host:container port
nginx        → image
```

You can get help for almost any Docker command using:

```bash
docker --help
```

Or:

```bash
docker run --help
```

Docker officially supports the `--help` option for displaying command-specific help.

* * *

# 1️⃣ Check Docker Installation

Before learning Docker commands, verify that Docker is installed.

## Check Docker Version

```bash
docker --version
```

Example:

```text
Docker version 28.x.x, build xxxxx
```

This tells you the installed Docker CLI version.

* * *

## Detailed Docker Version

```bash
docker version
```

This can show information about both the Docker client and server/engine.

Use it when troubleshooting version compatibility.

* * *

## Docker System Information

```bash
docker info
```

This provides information about the Docker environment.

It can include:

*   Containers
    
*   Images
    
*   Storage driver
    
*   Docker root directory
    
*   CPUs
    
*   Memory
    
*   Plugins
    
*   Server information
    

Useful when troubleshooting Docker.

* * *

## Docker Help

```bash
docker --help
```

For a specific command:

```bash
docker run --help
```

* * *

# 2️⃣ Docker Container Commands

Containers are where your applications actually run.

Let's learn the most important container commands.

* * *

# `docker run`

The most important Docker command for beginners.

```bash
docker run nginx
```

It creates and starts a new container from the `nginx` image.

If the image isn't available locally, Docker can pull it from a registry.

* * *

## Run in Background

```bash
docker run -d nginx
```

`-d` means:

```text
Detached mode
```

The container runs in the background.

* * *

## Give the Container a Name

```bash
docker run --name my-nginx -d nginx
```

Now instead of using a random container name, you can use:

```bash
docker stop my-nginx
```

Docker supports custom container names through the `--name` option.

* * *

## Map a Port

```bash
docker run -d -p 8080:80 nginx
```

The format is:

```text
-p HOST_PORT:CONTAINER_PORT
```

So:

```text
8080 → Your computer
80   → Container
```

You can then access:

```text
http://localhost:8080
```

* * *

## Run an Interactive Ubuntu Container

```bash
docker run -it ubuntu /bin/bash
```

Meaning:

```text
-i → interactive
-t → terminal
```

Now you can work inside the Ubuntu container.

* * *

## Run a Specific Image Version

```bash
docker run nginx:1.27
```

Here:

```text
nginx → image
1.27  → tag
```

Avoid blindly relying on `latest` in production deployments when reproducibility matters.

* * *

# `docker create`

Creates a container but does not start it.

```bash
docker create --name mycontainer nginx
```

Then start it:

```bash
docker start mycontainer
```

Think:

```text
docker create → Create
docker start  → Start
```

While:

```text
docker run → Create + Start
```

* * *

# `docker start`

Starts an existing stopped container.

```bash
docker start mycontainer
```

Important:

```text
docker run
```

creates a new container.

```text
docker start
```

starts an existing container.

* * *

# `docker stop`

Stops a running container gracefully.

```bash
docker stop mycontainer
```

Example:

```bash
docker stop nginx-container
```

Use this when you want to shut down an application cleanly.

* * *

# `docker restart`

Restarts a container.

```bash
docker restart mycontainer
```

Useful when a service needs to be restarted after a configuration change or temporary problem.

* * *

# `docker pause`

Pauses all processes inside a container.

```bash
docker pause mycontainer
```

* * *

# `docker unpause`

Resumes a paused container.

```bash
docker unpause mycontainer
```

* * *

# `docker kill`

Forcefully stops a running container.

```bash
docker kill mycontainer
```

Use `docker stop` for normal shutdowns.

Use `docker kill` when the container is stuck or doesn't respond properly.

* * *

# `docker rm`

Removes a container.

```bash
docker rm mycontainer
```

If the container is still running, Docker normally requires you to stop it first.

You can force removal:

```bash
docker rm -f mycontainer
```

⚠️ Be careful with `-f`.

* * *

# `docker rename`

Renames a container.

```bash
docker rename old-name new-name
```

Example:

```bash
docker rename nginx-container web-server
```

* * *

# `docker wait`

Waits until a container stops and then prints its exit code.

```bash
docker wait mycontainer
```

Useful in automation and scripts.

* * *

# `docker container prune`

Removes all stopped containers.

```bash
docker container prune
```

Docker asks for confirmation before deleting them.

* * *

# 3️⃣ Docker Image Commands

An image is a package/template used to create containers.

Think:

```text
Image
  ↓
Container
```

One image can be used to create many containers.

* * *

# `docker pull`

Downloads an image from a registry.

```bash
docker pull nginx
```

Specific version:

```bash
docker pull nginx:1.27
```

Ubuntu:

```bash
docker pull ubuntu:24.04
```

* * *

# `docker images`

Lists locally available images.

```bash
docker images
```

Example output:

```text
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    abc123         2 days ago    190MB
ubuntu       24.04     xyz456         3 days ago    78MB
```

* * *

# `docker image ls`

Modern object-oriented form of listing images:

```bash
docker image ls
```

It is equivalent to:

```bash
docker images
```

* * *

# `docker build`

Builds an image from a Dockerfile.

Suppose your project contains:

```text
myapp/
├── Dockerfile
└── app.py
```

Build the image:

```bash
docker build -t myapp:1.0 .
```

Meaning:

```text
-t myapp:1.0 → image name and tag
.            → current directory
```

* * *

# Example Dockerfile

```dockerfile
FROM python:3.12-slim

WORKDIR /app

COPY app.py .

CMD ["python", "app.py"]
```

Build:

```bash
docker build -t python-app:1.0 .
```

Run:

```bash
docker run python-app:1.0
```

* * *

# `docker rmi`

Removes an image.

```bash
docker rmi nginx
```

Or:

```bash
docker rmi nginx:latest
```

Force removal:

```bash
docker rmi -f nginx
```

Be careful because removing an image can affect containers that depend on it.

* * *

# `docker image rm`

Equivalent object-oriented form:

```bash
docker image rm nginx
```

* * *

# `docker tag`

Creates another tag/reference for an image.

```bash
docker tag myapp:latest username/myapp:v1
```

This is commonly used before pushing an image to Docker Hub or another registry.

* * *

# `docker history`

Shows the layers used to create an image.

```bash
docker history nginx
```

This can help you understand image construction and investigate image size.

* * *

# `docker inspect`

Displays detailed information about Docker objects.

For an image:

```bash
docker image inspect nginx
```

For a container:

```bash
docker inspect mycontainer
```

The output is usually JSON.

It can contain information such as:

*   Environment variables
    
*   Network configuration
    
*   Mounts
    
*   IP addresses
    
*   Image configuration
    
*   Container state
    

* * *

# `docker save`

Saves an image to a tar archive.

```bash
docker save -o myimage.tar myapp:latest
```

Useful when you need to transfer an image without directly pulling it from a registry.

* * *

# `docker load`

Loads an image from a tar archive.

```bash
docker load -i myimage.tar
```

Typical workflow:

```text
Machine A
   ↓
docker save
   ↓
myimage.tar
   ↓
Transfer file
   ↓
Machine B
   ↓
docker load
```

* * *

# 4️⃣ Docker Registry Commands

A registry stores Docker images.

Examples include:

*   Docker Hub
    
*   Amazon ECR
    
*   GitHub Container Registry
    
*   Google Artifact Registry
    
*   Azure Container Registry
    
*   Private registries
    

* * *

# `docker login`

Log in to a container registry.

```bash
docker login
```

For a specific registry:

```bash
docker login registry.example.com
```

* * *

# `docker logout`

Log out from a registry.

```bash
docker logout
```

* * *

# `docker search`

Search Docker Hub for images.

```bash
docker search nginx
```

You can use it to discover available images.

Always verify image ownership and trust before using third-party images.

* * *

# `docker push`

Push an image to a registry.

First tag your image:

```bash
docker tag myapp:latest username/myapp:latest
```

Then:

```bash
docker push username/myapp:latest
```

Typical workflow:

```text
Build
  ↓
Tag
  ↓
Login
  ↓
Push
  ↓
Registry
```

* * *

# 5️⃣ Docker Logs and Debugging

Debugging is one of the most important Docker skills.

* * *

# `docker ps`

Shows running containers.

```bash
docker ps
```

* * *

# `docker ps -a`

Shows all containers, including stopped containers.

```bash
docker ps -a
```

This is one of the first commands you should use when a container isn't behaving as expected.

* * *

# `docker logs`

View container logs.

```bash
docker logs mycontainer
```

* * *

## Follow Logs

```bash
docker logs -f mycontainer
```

`-f` means follow.

It behaves similarly to:

```bash
tail -f
```

* * *

## Show Last 100 Lines

```bash
docker logs --tail 100 mycontainer
```

* * *

## Show Logs with Timestamps

```bash
docker logs -t mycontainer
```

* * *

# `docker top`

Shows processes running inside a container.

```bash
docker top mycontainer
```

Useful for checking whether the expected application process is running.

* * *

# `docker stats`

Displays live resource usage.

```bash
docker stats
```

It can show:

```text
CPU %
Memory Usage
Memory %
Network I/O
Block I/O
PIDs
```

For a specific container:

```bash
docker stats mycontainer
```

* * *

# `docker port`

Shows port mappings.

```bash
docker port mycontainer
```

Example:

```text
80/tcp -> 0.0.0.0:8080
```

This means container port 80 is exposed through host port 8080.

* * *

# `docker diff`

Shows filesystem changes made inside a container.

```bash
docker diff mycontainer
```

Useful when troubleshooting unexpected file changes.

* * *

# `docker events`

Shows real-time Docker events.

```bash
docker events
```

You may see events such as:

```text
container create
container start
container stop
network connect
image pull
```

Useful for troubleshooting and automation.

* * *

# `docker inspect`

One of the most powerful debugging commands.

```bash
docker inspect mycontainer
```

For example, to find the container IP:

```bash
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' mycontainer
```

* * *

# `docker system df`

Shows Docker disk usage.

```bash
docker system df
```

This helps identify whether images, containers, volumes, or build cache are consuming disk space.

* * *

# 6️⃣ Docker Volume Commands

Containers are designed to be replaceable.

But application data often needs to survive container deletion.

This is where **volumes** are useful.

```text
Container
    |
    ↓
Volume
    |
    ↓
Persistent Data
```

* * *

# `docker volume create`

Create a volume:

```bash
docker volume create my_volume
```

* * *

# `docker volume ls`

List volumes:

```bash
docker volume ls
```

* * *

# `docker volume inspect`

Inspect a volume:

```bash
docker volume inspect my_volume
```

* * *

# Use a Volume with a Container

```bash
docker run -d \
  --name mysql \
  -v mysql_data:/var/lib/mysql \
  mysql
```

Here:

```text
mysql_data              → Docker volume
/var/lib/mysql          → Path inside container
```

If the container is removed, the named volume can remain.

* * *

# `docker volume rm`

Remove a volume:

```bash
docker volume rm my_volume
```

⚠️ Removing a volume can permanently delete stored data.

* * *

# `docker volume prune`

Remove unused volumes:

```bash
docker volume prune
```

Use this carefully.

* * *

# 7️⃣ Docker Network Commands

Containers often need to communicate with:

*   Other containers
    
*   The host
    
*   External services
    
*   Databases
    
*   APIs
    

Docker networking makes this possible.

* * *

# `docker network ls`

List networks:

```bash
docker network ls
```

Typical default networks include:

```text
bridge
host
none
```

* * *

# `docker network create`

Create a custom network:

```bash
docker network create my_network
```

* * *

# Run Container on a Network

```bash
docker run -d \
  --name web \
  --network my_network \
  nginx
```

* * *

# `docker network inspect`

Inspect a network:

```bash
docker network inspect my_network
```

This can show connected containers and network configuration.

* * *

# `docker network connect`

Connect an existing container to a network:

```bash
docker network connect my_network mycontainer
```

* * *

# `docker network disconnect`

Disconnect:

```bash
docker network disconnect my_network mycontainer
```

* * *

# `docker network rm`

Remove a network:

```bash
docker network rm my_network
```

* * *

# `docker network prune`

Remove unused networks:

```bash
docker network prune
```

* * *

# 🧠 Container-to-Container Communication Example

Create a network:

```bash
docker network create app-network
```

Run Redis:

```bash
docker run -d \
  --name redis \
  --network app-network \
  redis
```

Run another container:

```bash
docker run -it \
  --network app-network \
  busybox
```

Inside the second container, `redis` can be used as the hostname because Docker's user-defined networks provide service/container name-based communication.

* * *

# 8️⃣ Interact With a Running Container

Sometimes you need to enter a container to troubleshoot it.

The most useful command is:

```bash
docker exec
```

* * *

# `docker exec`

Run a command inside a running container.

```bash
docker exec mycontainer ls
```

* * *

## Open a Bash Shell

```bash
docker exec -it mycontainer /bin/bash
```

If Bash isn't available:

```bash
docker exec -it mycontainer /bin/sh
```

Important:

```text
-i → interactive
-t → terminal
```

Docker documents `docker exec` as executing a new command inside a running container.

* * *

## Run One Command

```bash
docker exec mycontainer ls /app
```

* * *

## Run as Root

```bash
docker exec -u root -it mycontainer sh
```

* * *

## Set Working Directory

```bash
docker exec -w /app mycontainer pwd
```

* * *

# `docker attach`

Attaches your terminal to a container's main process.

```bash
docker attach mycontainer
```

This is different from `docker exec`.

### `docker exec`

Starts a new process inside the container.

### `docker attach`

Connects to the container's existing main process.

For beginners, `docker exec` is generally the safer choice for interactive troubleshooting.

* * *

# 9️⃣ Copy Files Between Host and Container

* * *

# `docker cp`

Copy a file from host to container:

```bash
docker cp app.conf mycontainer:/app/app.conf
```

Copy a file from container to host:

```bash
docker cp mycontainer:/app/log.txt ./log.txt
```

Copy a directory:

```bash
docker cp ./config mycontainer:/app/
```

Useful for:

*   Debugging
    
*   Retrieving logs
    
*   Moving configuration
    
*   Temporary file transfers
    

For production applications, prefer proper image builds, volumes, or configuration mechanisms instead of manually modifying running containers.

* * *

# 🔟 Docker Cleanup Commands

Docker can consume significant disk space.

Images, containers, volumes, networks, and build cache can accumulate over time.

* * *

# `docker container prune`

Remove stopped containers:

```bash
docker container prune
```

* * *

# `docker image prune`

Remove dangling images:

```bash
docker image prune
```

* * *

# `docker image prune -a`

Remove unused images more aggressively:

```bash
docker image prune -a
```

Be careful because images you may want later can be removed.

* * *

# `docker network prune`

Remove unused networks:

```bash
docker network prune
```

* * *

# `docker volume prune`

Remove unused volumes:

```bash
docker volume prune
```

⚠️ Volumes may contain important application or database data.

* * *

# `docker system prune`

Clean unused Docker resources:

```bash
docker system prune
```

* * *

# `docker system prune -a`

More aggressive cleanup:

```bash
docker system prune -a
```

This can remove unused images in addition to stopped containers and unused networks.

Always review what you're deleting before running cleanup commands on important systems.

* * *

# `docker system df`

Before cleaning, check usage:

```bash
docker system df
```

A good habit is:

```text
Check
 ↓
docker system df
 ↓
Clean
 ↓
docker system prune
```

* * *

# 1️⃣1️⃣ Docker Commit, Export and Import

These commands are less common in modern application workflows but are useful to understand.

* * *

# `docker commit`

Creates a new image from a container's changes.

```bash
docker commit mycontainer myimage:v1
```

For example:

```text
Running Container
       ↓
Manual Changes
       ↓
docker commit
       ↓
New Image
```

However, for reproducible application builds, a Dockerfile is usually preferred.

* * *

# `docker export`

Exports a container filesystem as a tar archive.

```bash
docker export mycontainer > backup.tar
```

Important distinction:

`docker export` exports a **container filesystem**.

It does not preserve the image's complete layer history.

* * *

# `docker import`

Creates an image from a tar archive.

```bash
docker import backup.tar restored-image:latest
```

* * *

# `docker save` vs `docker export`

This is a common interview question.

### `docker save`

Used for images.

```bash
docker save -o image.tar myimage
```

### `docker export`

Used for containers.

```bash
docker export mycontainer > container.tar
```

Remember:

```text
IMAGE      → docker save
CONTAINER  → docker export
```

* * *

# 1️⃣2️⃣ Docker Compose Commands

Docker Compose is used to define and run multi-container applications.

For example:

```text
Application
   |
   +--- Frontend
   |
   +--- Backend
   |
   +--- Database
   |
   +--- Redis
```

Instead of manually running every container, Compose allows you to define the application stack in a YAML file.

Docker's current documentation describes Compose as a tool for defining and running multi-container applications.

Modern Docker uses:

```bash
docker compose
```

rather than the older standalone:

```bash
docker-compose
```

* * *

# `docker compose up`

Start the application stack:

```bash
docker compose up
```

Run in background:

```bash
docker compose up -d
```

* * *

# `docker compose down`

Stop and remove Compose-managed containers and networks:

```bash
docker compose down
```

* * *

# `docker compose build`

Build service images:

```bash
docker compose build
```

* * *

# `docker compose up --build`

Build images and start services:

```bash
docker compose up --build
```

* * *

# `docker compose ps`

Show Compose containers:

```bash
docker compose ps
```

Include stopped containers:

```bash
docker compose ps --all
```

The current Compose CLI supports `--all` to include stopped containers.

* * *

# `docker compose logs`

Show logs:

```bash
docker compose logs
```

Follow logs:

```bash
docker compose logs -f
```

Specific service:

```bash
docker compose logs -f backend
```

* * *

# `docker compose exec`

Run a command inside a service container:

```bash
docker compose exec web sh
```

For example:

```bash
docker compose exec db sh
```

Compose provides service-oriented execution, so you don't need to remember the generated container name.

* * *

# `docker compose pull`

Pull service images:

```bash
docker compose pull
```

* * *

# `docker compose push`

Push service images:

```bash
docker compose push
```

* * *

# `docker compose start`

Start existing containers:

```bash
docker compose start
```

Important difference:

```text
docker compose up
```

creates and starts containers when necessary.

```text
docker compose start
```

starts existing containers.

Docker documents `compose start` specifically as starting existing service containers.

* * *

# `docker compose stop`

Stop services:

```bash
docker compose stop
```

The containers remain available to start again.

* * *

# `docker compose restart`

Restart services:

```bash
docker compose restart
```

* * *

# `docker compose rm`

Remove stopped service containers:

```bash
docker compose rm
```

* * *

# `docker compose run`

Run a one-time command for a service:

```bash
docker compose run web sh
```

Useful for:

*   Database migrations
    
*   Admin commands
    
*   One-time scripts
    
*   Debugging
    

* * *

# `docker compose config`

Validate and render the Compose configuration:

```bash
docker compose config
```

This is very useful when debugging YAML, environment variables, or merged Compose files.

* * *

# `docker compose images`

List images used by the Compose project:

```bash
docker compose images
```

* * *

# `docker compose top`

Show processes running inside service containers:

```bash
docker compose top
```

* * *

# `docker compose stats`

Show resource usage:

```bash
docker compose stats
```

* * *

# `docker compose port`

Show the public port mapping for a service:

```bash
docker compose port web 80
```

* * *

# `docker compose ls`

List Compose projects:

```bash
docker compose ls
```

* * *

# `docker compose --dry-run`

Modern Docker Compose also supports dry-run mode for testing commands without applying stack changes.

Example:

```bash
docker compose --dry-run up --build -d
```

This is particularly useful when you want to understand what Compose plans to do before actually changing the environment.

* * *

# 1️⃣3️⃣ Real-World Docker Compose Example

Let's create a simple application with:

```text
Web
Database
```

Create:

```text
compose.yaml
```

Example:

```yaml
services:

  web:
    image: nginx:alpine
    ports:
      - "8080:80"

  redis:
    image: redis:alpine
```

Start:

```bash
docker compose up -d
```

Check:

```bash
docker compose ps
```

View logs:

```bash
docker compose logs
```

Stop:

```bash
docker compose stop
```

Start again:

```bash
docker compose start
```

Remove the stack:

```bash
docker compose down
```

The current Compose Specification is the recommended Compose file format; older Compose 2.x and 3.x file formats were merged into the Compose Specification.

* * *

# 1️⃣4️⃣ Docker Context Commands

Docker contexts allow the CLI to work with different Docker endpoints.

For example:

```text
Local Docker
      +
Remote Docker Server
      +
Cloud Environment
```

* * *

# `docker context ls`

List contexts:

```bash
docker context ls
```

* * *

# `docker context show`

Show the current context:

```bash
docker context show
```

* * *

# `docker context use`

Switch context:

```bash
docker context use my-context
```

* * *

# `docker context create`

Create a context.

For example, an SSH-based context:

```bash
docker context create remote-server --docker "host=ssh://user@server"
```

Then:

```bash
docker context use remote-server
```

Now Docker commands can target that context.

Switch back:

```bash
docker context use default
```

* * *

# `docker context inspect`

Inspect a context:

```bash
docker context inspect remote-server
```

* * *

# `docker context rm`

Remove a context:

```bash
docker context rm remote-server
```

* * *

# 1️⃣5️⃣ Docker Buildx Commands

Buildx provides advanced Docker image building capabilities.

It is especially useful for:

*   Multi-platform images
    
*   Advanced build workflows
    
*   CI/CD
    
*   Build cache
    
*   Modern Docker builds
    

* * *

# `docker buildx ls`

List builders:

```bash
docker buildx ls
```

* * *

# `docker buildx create`

Create a builder:

```bash
docker buildx create --name mybuilder
```

Use it:

```bash
docker buildx use mybuilder
```

* * *

# `docker buildx inspect`

Inspect a builder:

```bash
docker buildx inspect mybuilder
```

* * *

# `docker buildx build`

Build an image:

```bash
docker buildx build -t myapp:latest .
```

* * *

## Multi-Architecture Build

Build for AMD64 and ARM64:

```bash
docker buildx build \
  --platform linux/amd64,linux/arm64 \
  -t username/myapp:latest \
  --push .
```

This is useful when your application needs to run on different CPU architectures.

For example:

```text
Intel/AMD servers
        +
ARM servers
        ↓
Same Docker image tag
```

* * *

# 1️⃣6️⃣ Docker Manifest Commands

Manifests help work with image manifests and multi-platform image references.

* * *

# `docker manifest inspect`

Inspect a manifest:

```bash
docker manifest inspect nginx:latest
```

This can show information about supported platforms.

* * *

# `docker manifest create`

Create a manifest list:

```bash
docker manifest create \
  myapp:latest \
  myapp:amd64 \
  myapp:arm64
```

* * *

# `docker manifest push`

Push a manifest list:

```bash
docker manifest push myapp:latest
```

For most modern multi-platform build workflows, Buildx is generally the simpler approach.

* * *

# 1️⃣7️⃣ Docker Swarm Commands

Docker Swarm is Docker's native clustering/orchestration technology.

Kubernetes is more commonly encountered in modern cloud-native environments, but understanding Swarm is useful for Docker knowledge and interviews.

* * *

# `docker swarm init`

Initialize a Swarm:

```bash
docker swarm init
```

If you need to specify the advertised address:

```bash
docker swarm init --advertise-addr 192.168.1.10
```

* * *

# `docker swarm join`

Workers can join using the command generated by the manager:

```bash
docker swarm join --token <TOKEN> <MANAGER-IP>:2377
```

* * *

# `docker node ls`

List nodes:

```bash
docker node ls
```

* * *

# `docker node inspect`

Inspect a node:

```bash
docker node inspect node-name
```

* * *

# `docker node ps`

Show tasks running on a node:

```bash
docker node ps node-name
```

* * *

# `docker service create`

Create a service:

```bash
docker service create \
  --name web \
  --replicas 3 \
  nginx
```

This creates a service with three replicas.

* * *

# `docker service ls`

List services:

```bash
docker service ls
```

* * *

# `docker service ps`

Show service tasks:

```bash
docker service ps web
```

* * *

# `docker service scale`

Scale a service:

```bash
docker service scale web=5
```

Now:

```text
web
 ↓
5 replicas
```

* * *

# `docker service update`

Update a service:

```bash
docker service update --image nginx:latest web
```

* * *

# `docker service rm`

Remove a service:

```bash
docker service rm web
```

* * *

# `docker stack deploy`

Deploy a stack using a Compose file:

```bash
docker stack deploy -c compose.yaml myapp
```

* * *

# `docker stack ls`

List stacks:

```bash
docker stack ls
```

* * *

# `docker stack services`

List services in a stack:

```bash
docker stack services myapp
```

* * *

# `docker stack ps`

Show tasks in a stack:

```bash
docker stack ps myapp
```

* * *

# `docker stack rm`

Remove a stack:

```bash
docker stack rm myapp
```

* * *

# 1️⃣8️⃣ Docker Plugin Commands

Docker plugins can extend Docker functionality.

* * *

# `docker plugin ls`

List plugins:

```bash
docker plugin ls
```

* * *

# `docker plugin install`

Install a plugin:

```bash
docker plugin install <plugin>
```

Only install plugins from sources you trust and understand.

* * *

# `docker plugin enable`

Enable a plugin:

```bash
docker plugin enable <plugin>
```

* * *

# `docker plugin disable`

Disable:

```bash
docker plugin disable <plugin>
```

* * *

# `docker plugin inspect`

Inspect:

```bash
docker plugin inspect <plugin>
```

* * *

# `docker plugin rm`

Remove:

```bash
docker plugin rm <plugin>
```

* * *

# 1️⃣9️⃣ Useful Docker Filters

Docker provides filtering options for many commands.

* * *

## Find Containers by Status

```bash
docker ps -a --filter status=exited
```

* * *

## Find Containers by Name

```bash
docker ps --filter name=web
```

* * *

## Find Containers by Ancestor Image

```bash
docker ps --filter ancestor=nginx
```

* * *

## Show Only Container IDs

```bash
docker ps -q
```

This is extremely useful in shell scripts.

Example:

```bash
docker stop $(docker ps -q)
```

* * *

# 2️⃣0️⃣ Useful Docker Formatting Commands

Docker supports output formatting using Go templates.

For example:

```bash
docker ps --format "{{.Names}}"
```

Show container names and status:

```bash
docker ps --format "table {{.Names}}\t{{.Status}}"
```

Show image names:

```bash
docker images --format "{{.Repository}}:{{.Tag}}"
```

This is useful in:

*   Shell scripting
    
*   Automation
    
*   CI/CD pipelines
    
*   Monitoring scripts
    

* * *

# 2️⃣1️⃣ Common Docker Errors

Let's look at some problems beginners frequently face.

* * *

# ❌ Error: Docker Daemon Is Not Running

You may see an error similar to:

```text
Cannot connect to the Docker daemon
```

First check:

```bash
docker info
```

On Linux with systemd:

```bash
sudo systemctl status docker
```

Start Docker:

```bash
sudo systemctl start docker
```

Enable Docker at boot:

```bash
sudo systemctl enable docker
```

* * *

# ❌ Error: Container Name Already in Use

Example:

```text
Conflict. The container name is already in use.
```

Check:

```bash
docker ps -a
```

Then remove the old container:

```bash
docker rm old-container
```

Or choose another name:

```bash
docker run --name new-container nginx
```

* * *

# ❌ Error: Port Already Allocated

Example:

```text
port is already allocated
```

Find containers using ports:

```bash
docker ps
```

You can choose another host port:

```bash
docker run -d -p 8081:80 nginx
```

Now:

```text
localhost:8081
    ↓
container:80
```

* * *

# ❌ Container Immediately Exits

Run:

```bash
docker ps -a
```

Then:

```bash
docker logs <container>
```

For example:

```bash
docker logs myapp
```

Check the exit code:

```bash
docker inspect myapp
```

A common reason is that the container's main process finished or crashed.

Remember:

> A Docker container stays running only while its primary process is running.

* * *

# ❌ Cannot Enter Container With Bash

You may try:

```bash
docker exec -it mycontainer bash
```

and receive:

```text
bash: executable file not found
```

Some lightweight images don't include Bash.

Try:

```bash
docker exec -it mycontainer sh
```

* * *

# ❌ Image Not Found

Example:

```text
Unable to find image
```

Try:

```bash
docker pull image-name
```

Check the image name and tag:

```bash
docker search image-name
```

* * *

# ❌ Permission Denied on Linux

You may need:

```bash
sudo docker ps
```

If your Docker setup allows non-root access through the Docker group, configure it according to your system's Docker installation instructions.

Avoid blindly changing permissions on the Docker socket.

* * *

# 2️⃣2️⃣ Docker Commands Beginners Should Memorize

You don't need to memorize every Docker command.

Start with these:

```bash
docker --version
docker version
docker info

docker pull nginx
docker images

docker run nginx
docker run -d -p 8080:80 nginx

docker ps
docker ps -a

docker stop <container>
docker start <container>
docker restart <container>
docker rm <container>

docker logs <container>
docker exec -it <container> sh

docker inspect <container>
docker stats

docker build -t myapp:latest .
docker rmi <image>

docker login
docker tag <image> <username>/<image>:latest
docker push <username>/<image>:latest

docker volume ls
docker volume create <volume>

docker network ls
docker network create <network>

docker compose up -d
docker compose down
docker compose ps
docker compose logs -f
docker compose exec <service> sh
```

If you understand these commands, you already have a strong foundation.

* * *

# 2️⃣3️⃣ Docker Cheat Sheet

## 🔵 Docker Basics

| Command | Purpose |
| --- | --- |
| `docker --version` | Check Docker version |
| `docker version` | Show client/server version |
| `docker info` | Show Docker system information |
| `docker --help` | Show help |

* * *

## 🟢 Containers

| Command | Purpose |
| --- | --- |
| `docker run` | Create and start container |
| `docker create` | Create container |
| `docker start` | Start stopped container |
| `docker stop` | Stop container |
| `docker restart` | Restart container |
| `docker pause` | Pause container |
| `docker unpause` | Resume container |
| `docker kill` | Force stop container |
| `docker rm` | Remove container |
| `docker rename` | Rename container |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker exec` | Execute command inside container |
| `docker attach` | Attach to main process |
| `docker logs` | View logs |
| `docker stats` | Resource usage |
| `docker top` | Running processes |
| `docker inspect` | Detailed information |
| `docker port` | Show port mappings |
| `docker diff` | Show filesystem changes |

* * *

## 🟡 Images

| Command | Purpose |
| --- | --- |
| `docker pull` | Download image |
| `docker build` | Build image |
| `docker images` | List images |
| `docker image ls` | List images |
| `docker rmi` | Remove image |
| `docker tag` | Create image tag |
| `docker history` | Show image layers |
| `docker save` | Save image to tar |
| `docker load` | Load image from tar |
| `docker inspect` | Inspect image/object |

* * *

## 🟣 Volumes

| Command | Purpose |
| --- | --- |
| `docker volume create` | Create volume |
| `docker volume ls` | List volumes |
| `docker volume inspect` | Inspect volume |
| `docker volume rm` | Remove volume |
| `docker volume prune` | Remove unused volumes |

* * *

## 🔴 Networks

| Command | Purpose |
| --- | --- |
| `docker network create` | Create network |
| `docker network ls` | List networks |
| `docker network inspect` | Inspect network |
| `docker network connect` | Connect container |
| `docker network disconnect` | Disconnect container |
| `docker network rm` | Remove network |
| `docker network prune` | Remove unused networks |

* * *

## 🟠 Registry

| Command | Purpose |
| --- | --- |
| `docker login` | Login to registry |
| `docker logout` | Logout |
| `docker search` | Search Docker Hub |
| `docker tag` | Tag image |
| `docker push` | Push image |
| `docker pull` | Pull image |

* * *

## 🟤 Compose

| Command | Purpose |
| --- | --- |
| `docker compose up` | Create/start services |
| `docker compose down` | Stop/remove stack |
| `docker compose build` | Build services |
| `docker compose ps` | List services |
| `docker compose logs` | View logs |
| `docker compose exec` | Execute command |
| `docker compose pull` | Pull images |
| `docker compose push` | Push images |
| `docker compose start` | Start existing services |
| `docker compose stop` | Stop services |
| `docker compose restart` | Restart services |
| `docker compose run` | Run one-off command |
| `docker compose config` | Validate/render config |

* * *

# 🧠 Most Important Docker Concepts to Understand

Don't just memorize commands.

Understand these relationships:

```text
Dockerfile
     ↓
docker build
     ↓
Docker Image
     ↓
docker run
     ↓
Docker Container
     ↓
docker stop
     ↓
Stopped Container
     ↓
docker start
     ↓
Running Container
```

For persistent storage:

```text
Container
    ↓
Volume
    ↓
Persistent Data
```

For networking:

```text
Container A
     ↕
Docker Network
     ↕
Container B
```

For image distribution:

```text
Dockerfile
    ↓
Build Image
    ↓
Tag Image
    ↓
Docker Registry
    ↓
Push Image
    ↓
Pull Image
    ↓
Run Container
```

* * *

# 🚀 Real-World Docker Workflow

A common application workflow looks like this:

## Step 1: Create Dockerfile

```dockerfile
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

* * *

## Step 2: Build Image

```bash
docker build -t my-node-app:1.0 .
```

* * *

## Step 3: Run Container

```bash
docker run -d \
  --name my-node-app \
  -p 3000:3000 \
  my-node-app:1.0
```

* * *

## Step 4: Check Container

```bash
docker ps
```

* * *

## Step 5: Check Logs

```bash
docker logs my-node-app
```

* * *

## Step 6: Enter Container

```bash
docker exec -it my-node-app sh
```

* * *

## Step 7: Stop Application

```bash
docker stop my-node-app
```

* * *

## Step 8: Remove Container

```bash
docker rm my-node-app
```

* * *

# 🔄 Docker CI/CD Workflow

Docker is heavily used in CI/CD pipelines.

A simplified workflow looks like:

```text
Developer
    ↓
Git Push
    ↓
CI Pipeline
    ↓
Run Tests
    ↓
docker build
    ↓
Docker Image
    ↓
docker tag
    ↓
docker push
    ↓
Container Registry
    ↓
Deployment Server
    ↓
docker pull
    ↓
docker run
```

For example:

```bash
docker build -t myapp:1.0 .
```

Then:

```bash
docker tag myapp:1.0 username/myapp:1.0
```

Then:

```bash
docker push username/myapp:1.0
```

On the deployment server:

```bash
docker pull username/myapp:1.0
```

Then:

```bash
docker run -d username/myapp:1.0
```

This is one of the fundamental Docker workflows used in DevOps.

* * *

# 🎯 Docker Interview Questions Based on These Commands

If you're preparing for a DevOps interview, make sure you can answer these.

### 1\. What is the difference between `docker run` and `docker start`?

```text
docker run
= Create + Start a new container

docker start
= Start an existing stopped container
```

* * *

### 2\. What is the difference between `docker stop` and `docker kill`?

```text
docker stop
= Graceful shutdown

docker kill
= Forceful shutdown
```

* * *

### 3\. What is the difference between an image and a container?

```text
Image
= Template/package

Container
= Running instance of an image
```

* * *

### 4\. What is the difference between `docker exec` and `docker attach`?

```text
docker exec
= Starts a new process

docker attach
= Connects to the existing main process
```

* * *

### 5\. What is the difference between `docker save` and `docker export`?

```text
docker save
= Save an image

docker export
= Export a container filesystem
```

* * *

### 6\. What is the difference between `docker compose up` and `docker compose start`?

```text
docker compose up
= Creates/recreates and starts services when needed

docker compose start
= Starts existing service containers
```

* * *

### 7\. How do you check container logs?

```bash
docker logs <container>
```

* * *

### 8\. How do you enter a running container?

```bash
docker exec -it <container> sh
```

or:

```bash
docker exec -it <container> bash
```

depending on the image.

* * *

### 9\. How do you check Docker disk usage?

```bash
docker system df
```

* * *

### 10\. How do you remove unused Docker resources?

```bash
docker system prune
```

* * *

# ⚠️ Important Docker Safety Tips

Docker commands can delete data, so be careful.

Especially review these commands before running them:

```bash
docker rm -f
docker rmi -f
docker volume rm
docker volume prune
docker system prune
docker system prune -a
```

The most dangerous mistake for beginners is deleting a volume containing important database data.

Before cleanup, inspect:

```bash
docker volume ls
```

and:

```bash
docker system df
```

* * *

# 🧩 Docker Command Mental Model

If you forget a command, think about what you are trying to manage.

```text
What am I managing?
        |
        +---- Container?
        |       |
        |       +-- docker ps
        |       +-- docker run
        |       +-- docker stop
        |       +-- docker exec
        |       +-- docker logs
        |
        +---- Image?
        |       |
        |       +-- docker pull
        |       +-- docker build
        |       +-- docker images
        |       +-- docker push
        |
        +---- Volume?
        |       |
        |       +-- docker volume ls
        |       +-- docker volume create
        |       +-- docker volume inspect
        |
        +---- Network?
        |       |
        |       +-- docker network ls
        |       +-- docker network create
        |       +-- docker network inspect
        |
        +---- Multi-container app?
        |       |
        |       +-- docker compose up
        |       +-- docker compose down
        |       +-- docker compose logs
        |
        +---- Build?
                |
                +-- docker build
                +-- docker buildx build
```

This mental model is much more useful than trying to memorize hundreds of commands.

* * *

# 📚 Docker Learning Roadmap

If you are completely new to Docker, don't try to learn everything in one day.

Follow this order:

```text
1. Docker Basics
       ↓
2. Images
       ↓
3. Containers
       ↓
4. Dockerfile
       ↓
5. Ports
       ↓
6. Volumes
       ↓
7. Networks
       ↓
8. Docker Compose
       ↓
9. Docker Registry
       ↓
10. Docker Buildx
       ↓
11. CI/CD
       ↓
12. Kubernetes
```

* * *

# 🏆 Docker Commands You Should Know for DevOps

If your goal is to become a DevOps Engineer, prioritize these:

```bash
docker pull
docker build
docker run
docker ps
docker ps -a
docker stop
docker start
docker restart
docker rm
docker exec
docker logs
docker inspect
docker stats
docker images
docker rmi
docker tag
docker push
docker login

docker volume ls
docker volume create
docker volume inspect

docker network ls
docker network create
docker network inspect
docker network connect

docker compose up
docker compose down
docker compose ps
docker compose logs
docker compose exec
docker compose build

docker system df
docker system prune

docker buildx build
docker buildx ls
```

* * *

# 💡 Final Advice for Beginners

The biggest mistake beginners make is trying to memorize Docker commands.

Don't do that.

Instead, understand the lifecycle:

```text
Build
  ↓
Image
  ↓
Run
  ↓
Container
  ↓
Inspect
  ↓
Logs
  ↓
Debug
  ↓
Stop
  ↓
Remove
```

Then understand supporting resources:

```text
Container
   ├── Network
   ├── Volume
   └── Image
```

And for multi-container applications:

```text
Docker Compose
      ↓
Multiple Containers
      ↓
Networks + Volumes
      ↓
Complete Application
```

Once you understand this flow, Docker commands become much easier.

* * *

# 📝 Quick Docker Practice Lab

If you are a beginner, try these commands yourself.

### Step 1 — Pull Nginx

```bash
docker pull nginx
```

### Step 2 — Run Nginx

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

### Step 3 — Check Container

```bash
docker ps
```

### Step 4 — Open in Browser

```text
http://localhost:8080
```

### Step 5 — Check Logs

```bash
docker logs my-nginx
```

### Step 6 — Inspect

```bash
docker inspect my-nginx
```

### Step 7 — Enter Container

```bash
docker exec -it my-nginx sh
```

### Step 8 — Check Processes

```bash
docker top my-nginx
```

### Step 9 — Check Resources

```bash
docker stats my-nginx
```

### Step 10 — Stop Container

```bash
docker stop my-nginx
```

### Step 11 — Start Again

```bash
docker start my-nginx
```

### Step 12 — Remove Container

```bash
docker stop my-nginx
docker rm my-nginx
```

Congratulations 🎉

You have just completed a basic Docker container lifecycle.

* * *

# 🔥 Final Docker Cheat Sheet

```bash
# Docker
docker --version
docker version
docker info
docker --help

# Images
docker pull nginx
docker images
docker build -t myapp .
docker rmi myapp
docker tag myapp username/myapp:v1
docker push username/myapp:v1
docker history nginx
docker save -o image.tar myapp
docker load -i image.tar

# Containers
docker run -d nginx
docker run --name web -d -p 8080:80 nginx
docker ps
docker ps -a
docker create nginx
docker start web
docker stop web
docker restart web
docker pause web
docker unpause web
docker kill web
docker rm web
docker rename web web-server

# Debugging
docker logs web
docker logs -f web
docker inspect web
docker exec -it web sh
docker top web
docker stats web
docker port web
docker diff web
docker events

# Files
docker cp file.txt web:/tmp/
docker cp web:/tmp/file.txt .

# Volumes
docker volume create data
docker volume ls
docker volume inspect data
docker volume rm data
docker volume prune

# Networks
docker network create app-network
docker network ls
docker network inspect app-network
docker network connect app-network web
docker network disconnect app-network web
docker network rm app-network
docker network prune

# Cleanup
docker system df
docker container prune
docker image prune
docker network prune
docker volume prune
docker system prune
docker system prune -a

# Registry
docker login
docker logout
docker search nginx
docker tag myapp username/myapp:latest
docker push username/myapp:latest

# Compose
docker compose up -d
docker compose down
docker compose build
docker compose up --build -d
docker compose ps
docker compose logs -f
docker compose exec web sh
docker compose pull
docker compose push
docker compose start
docker compose stop
docker compose restart
docker compose run web sh
docker compose config
docker compose ls

# Context
docker context ls
docker context show
docker context inspect
docker context create
docker context use
docker context rm

# Buildx
docker buildx ls
docker buildx create --name builder
docker buildx use builder
docker buildx inspect builder
docker buildx build -t myapp .

# Swarm
docker swarm init
docker node ls
docker service create
docker service ls
docker service ps
docker service scale
docker service update
docker service rm
docker stack deploy
docker stack ls
docker stack services
docker stack ps
docker stack rm
```

* * *

# 🎯 Conclusion

Docker becomes much easier when you stop treating it as a collection of commands and start understanding the relationship between its components.

Remember this:

```text
Dockerfile
     ↓
docker build
     ↓
Image
     ↓
docker run
     ↓
Container
     ↓
docker exec / logs / inspect
     ↓
Debug & Manage
     ↓
docker stop
     ↓
docker rm
```

For persistent data:

```text
Volume
```

For communication:

```text
Network
```

For multiple containers:

```text
Docker Compose
```

For sharing images:

```text
Docker Registry
```

For multi-platform builds:

```text
Docker Buildx
```

For container orchestration with Docker:

```text
Docker Swarm
```

The official Docker CLI reference provides the current command hierarchy and includes areas such as containers, images, Compose, contexts, Buildx, manifests, and newer CLI capabilities.

The best way to learn Docker is simple:

> **Don't just read Docker commands. Run them. Break things. Inspect them. Fix them. Repeat.**

Start with:

```bash
docker run
docker ps
docker logs
docker exec
docker inspect
docker stop
docker rm
```

Then move to:

```bash
docker build
docker volume
docker network
docker compose
docker push
docker buildx
```

With regular practice, Docker will stop feeling like a huge list of commands and start feeling like a logical workflow.

* * *

## 🚀 What's Next?

If you're learning DevOps, your next topics after Docker should be:

```text
Docker
   ↓
Docker Compose
   ↓
Docker Registry
   ↓
Jenkins / GitHub Actions
   ↓
CI/CD
   ↓
AWS
   ↓
Kubernetes
   ↓
Helm
   ↓
Monitoring
   ↓
Prometheus + Grafana
```

Keep practicing, keep building, and keep shipping. 🚀🐳

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