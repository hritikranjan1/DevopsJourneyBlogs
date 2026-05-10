---
title: " DevOps Week 4: Containers & Docker Fundamentals/Project Management"
seoTitle: "DevOps Week 4: Containers & Docker Fundamentals"
seoDescription: "Learn containers, Docker basics, architecture, and lifecycle with hands-on practice in this DevOps Week 4 beginner guide."
datePublished: 2026-04-26T04:55:59.239Z
cuid: cmofapds0009228jpcjet2qlh
slug: devops-week-4-containers-docker-fundamentals-project-management
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/30890e5e-80d2-42d2-8ec1-b0828036ddcc.png
tags: docker, aws, cloud-computing, devops, beginners, containers, containerization, devops-journey

---

## DevOps Project Management & First Week

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/6e1deaf6-119d-4580-83f6-90019cab11b4.png align="center")

## 🔹 1. Why Project Management is Important in DevOps?

👉 DevOps is not just coding or tools

👉 You also need to:

*   Track tasks
    
*   Manage work
    
*   Collaborate with teams
    

💡 Without management → work becomes messy

* * *

## 🔹 2. Traditional vs Agile (Very Important 🔥)

* * *

### ❌ Waterfall Model (Old Method)

*   Work done step by step
    
*   No flexibility
    
*   Changes are difficult
    

* * *

### ✔ Agile Methodology (Modern)

### 👉 Work is divided into **small parts (Sprints)**

### Sprint = 2–3 weeks

*   Continuous feedback
    
*   Faster delivery
    

* * *

### ✔ Why Agile?

*   Flexible
    
*   Faster updates
    
*   Better teamwork
    

* * *

### 🔹 3. Key Project Management Tools

* * *

## 🔹 Jira (Most Important 🔥)

### 👉 What it is:

*   Task management tool
    

👉 Used for:

*   Create tasks
    
*   Track progress
    
*   Manage bugs
    

* * *

## ✔ Example:

*   Task → “Deploy app on AWS”
    
*   Status → To Do / In Progress / Done
    

* * *

## ✔ Why Jira?

*   Industry standard
    
*   Used in almost every company
    

* * *

## 🔹 Confluence

👉 What it is:

*   Documentation tool
    

👉 Use:

*   Store notes
    
*   Share knowledge
    

* * *

## 🔹 SharePoint

👉 Similar to Confluence

👉 Used in:

*   Large organizations
    

* * *

## 🔹 ServiceNow (Very Important 🔥)

### 👉 Used for:

### ✔ 1. Incident Management

*   When system fails
    
*   Fix issues quickly
    

👉 Example:

*   Server down → ticket created
    

* * *

### ✔ 2. Change Management

👉 Controlled process to:

*   Make changes safely
    

👉 Example:

*   Deploy update without downtime
    

* * *

## 🔹 Read the Docs

👉 Open-source documentation tool

👉 Used with:

*   GitHub
    

* * *

## 🔹 Git & GitHub

👉 Used for:

*   Code management
    
*   Version control
    

👉 Also used for:

*   Tracking tasks (GitHub Projects)
    

* * *

## 🔹 4. What DevOps Engineer Does in First Week?

* * *

## ✔ 1. Understand Project

*   Learn system architecture
    
*   Understand tools used
    

* * *

## ✔ 2. Access Setup

*   GitHub access
    
*   AWS access
    
*   Jira access
    

* * *

## ✔ 3. Learn Workflow

*   How tasks move in Jira
    
*   How deployments happen
    

* * *

## ✔ 4. Monitoring & Alerts

*   Understand tools like:
    
    *   Prometheus
        
    *   Grafana
        

* * *

## ✔ 5. Handle Tickets

*   Small bug fixes
    
*   Minor tasks
    

* * *

## ✔ 6. Documentation

*   Read Confluence / Docs
    

* * *

## 🔹 5. Real DevOps Workflow

1.  Task created in Jira
    
2.  Developer works on code
    
3.  Code pushed to GitHub
    
4.  CI/CD pipeline runs
    
5.  Deploy to server
    
6.  Monitor using tools
    
7.  If issue → ServiceNow ticket
    

* * *

## 📘Containers in DevOps

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/72d2167c-46ca-47c8-82bb-d31501fd46df.png align="center")

## 🔹 1. What is a Container?

👉 Container = **Lightweight environment to run applications**

*   Contains:
    
    *   Code
        
    *   Dependencies
        
    *   Libraries
        

👉 Works same everywhere 💡 “Build once, run anywhere”

* * *

## 🔹 2. Problem with Traditional Systems ❌

* * *

## 🖥️ Physical Servers

*   One app per server
    
*   Wasted resources
    

* * *

## 🧱 Virtual Machines (VMs)

👉 Improvement over physical servers

*   Multiple VMs on one machine
    
*   Each VM has:
    
    *   Full OS
        
    *   Applications
        

* * *

## ❌ Issues with VMs:

*   Heavy (uses more RAM & CPU)
    
*   Slow startup
    
*   Large size
    

* * *

## 🔹 3. Containers vs Virtual Machines 🔥

* * *

## 🧱 Virtual Machine

*   Full OS required
    
*   Heavy
    
*   Slow
    

* * *

## 📦 Container

*   No full OS
    
*   Uses host OS
    
*   Lightweight
    
*   Fast
    

* * *

## 👉 Simple Difference:

*   VM = Separate machine
    
*   Container = Isolated app environment
    

* * *

## 🔹 4. Why Containers are Better?

✔ Fast startup ✔ Lightweight ✔ Easy to deploy ✔ Portable

* * *

## 👉 Real Example:

*   App works on your laptop 👉 Same container runs on:
    
*   Server
    
*   Cloud
    
*   Anywhere
    

* * *

## 🔹 5. Container Architecture

👉 Containers can run on:

*   Physical server
    
*   Virtual machine (common in cloud)
    

* * *

## ✔ Modern Practice:

👉 Containers run on:

*   Cloud VMs (AWS, Azure, GCP)
    

👉 Benefits:

*   Less maintenance
    
*   Easy scaling
    

* * *

## 🔹 6. Docker (Most Important 🔥)

👉 Docker = Container platform

* * *

## ✔ What Docker does:

*   Creates containers
    
*   Runs applications
    

* * *

## ✔ Key Components:

### 🔹 Dockerfile

*   Instructions to build image
    

* * *

### 🔹 Docker Image

*   Blueprint of application
    

* * *

### 🔹 Container

*   Running instance of image
    

* * *

## 👉 Flow:

```id="c1g8sd"
Dockerfile → Image → Container
```

* * *

## 🔹 7. Buildah (Alternative to Docker)

👉 Buildah = Tool to build container images

* * *

## ✔ Why Buildah?

*   No daemon (no background engine)
    
*   More secure
    
*   Avoids single point of failure
    

* * *

## ✔ Works with:

*   Podman
    
*   Skopeo
    

* * *

## 🔹 8. Docker vs Buildah

| Feature | Docker | Buildah |
| --- | --- | --- |
| Engine | Required | Not required |
| Setup | Easy | Advanced |
| Use | Beginners | Advanced users |

* * *

## 🔹 9. Why Containers are Important in DevOps?

👉 DevOps focuses on:

*   Automation
    
*   Scalability
    
*   Consistency
    

👉 Containers help in:

*   Faster deployment
    
*   Easy scaling
    
*   Environment consistency
    

* * *

## 🔹 10. Real DevOps Workflow

1.  Write code
    
2.  Create Dockerfile
    
3.  Build image
    
4.  Run container
    
5.  Deploy to cloud
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/b995101d-089d-4230-a887-ccbbf68464f4.png align="center")

## What is a container ?

A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

Ok, let me make it easy !!!

A container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.

![Screenshot 2023-02-07 at 7 18 10 PM](https://user-images.githubusercontent.com/43399466/217262726-7cabcb5b-074d-45cc-950e-84f7119e7162.png align="center")

## Containers vs Virtual Machine

Containers and virtual machines are both technologies used to isolate applications and their dependencies, but they have some key differences:

```plaintext
1. Resource Utilization: Containers share the host operating system kernel, making them lighter and faster than VMs. VMs have a full-fledged OS and hypervisor, making them more resource-intensive.

2. Portability: Containers are designed to be portable and can run on any system with a compatible host operating system. VMs are less portable as they need a compatible hypervisor to run.

3. Security: VMs provide a higher level of security as each VM has its own operating system and can be isolated from the host and other VMs. Containers provide less isolation, as they share the host operating system.
```

4.  Management: Managing containers is typically easier than managing VMs, as containers are designed to be lightweight and fast-moving.
    

## Why are containers light weight ?

Containers are lightweight because they use a technology called containerization, which allows them to share the host operating system's kernel and libraries, while still providing isolation for the application and its dependencies. This results in a smaller footprint compared to traditional virtual machines, as the containers do not need to include a full operating system. Additionally, Docker containers are designed to be minimal, only including what is necessary for the application to run, further reducing their size.

Let's try to understand this with an example:

Below is the screenshot of official ubuntu base image which you can use for your container. It's just ~ 22 MB, isn't it very small ? on a contrary if you look at official ubuntu VM image it will be close to ~ 2.3 GB. So the container base image is almost 100 times less than VM image.

![Screenshot 2023-02-08 at 3 12 38 PM](https://user-images.githubusercontent.com/43399466/217493284-85411ae0-b283-4475-9729-6b082e35fc7d.png align="center")

To provide a better picture of files and folders that containers base images have and files and folders that containers use from host operating system (not 100 percent accurate -> varies from base image to base image). Refer below.

### Files and Folders in containers base images

```plaintext
    /bin: contains binary executable files, such as the ls, cp, and ps commands.

    /sbin: contains system binary executable files, such as the init and shutdown commands.

    /etc: contains configuration files for various system services.

    /lib: contains library files that are used by the binary executables.

    /usr: contains user-related files and utilities, such as applications, libraries, and documentation.

    /var: contains variable data, such as log files, spool files, and temporary files.

    /root: is the home directory of the root user.
```

### Files and Folders that containers use from host operating system

```plaintext
    The host's file system: Docker containers can access the host file system using bind mounts, which allow the container to read and write files in the host file system.

    Networking stack: The host's networking stack is used to provide network connectivity to the container. Docker containers can be connected to the host's network directly or through a virtual network.

    System calls: The host's kernel handles system calls from the container, which is how the container accesses the host's resources, such as CPU, memory, and I/O.

    Namespaces: Docker containers use Linux namespaces to create isolated environments for the container's processes. Namespaces provide isolation for resources such as the file system, process ID, and network.

    Control groups (cgroups): Docker containers use cgroups to limit and control the amount of resources, such as CPU, memory, and I/O, that a container can access.
    
```

It's important to note that while a container uses resources from the host operating system, it is still isolated from the host and other containers, so changes to the container do not affect the host or other containers.

**Note:** There are multiple ways to reduce your VM image size as well, but I am just talking about the default for easy comparision and understanding.

so, in a nutshell, container base images are typically smaller compared to VM images because they are designed to be minimalist and only contain the necessary components for running a specific application or service. VMs, on the other hand, emulate an entire operating system, including all its libraries, utilities, and system files, resulting in a much larger size.

I hope it is now very clear why containers are light weight in nature.

## Docker

### What is Docker ?

Docker is a containerization platform that provides easy way to containerize your applications, which means, using Docker you can build container images, run the images to create containers and also push these containers to container regestries such as DockerHub, Quay.io and so on.

In simple words, you can understand as `containerization is a concept or technology` and `Docker Implements Containerization`.

### Docker Architecture ?

![image](https://user-images.githubusercontent.com/43399466/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png align="center")

The above picture, clearly indicates that Docker Deamon is brain of Docker. If Docker Deamon is killed, stops working for some reasons, Docker is brain dead :p (sarcasm intended).

### Docker LifeCycle

We can use the above Image as reference to understand the lifecycle of Docker.

There are three important things,

1.  docker build -> builds docker images from Dockerfile
    
2.  docker run -> runs container from docker images
    
3.  docker push -> push the container image to public/private regestries to share the docker images.
    

![Screenshot 2023-02-08 at 4 32 13 PM](https://user-images.githubusercontent.com/43399466/217511949-81f897b2-70ee-41d1-b229-38d0572c54c7.png align="center")

### Understanding the terminology (Inspired from Docker Docs)

#### Docker daemon

The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

#### Docker client

The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

#### Docker Desktop

Docker Desktop is an easy-to-install application for your Mac, Windows or Linux environment that enables you to build and share containerized applications and microservices. Docker Desktop includes the Docker daemon (dockerd), the Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes, and Credential Helper. For more information, see Docker Desktop.

#### Docker registries

A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own private registry.

When you use the docker pull or docker run commands, the required images are pulled from your configured registry. When you use the docker push command, your image is pushed to your configured registry. Docker objects

When you use Docker, you are creating and using images, containers, networks, volumes, plugins, and other objects. This section is a brief overview of some of those objects.

#### Dockerfile

Dockerfile is a file where you provide the steps to build your Docker Image.

#### Images

An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization. For example, you may build an image which is based on the ubuntu image, but installs the Apache web server and your application, as well as the configuration details needed to make your application run.

You might create your own images or you might only use those created by others and published in a registry. To build your own image, you create a Dockerfile with a simple syntax for defining the steps needed to create the image and run it. Each instruction in a Dockerfile creates a layer in the image. When you change the Dockerfile and rebuild the image, only those layers which have changed are rebuilt. This is part of what makes images so lightweight, small, and fast, when compared to other virtualization technologies.

## INSTALL DOCKER

A very detailed instructions to install Docker are provide in the below link

https://docs.docker.com/get-docker/

For Demo,

You can create an Ubuntu EC2 Instance on AWS and run the below commands to install docker.

```plaintext
sudo apt update
sudo apt install docker.io -y
```

### Start Docker and Grant Access

A very common mistake that many beginners do is, After they install docker using the sudo access, they miss the step to Start the Docker daemon and grant acess to the user they want to use to interact with docker and run docker commands.

Always ensure the docker daemon is up and running.

A easy way to verify your Docker installation is by running the below command

```plaintext
docker run hello-world
```

If the output says:

```plaintext
docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
```

This can mean two things,

1.  Docker deamon is not running.
    
2.  Your user does not have access to run docker commands.
    

### Start Docker daemon

You use the below command to verify if the docker daemon is actually started and Active

```plaintext
sudo systemctl status docker
```

If you notice that the docker daemon is not running, you can start the daemon using the below command

```plaintext
sudo systemctl start docker
```

### Grant Access to your user to run docker commands

To grant access to your user to run the docker command, you should add the user to the Docker Linux group. Docker group is create by default when docker is installed.

```plaintext
sudo usermod -aG docker ubuntu
```

In the above command `ubuntu` is the name of the user, you can change the username appropriately.

**NOTE:** : You need to logout and login back for the changes to be reflected.

### Docker is Installed, up and running 🥳🥳

Use the same command again, to verify that docker is up and running.

```plaintext
docker run hello-world
```

Output should look like:

```plaintext
....
....
Hello from Docker!
This message shows that your installation appears to be working correctly.
...
...
```

## Great Job, Now start with the examples folder to write your first Dockerfile and move to the next examples. Happy Learning :)

### Clone this repository and move to example folder

```plaintext
git clone https://github.com/iam-veeramalla/Docker-Zero-to-Hero
cd  examples
```

### Login to Docker \[Create an account with https://hub.docker.com/\]

```plaintext
docker login
```

```plaintext
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: abhishekf5
Password:
WARNING! Your password will be stored unencrypted in /home/ubuntu/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```

### Build your first Docker Image

You need to change the username accoringly in the below command

```plaintext
docker build -t abhishekf5/my-first-docker-image:latest .
```

Output of the above command

```plaintext
    Sending build context to Docker daemon  992.8kB
    Step 1/6 : FROM ubuntu:latest
    latest: Pulling from library/ubuntu
    677076032cca: Pull complete
    Digest: sha256:9a0bdde4188b896a372804be2384015e90e3f84906b750c1a53539b585fbbe7f
    Status: Downloaded newer image for ubuntu:latest
     ---> 58db3edaf2be
    Step 2/6 : WORKDIR /app
     ---> Running in 630f5e4db7d3
    Removing intermediate container 630f5e4db7d3
     ---> 6b1d9f654263
    Step 3/6 : COPY . /app
     ---> 984edffabc23
    Step 4/6 : RUN apt-get update && apt-get install -y python3 python3-pip
     ---> Running in a558acdc9b03
    Step 5/6 : ENV NAME World
     ---> Running in 733207001f2e
    Removing intermediate container 733207001f2e
     ---> 94128cf6be21
    Step 6/6 : CMD ["python3", "app.py"]
     ---> Running in 5d60ad3a59ff
    Removing intermediate container 5d60ad3a59ff
     ---> 960d37536dcd
    Successfully built 960d37536dcd
    Successfully tagged abhishekf5/my-first-docker-image:latest
```

### Verify Docker Image is created

```plaintext
docker images
```

Output

```plaintext
REPOSITORY                         TAG       IMAGE ID       CREATED          SIZE
abhishekf5/my-first-docker-image   latest    960d37536dcd   26 seconds ago   467MB
ubuntu                             latest    58db3edaf2be   13 days ago      77.8MB
hello-world                        latest    feb5d9fea6a5   16 months ago    13.3kB
```

### Run your First Docker Container

```plaintext
docker run -it abhishekf5/my-first-docker-image
```

Output

```plaintext
Hello World
```

### Push the Image to DockerHub and share it with the world

```plaintext
docker push abhishekf5/my-first-docker-image
```

Output

```plaintext
Using default tag: latest
The push refers to repository [docker.io/abhishekf5/my-first-docker-image]
896818320e80: Pushed
b8088c305a52: Pushed
69dd4ccec1a0: Pushed
c5ff2d88f679: Mounted from library/ubuntu
latest: digest: sha256:6e49841ad9e720a7baedcd41f9b666fcd7b583151d0763fe78101bb8221b1d88 size: 1157
```

### You must be feeling like a champ already

Repo link - [https://github.com/hritikranjan1/Docker-Zero-to-Hero.git](https://github.com/hritikranjan1/Docker-Zero-to-Hero.git)  
org - [https://github.com/iam-veeramalla/Docker-Zero-to-Hero.git](https://github.com/iam-veeramalla/Docker-Zero-to-Hero.git)