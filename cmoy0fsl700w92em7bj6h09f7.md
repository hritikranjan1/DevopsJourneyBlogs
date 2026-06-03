---
title: "DevOps Week 5 – Docker Networking, Storage & Advanced Containerization"
seoTitle: "DevOps Week 5: Docker Networking & Storage Guide"
seoDescription: "Learn Docker networking, volumes, bind mounts, and containerization concepts with beginner-friendly DevOps notes."
datePublished: 2026-05-09T07:16:13.059Z
cuid: cmoy0fsl700w92em7bj6h09f7
slug: devops-week-5-docker-networking-storage-advanced-containerization
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/57e0710d-be85-4a2e-91d8-1acd1a06462a.png
ogImage: https://cdn.hashnode.com/uploads/og-images/66fecde7cb0abd844c1a2f3c/3b2fbe18-2a65-46d1-9907-5eaef065942c.png
tags: docker, aws, devops, beginners, containers, dockervolume, dockernetworking

---

* * *

## Dockerizing Django Application

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/8d3ca266-6763-4785-8c14-a6b64d6f2d87.png align="center")

* * *

## 🔹 1. Django Basics (Very Important 🔥)

👉 Django = Python web framework

* * *

## ✔ Project Structure

### 📂 `settings.py`

*   Configuration file
    
*   Database, apps, security settings
    

* * *

### 📂 `urls.py`

*   Handles routing 👉 URL → View mapping
    

* * *

### 📂 `startapp`

👉 Command to create new app

```bash
python manage.py startapp myapp
```

👉 Helps in modular development

* * *

## 🔹 2. Why Containerize Django? 📦

👉 Problem without Docker:

*   Works on my system but not on server
    
*   Dependency issues
    

* * *

## ✔ Solution: Docker

👉 Package everything:

*   Code
    
*   Dependencies
    
*   Environment
    

💡 Result: 👉 Runs same everywhere

* * *

## 🔹 3. Dockerfile for Django 🔥

* * *

### ✔ Basic Dockerfile Example

```dockerfile
FROM python:3.9

WORKDIR /app

COPY . .

RUN pip install -r requirements.txt

CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

* * *

## ✔ Explanation:

*   `FROM` → Base image
    
*   `WORKDIR` → Working folder
    
*   `COPY` → Copy project files
    
*   `RUN` → Install dependencies
    
*   `CMD` → Run application
    

* * *

## 🔹 4. ENTRYPOINT vs CMD 🔥 (Important)

* * *

## ✔ ENTRYPOINT

👉 Fixed main command 👉 Cannot be overridden easily

* * *

## ✔ CMD

👉 Default arguments 👉 Can be overridden

* * *

## 👉 Simple Difference:

*   ENTRYPOINT = Main command
    
*   CMD = Optional settings
    

* * *

## 🔹 5. Build & Run Container 🚀

* * *

## ✔ Build Image

```bash
docker build -t django-app .
```

* * *

## ✔ Run Container

```bash
docker run -p 8000:8000 django-app
```

* * *

## ✔ Port Mapping (Important)

👉 `-p 8000:8000`

*   First → Local port
    
*   Second → Container port
    

👉 Access app:

```plaintext
http://localhost:8000
```

* * *

## 🔹 6. AWS Deployment 🌐

* * *

## ✔ Steps:

*   Launch EC2
    
*   Install Docker
    
*   Run container
    

* * *

## ✔ Security Group (Important)

👉 Allow inbound traffic:

*   Port: 8000
    

👉 Otherwise app won’t open

* * *

## 🔹 7. Networking Concept

## 👉 Container runs internally

👉 Port mapping exposes it outside

* * *

## 🔹 8. DevOps Perspective 💡

### 👉 DevOps Engineer must:

*   Understand application flow
    
*   Know dependencies
    
*   Troubleshoot issues
    

* * *

## ✔ Not required:

*   Full developer knowledge
    

## ✔ Required:

*   Basic understanding of apps
    

* * *

## 🔹 9. Real DevOps Workflow

1.  Developer builds Django app
    
2.  DevOps writes Dockerfile
    
3.  Build Docker image
    
4.  Run container
    
5.  Deploy on AWS
    

* * *

## Project Repo link - [https://github.com/hritikranjan1/Docker-Zero-to-Hero.git](https://github.com/hritikranjan1/Docker-Zero-to-Hero.git)

* * *

## Optimize Docker Images (Advanced 🚀)

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/343fb89e-1fb3-46ef-928b-17c91a8b9c27.png align="center")

* * *

## 🔹 1. Problem with Large Docker Images ❌

### 👉 Normal Docker images:

*   Very large (500MB – 1GB+)
    
*   Contain:
    
    *   OS
        
    *   Build tools
        
    *   Extra libraries
        

* * *

### ❌ Issues:

*   Slow deployment
    
*   High storage cost
    
*   Security risks
    

* * *

## 🔹 2. Multi-Stage Docker Builds 🔥

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/e37215c2-6a2b-4842-8eed-3d64f8462bd3.png align="center")

* * *

### ✔ What is it?

👉 Split Dockerfile into **multiple stages**

* * *

## ✔ Idea:

*   Stage 1 → Build application
    
*   Stage 2 → Run application
    

👉 Only copy required files

* * *

✔ Example Flow:

```dockerfile
# Stage 1 (Build)
FROM golang:1.20 AS builder
WORKDIR /app
COPY . .
RUN go build -o app

# Stage 2 (Run)
FROM scratch
COPY --from=builder /app/app /app/app
CMD ["/app/app"]
```

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/2dbe94f0-ae69-40ae-a99d-9e3059bbbd5f.png align="center")

* * *

## ✔ Benefits:

*   Removes unnecessary files
    
*   Reduces image size
    
*   Faster deployment
    

* * *

### 📊 Real Example

*   Without multi-stage → ~861 MB ❌
    
*   With multi-stage → ~150 MB ✔
    

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/d3cb9fad-2b8b-4e27-bd8c-40efba4a7c71.png align="center")

* * *

## 🔹 3. Distroless Images 🔥

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/08b5e723-401c-4401-8183-c6b2c9424651.png align="center")

* * *

### ✔ What is Distroless?

👉 Minimal Docker image

👉 Contains:

*   Only app
    
*   Required runtime
    

* * *

### ❌ Does NOT contain:

*   Shell (bash)
    
*   curl / wget
    
*   package manager
    

* * *

### ✔ Benefits:

*   Very small size
    
*   More secure
    
*   Less attack surface
    

* * *

## 🔹 4. Scratch Image (Extreme Case)

### 👉 `FROM scratch` = Empty image

👉 Only your app exists

* * *

## 📊 Real Result:

*   Final image size → **1.83 MB 😲**
    
*   Reduction → ~800x  
    Project Repo link - [https://github.com/hritikranjan1/Docker-Zero-to-Hero.git](https://github.com/hritikranjan1/Docker-Zero-to-Hero.git)
    

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/b563520a-e3fb-4ba7-80ef-4f1c39c864bd.png align="center")

*   Final image size → **1.21 MB 😲**
    
    ![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/b1771d35-036d-4039-b438-c25fd7f294e9.png align="center")
    

* * *

## 🔹 5. Security Benefits 🔐

* * *

## ✔ Why Distroless is Secure?

*   No unnecessary tools
    
*   Hackers can’t run commands
    
*   Minimal vulnerabilities
    

* * *

### ✔ Compared to Ubuntu:

| Ubuntu Image | Distroless |
| --- | --- |
| Large size | Very small |
| More packages | Minimal |
| More vulnerabilities | Less |

* * *

## 🔹 6. Real DevOps Use Case 💡

👉 In production:

*   Use multi-stage builds
    
*   Use distroless images
    

* * *

## ✔ Result:

*   Faster CI/CD
    
*   Better security
    
*   Lower cost
    

* * *

## 🔹 7. Interview Answer

👉 If asked:

**“How did you optimize Docker images?”**

👉 Answer:

*   Used multi-stage builds
    
*   Removed unnecessary dependencies
    
*   Switched to distroless images
    
*   Reduced size & improved security
    

* * *

## 🔹 8. Real Workflow

1.  Write Dockerfile (multi-stage)
    
2.  Build app in first stage
    
3.  Copy only binary
    
4.  Use distroless image
    
5.  Deploy container
    

* * *

## Docker Volumes & Bind Mounts

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/3eb9619f-4219-428d-9492-ce555fa3a671.png align="center")

* * *

### 🔹 1. The Problem with Containers ❌

👉 Containers are **temporary (ephemeral)**

👉 If container is deleted:

*   Data inside container is also deleted 😢
    

* * *

## ✔ Example:

You run:

```bash
docker run mysql
```

👉 Store database data

But if container is removed:

```bash
docker rm container_id
```

❌ Database data is gone

* * *

## 🔹 2. Solution → Persistent Storage

👉 To save data permanently:

*   Bind Mounts
    
*   Docker Volumes
    

* * *

## 🔹 3. Bind Mounts 📂

* * *

## ✔ What is Bind Mount?

👉 Connect a folder from:

*   Host machine ➡️ Container folder
    

* * *

## ✔ Example:

```bash
docker run -v /home/data:/app/data nginx
```

👉 Meaning:

*   `/home/data` = Host folder
    
*   `/app/data` = Container folder
    

* * *

## ✔ Benefits

*   Easy for development
    
*   Direct access to files
    

* * *

## ❌ Problems

*   Depends on host OS path
    
*   Harder to manage in production
    

* * *

## 🔹 4. Docker Volumes 🔥 (Recommended)

* * *

## ✔ What are Volumes?

👉 Docker-managed storage system

👉 Data exists independently from container

* * *

## ✔ Benefits

*   Persistent storage
    
*   Easy backup
    
*   Portable
    
*   Better for production
    

* * *

## ✔ Key Advantage

👉 Even if container is deleted:

*   Volume data remains safe ✔
    

* * *

## 🔹 5. Volume Commands 🛠️

* * *

## ✔ Create Volume

```bash
docker volume create myvolume
```

* * *

## ✔ List Volumes

```bash
docker volume ls
```

* * *

## ✔ Inspect Volume

```bash
docker volume inspect myvolume
```

* * *

## ✔ Remove Volume

```bash
docker volume rm myvolume
```

* * *

## 🔹 6. Mount Volume to Container

* * *

## ✔ Using `--mount`

```bash
docker run --mount source=myvolume,target=/app/data nginx
```

* * *

## ✔ Meaning:

*   `source` = Docker volume
    
*   `target` = Container directory
    

* * *

## 🔹 7. Verify Volume Connection 🔍

👉 Check container details:

```bash
docker inspect container_id
```

👉 Shows:

*   Mounted volumes
    
*   Paths
    

* * *

## 🔹 8. Bind Mount vs Volume 🔥

| Feature | Bind Mount | Volume |
| --- | --- | --- |
| Managed by Docker | ❌ | ✔ |
| Easy for local dev | ✔ | ✔ |
| Production ready | ❌ | ✔ |
| Portable | ❌ | ✔ |

* * *

## 🔹 9. Real DevOps Use Cases 💡

* * *

## ✔ Databases

*   MySQL
    
*   PostgreSQL
    

👉 Data must survive container deletion

* * *

## ✔ Logs

Store application logs permanently

* * *

## ✔ Shared Data

Multiple containers can share same volume

* * *

## 🔹 10. Best Practice 🚀

👉 Use:

*   Bind Mounts → Development
    
*   Volumes → Production
    

* * *

## 🔹 11. Real Workflow

1.  Create volume
    
2.  Attach to container
    
3.  Store data
    
4.  Delete container
    
5.  Data still safe in volume ✔
    

* * *

## 📘Docker Networking

👉 *Bridge vs Host vs Overlay Networks | Secure Containers with Custom Bridge Network*

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/46c78248-687a-4908-8232-8e7803a89946.png align="center")

* * *

## 🔹 1. Introduction to Docker Networking 🌐

When we run multiple containers, they often need to communicate with each other.

### 👉 Example:

*   Frontend container
    
*   Backend container
    
*   Database container
    

All these containers need networking to exchange data.

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/f2d75aaf-c6a5-4dc3-8fec-48612fcaef37.png align="center")

* * *

## 🔹 2. Why Docker Networking is Important? 🔥

Docker networking helps in:

✔ Communication between containers ✔ Isolation of applications ✔ Security ✔ Connecting containers to internet ✔ Multi-container applications

* * *

## 💡 Real Example

Imagine:

*   Login Service Container
    
*   Payment Service Container
    
*   Database Container
    

👉 Login service should talk to database 👉 Finance service should remain isolated for security

This is where Docker networking becomes important.

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/98ba996a-d3b1-40d7-9f77-2e3f6d1e8fc5.png align="center")

* * *

## 🔹 3. Types of Docker Networks

Docker mainly provides:

1.  Bridge Network
    
2.  Host Network
    
3.  Overlay Network
    

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/61c6a414-e5a5-4828-b8aa-0525670fdba0.png align="center")

* * *

## 🔹 4. Bridge Network (Default Network) 🔥

* * *

## ✔ What is Bridge Network?

When Docker is installed, it automatically creates a virtual network called:

```id="0kq2nm"
docker0
```

This acts like a bridge between containers.

* * *

## ✔ How it Works

Containers connected to the same bridge network can communicate with each other.

* * *

## ✔ Default Behavior

When you run containers normally:

```bash
docker run nginx
```

Docker automatically connects them to the default bridge network.

* * *

## ✔ Benefits

✅ Easy setup ✅ Good for single-host communication ✅ Containers can talk to each other

* * *

## ❌ Limitation

*   Less secure
    
*   All containers on same bridge may communicate
    

* * *

## 🔹 5. Host Network 🔥

* * *

## ✔ What is Host Networking?

In host networking:

👉 Container directly uses the host machine’s network.

* * *

## ✔ Meaning

Container does NOT get its own isolated network.

Instead:

```id="9ps4mg"
Container uses Host IP directly
```

* * *

## ✔ Command Example

```bash
docker run --network=host nginx
```

* * *

## ✔ Advantages

✅ Faster performance ✅ No bridge overhead

* * *

## ❌ Disadvantages

❌ Least secure ❌ No isolation ❌ Port conflicts possible

* * *

## 🔹 6. Overlay Network 🔥

* * *

## ✔ What is Overlay Network?

Overlay networking is used when containers run on:

👉 Multiple servers (multi-host)

* * *

## ✔ Used In:

*   Kubernetes
    
*   Docker Swarm
    

* * *

## ✔ Purpose

Allows containers on different servers to communicate.

* * *

## 💡 Example

Container A → Server 1 Container B → Server 2

Overlay network connects them together.

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/a3372f44-93a3-4cde-809d-5fd3a2db564a.png align="center")

* * *

## 🔹 7. Custom Bridge Network 🔥 (Very Important)

* * *

## ✔ Why Create Custom Network?

Default bridge allows many containers to communicate.

Sometimes we need:

*   Better isolation
    
*   More security
    

* * *

## ✔ Example Use Case

Finance application should not communicate with:

*   Login service
    
*   Public applications
    

* * *

## 🔹 8. Create Custom Bridge Network

* * *

## ✔ Command

```bash
docker network create secure-network
```

* * *

## ✔ Verify Networks

```bash
docker network ls
```

* * *

## 🔹 9. Run Container in Custom Network

* * *

## ✔ Example

```bash
docker run --network=secure-network nginx
```

Now this container belongs only to:

```id="gxj6z7"
secure-network
```

* * *

## 🔹 10. Benefits of Custom Bridge Networks

✅ Better security ✅ Better isolation ✅ Easier communication control ✅ Containers communicate using names

* * *

## 🔹 11. Container Communication Demo

* * *

## ✔ Same Network

Containers can communicate.

* * *

## ✔ Different Networks

Containers cannot communicate unless connected manually.

* * *

## 🔹 12. Check Docker Networks

* * *

## ✔ List Networks

```bash
docker network ls
```

* * *

## ✔ Inspect Network

```bash
docker network inspect secure-network
```

Shows:

*   Connected containers
    
*   Network details
    
*   IP addresses
    

* * *

## 🔹 13. Real DevOps Use Cases 💡

* * *

## ✔ Microservices

Different services communicate securely.

* * *

## ✔ Security Isolation

Sensitive apps separated from public apps.

* * *

## ✔ Kubernetes Networking

Overlay networks used heavily in clusters.

* * *

## 🔹 14. Bridge vs Host vs Overlay 🔥

| Feature | Bridge | Host | Overlay |
| --- | --- | --- | --- |
| Isolation | Medium | Low | High |
| Multi-host | ❌ | ❌ | ✔ |
| Security | Good | Weak | Strong |
| Performance | Good | Best | Moderate |
| Use Case | Single Host | High Speed | Kubernetes |

* * *

## 🔹 15. Important Interview Points 🔥

* * *

## ✔ Why custom bridge network?

👉 Better isolation and security.

* * *

## ✔ Why host network is risky?

👉 Container directly uses host network.

* * *

## ✔ Where is overlay network used?

👉 Kubernetes & Docker Swarm.

* * *

## 🔹 16. Real Workflow Example 🚀

1.  Create custom network
    
2.  Run frontend container
    
3.  Run backend container
    
4.  Allow only required communication
    
5.  Secure sensitive services
    

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

✅ Share it with your network  
✅ Bookmark it for future reference  
✅ Follow for more DevOps, AI, Cloud, Cybersecurity, and Software Engineering content

Thank you for reading and being part of this learning journey.

**Keep Learning. Keep Building. Keep Growing. 🚀**