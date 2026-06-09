---
title: "Week 9.4 – Networking Fundamentals & OSI Model Explained"
seoTitle: "Networking Fundamentals & OSI Model Explained for DevOps"
seoDescription: "Learn IP Addressing, Subnets, CIDR, Ports, DNS, TCP/IP, and the OSI Model with real-world examples for DevOps and Cloud Engineers."
datePublished: 2026-06-09T15:24:28.822Z
cuid: cmq6sj3yj00000bkv5sj44srv
slug: week-9-4-networking-fundamentals-osi-model-explained
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/5bcf8a77-81f8-499c-b391-c0955a7aa1fd.png
tags: linux, kubernetes, cloud-computing, devops, networking, linux-for-beginners, devops-articles

---

# 🌐 Networking Concepts Made Easy | Complete Beginner Guide to IP Address, Subnets, CIDR & Ports 🚀

Networking is one of the most important skills for DevOps Engineers, Cloud Engineers, System Administrators, and Software Developers.

Whenever you open a website, connect to a server, use Docker, deploy Kubernetes applications, or access cloud services, networking is working behind the scenes.

Understanding networking fundamentals helps you troubleshoot issues faster and build reliable systems.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/726ef3ae-1f28-4480-bc92-dac19d6b5915.png align="center")

# 📘 What is Networking?

Networking is the process of connecting multiple devices so they can communicate and share information.

Examples:

*   Accessing Google from your laptop.
    
*   Connecting your phone to Wi-Fi.
    
*   Communicating between Kubernetes Pods.
    
*   Connecting an application to a database server.
    

Without networking, devices cannot exchange information.

* * *

# 🤔 Why Should DevOps Engineers Learn Networking?

In real-world production environments, many issues are network-related.

Examples:

*   Application cannot reach the database.
    
*   Website is inaccessible.
    
*   Kubernetes Pods cannot communicate.
    
*   Load Balancer is not routing traffic.
    
*   DNS resolution fails.
    

Networking knowledge helps engineers quickly identify and solve these problems.

* * *

# 🔹 What is an IP Address? 📍

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/1ca6ac4f-cf31-4c6c-96da-3a2fcaef8640.png align="center")

An **IP Address (Internet Protocol Address)** is a unique identifier assigned to every device connected to a network.

Just like every house has a unique address, every device on a network requires a unique IP address.

Examples:

```text
192.168.1.10
172.16.0.5
10.0.0.20
```

Without an IP address, devices cannot find or communicate with each other.

* * *

# 🏠 Real-Life Example of an IP Address

Imagine sending a courier package.

The courier company needs:

*   Sender Address
    
*   Receiver Address
    

Similarly, when data travels across a network:

*   Source IP = Sender Address
    
*   Destination IP = Receiver Address
    

This allows information to reach the correct destination.

* * *

# 🔹 Understanding IPv4

The most commonly used IP version today is **IPv4**.

Example:

```text
192.168.1.100
```

IPv4 contains:

```text
192 . 168 . 1 . 100
```

Four sections called **octets**.

Each octet ranges from:

```text
0 - 255
```

* * *

# 🤔 Why Can an Octet Only Be Between 0 and 255?

Each octet contains 8 bits.

Example:

```text
11111111
```

Binary value:

```text
255
```

Therefore:

```text
Minimum = 0
Maximum = 255
```

This is why IPv4 addresses always use numbers between 0 and 255.

* * *

# 🔹 Public IP vs Private IP

## 🌍 Public IP Address

A public IP is accessible from the internet.

Example:

```text
49.37.102.10
```

Used by:

*   Websites
    
*   Cloud servers
    
*   Load Balancers
    

* * *

## 🔒 Private IP Address

Private IPs are used within internal networks.

Examples:

```text
192.168.x.x
10.x.x.x
172.16.x.x - 172.31.x.x
```

Used by:

*   Home Wi-Fi networks
    
*   Corporate networks
    
*   Kubernetes clusters
    
*   Cloud VPCs
    

Private IPs cannot be accessed directly from the internet.

* * *

# 🔹 What is a Subnet? 🏘️

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/13697a2f-1503-4171-887b-604c9f772baf.png align="center")

A **Subnet (Sub Network)** is a smaller network created inside a larger network.

Instead of placing all devices in one large network, organizations divide them into smaller segments.

Benefits:

✅ Better Security

✅ Better Isolation

✅ Better Management

✅ Improved Performance

* * *

# 🏢 Real-World Example of Subnets

Imagine a company with multiple departments:

*   HR
    
*   Finance
    
*   Development
    
*   Security
    

Instead of allowing everyone access to everything, each department gets its own subnet.

Example:

```text
HR Network        → 10.0.1.0/24
Finance Network   → 10.0.2.0/24
Development       → 10.0.3.0/24
```

This improves security and organization.

* * *

# 🔹 Public vs Private Subnets

## 🌍 Public Subnet

Resources inside a public subnet can directly access the internet.

Examples:

*   Load Balancers
    
*   Web Servers
    
*   Bastion Hosts
    

* * *

## 🔒 Private Subnet

Resources inside a private subnet are hidden from the internet.

Examples:

*   Databases
    
*   Internal Applications
    
*   Kubernetes Worker Nodes
    

This improves security.

* * *

# 🔹 What is CIDR? 📏

CIDR stands for:

**Classless Inter-Domain Routing**

CIDR defines the size of an IP address range.

Example:

```text
192.168.1.0/24
```

The number after "/" determines how many IP addresses are available.

* * *

# 🔹 Common CIDR Ranges

| CIDR | Total IPs |
| --- | --- |
| /24 | 256 |
| /25 | 128 |
| /26 | 64 |
| /27 | 32 |
| /28 | 16 |
| /29 | 8 |

* * *

# 🧮 CIDR Example

Example:

```text
192.168.1.0/24
```

Contains:

```text
192.168.1.0
to
192.168.1.255
```

Total:

```text
256 IP Addresses
```

* * *

# 🔹 Why CIDR is Important?

CIDR helps cloud engineers allocate network ranges efficiently.

Examples:

### AWS VPC

```text
10.0.0.0/16
```

### Public Subnet

```text
10.0.1.0/24
```

### Private Subnet

```text
10.0.2.0/24
```

This allows proper network planning.

* * *

# 🔹 What is a Port? 🚪

An IP address identifies a machine.

A **Port** identifies a specific application running on that machine.

Think of it this way:

*   IP Address = Apartment Building
    
*   Port = Apartment Number
    

Without ports, the operating system wouldn't know which application should receive incoming traffic.

* * *

# 🖥️ Real-Life Example

Suppose a server has IP:

```text
192.168.1.10
```

Running:

*   Website
    
*   Database
    
*   SSH Service
    

Each application uses a different port.

| Service | Port |
| --- | --- |
| HTTP | 80 |
| HTTPS | 443 |
| SSH | 22 |
| MySQL | 3306 |
| PostgreSQL | 5432 |
| Jenkins | 8080 |
| Kubernetes API | 6443 |

* * *

# 🔹 Why Ports Are Important?

Ports allow multiple applications to run on the same server.

Example:

```text
192.168.1.10:80
```

Website

```text
192.168.1.10:22
```

SSH Access

```text
192.168.1.10:3306
```

MySQL Database

Same IP, different applications.

* * *

# 🌐 Networking in Kubernetes

Networking concepts become even more important in Kubernetes.

Examples:

*   Pod IP Addresses
    
*   ClusterIP Services
    
*   NodePort Services
    
*   Ingress Controllers
    
*   Load Balancers
    

Without networking fundamentals, Kubernetes becomes difficult to understand.

* * *

# ☁️ Networking in Cloud Platforms

Cloud providers heavily use networking concepts.

Examples:

### AWS

*   VPC
    
*   Subnets
    
*   Security Groups
    
*   Route Tables
    
*   NAT Gateway
    

### Azure

*   Virtual Networks
    
*   Network Security Groups
    

### Google Cloud

*   VPC Networks
    
*   Firewall Rules
    

Networking is the backbone of cloud infrastructure.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/4429c6d5-f5a6-45a7-b75f-51d74a55e745.png align="center")

# 🎯 Interview Questions & Answers

### Q1. What is an IP Address?

An IP Address is a unique identifier assigned to a device on a network.

* * *

### Q2. What is the difference between Public and Private IP?

Public IPs are accessible from the internet, while Private IPs are used only within internal networks.

* * *

### Q3. What is a Subnet?

A subnet is a smaller network created from a larger network to improve security and management.

* * *

### Q4. What is CIDR?

CIDR (Classless Inter-Domain Routing) defines the size of an IP address range.

* * *

### Q5. What does /24 mean?

A /24 network contains 256 IP addresses.

* * *

### Q6. What is a Port?

A port is a logical endpoint used by applications to send and receive network traffic.

* * *

### Q7. What port does SSH use?

```text
22
```

* * *

### Q8. What port does HTTPS use?

```text
443
```

* * *

### Q9. Why are subnets important?

Subnets provide security, isolation, and better network organization.

* * *

### Q10. Why should DevOps Engineers learn networking?

Because most cloud, Kubernetes, Docker, and production system issues involve networking concepts.

* * *

# 🌐 OSI Model Simplified – Complete Beginner Guide for DevOps Engineers

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/068ca427-539b-48ce-a01b-673efbd2747c.png align="center")

The OSI (Open Systems Interconnection) Model is a framework that explains how data travels from one device to another over a network. It helps us understand networking concepts in a structured way and makes troubleshooting much easier.

Whenever you open a website, send an email, watch a YouTube video, or use any internet service, data passes through multiple layers before reaching its destination. The OSI model divides this entire process into seven layers.

For DevOps Engineers, Cloud Engineers, System Administrators, and Network Engineers, understanding the OSI model is extremely important because most real-world troubleshooting involves identifying which layer is causing an issue.

* * *

# 🤔 Why Do We Need the OSI Model?

Imagine sending a package from one city to another.

*   The package is packed.
    
*   Address information is added.
    
*   It is transported through multiple routes.
    
*   It finally reaches the recipient.
    

Network communication works similarly.

The OSI model breaks this communication process into smaller layers so that each layer has a specific responsibility.

### Benefits of the OSI Model

✅ Easier troubleshooting

✅ Better understanding of network communication

✅ Standardized communication process

✅ Helps different vendors build compatible systems

✅ Useful for DevOps, Cloud, and Security Engineers

* * *

# 🌍 What Happens When You Open a Website?

Let's assume you type:

```bash
https://www.google.com
```

inside your browser.

Before the website loads, several processes happen behind the scenes.

* * *

# 🔹 Step 1: DNS Resolution

Computers do not understand domain names.

They communicate using IP addresses.

When you enter:

```bash
google.com
```

the browser first asks a DNS server:

> "What is the IP address of google.com?"

DNS then returns something like:

```bash
142.250.183.14
```

Now the browser knows where to send the request.

* * *

# 🔹 Step 2: TCP Three-Way Handshake

Before sending actual data, the client and server establish a connection.

This process is called the TCP Three-Way Handshake.

### Step 1: SYN

Client sends:

```bash
SYN
```

Meaning:

> "Can we start communication?"

### Step 2: SYN-ACK

Server replies:

```bash
SYN + ACK
```

Meaning:

> "Yes, I'm ready."

### Step 3: ACK

Client responds:

```bash
ACK
```

Meaning:

> "Connection established."

Now communication can begin.

* * *

# 🏗️ The 7 Layers of the OSI Model

The OSI model consists of seven layers.

```text
Layer 7 - Application
Layer 6 - Presentation
Layer 5 - Session
Layer 4 - Transport
Layer 3 - Network
Layer 2 - Data Link
Layer 1 - Physical
```

A simple way to remember them:

```text
Application
Presentation
Session
Transport
Network
Data Link
Physical
```

* * *

# 🔹 Layer 7 – Application Layer

The Application Layer is the closest layer to the user.

This is where applications interact with the network.

### Examples

*   Web Browsers
    
*   Gmail
    
*   WhatsApp
    
*   Slack
    
*   Microsoft Teams
    
*   APIs
    

### Common Protocols

```bash
HTTP
HTTPS
FTP
SMTP
DNS
```

### Real-Life Example

When you open Google Chrome and visit a website, the request starts at the Application Layer.

* * *

# 🔹 Layer 6 – Presentation Layer

This layer handles data formatting and encryption.

Its job is to ensure data is presented in a format both systems can understand.

### Responsibilities

*   Data formatting
    
*   Data conversion
    
*   Compression
    
*   Encryption
    
*   Decryption
    

### Example

When HTTPS encrypts your data before sending it over the internet, the Presentation Layer is involved.

* * *

# 🔹 Layer 5 – Session Layer

The Session Layer creates, manages, and terminates communication sessions.

Think of it as a manager that keeps track of conversations between devices.

### Responsibilities

*   Session creation
    
*   Session maintenance
    
*   Session termination
    

### Example

When you log in to a website and remain logged in while browsing multiple pages, the Session Layer helps maintain that session.

* * *

# 🔹 Layer 4 – Transport Layer

The Transport Layer ensures reliable communication between devices.

This layer divides large data into smaller segments.

### Main Protocols

```bash
TCP
UDP
```

* * *

## TCP (Transmission Control Protocol)

TCP guarantees delivery.

### Features

✅ Reliable

✅ Error checking

✅ Ordered delivery

### Examples

*   HTTPS
    
*   Banking Applications
    
*   Online Shopping
    

* * *

## UDP (User Datagram Protocol)

UDP focuses on speed rather than reliability.

### Features

✅ Fast

✅ Lightweight

❌ No delivery guarantee

### Examples

*   Video Streaming
    
*   Gaming
    
*   Voice Calls
    

* * *

# 🔹 Layer 3 – Network Layer

The Network Layer handles routing.

It determines how packets travel from source to destination.

### Responsibilities

*   Routing
    
*   Logical addressing
    
*   Path selection
    

### Uses IP Addresses

Example:

```bash
192.168.1.10
```

### Devices

*   Routers
    

### Real-Life Example

Google receives millions of requests daily.

Routers determine the best path for your packet to reach Google's servers.

* * *

# 🔹 Layer 2 – Data Link Layer

The Data Link Layer handles communication within the same local network.

Instead of IP addresses, it uses MAC addresses.

### Responsibilities

*   Framing
    
*   Error detection
    
*   MAC addressing
    

### Devices

*   Switches
    

### Example MAC Address

```bash
00:1A:2B:3C:4D:5E
```

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/619080af-1c4b-44e3-8e40-98561e152351.gif align="center")

# 🔹 Layer 1 – Physical Layer

This is the lowest layer.

It handles the actual transmission of data.

### Examples

*   Network cables
    
*   Fiber optic cables
    
*   Wireless signals
    
*   Electrical signals
    

### Responsibilities

*   Sending bits
    
*   Receiving bits
    
*   Physical connectivity
    

Without this layer, no data can move.

* * *

# 📦 Data Encapsulation Explained

As data moves down the OSI model, each layer adds its own information.

```text
Application Data
↓
Segments
↓
Packets
↓
Frames
↓
Bits
```

When data reaches the destination, the reverse process occurs.

This is called:

```text
Decapsulation
```

* * *

# 🔄 Real-Life Example of the OSI Model

Suppose you watch a YouTube video.

### Application Layer

You click Play.

### Presentation Layer

Video data is compressed and encrypted.

### Session Layer

Session is established between your device and YouTube.

### Transport Layer

Video data is divided into segments.

### Network Layer

Packets are routed through the internet.

### Data Link Layer

Frames are transferred between devices.

### Physical Layer

Signals travel through cables and wireless networks.

Finally, the video appears on your screen.

* * *

# 🆚 OSI Model vs TCP/IP Model

In real-world networking, the TCP/IP model is more commonly used.

### OSI Model

```text
7 Layers
```

### TCP/IP Model

```text
Application
Transport
Internet
Network Access
```

TCP/IP combines:

```text
Application
Presentation
Session
```

into a single Application Layer.

* * *

# 💡 Why DevOps Engineers Should Learn the OSI Model?

In DevOps, networking issues happen frequently.

Understanding the OSI model helps identify where problems occur.

### Common Troubleshooting Examples

| Problem | OSI Layer |
| --- | --- |
| Website not opening | Layer 7 |
| SSL Certificate Error | Layer 6 |
| Session Timeout | Layer 5 |
| TCP Connection Failure | Layer 4 |
| Routing Issue | Layer 3 |
| Switch Failure | Layer 2 |
| Cable Disconnected | Layer 1 |

* * *

# 🎯 Key Takeaways

*   OSI stands for Open Systems Interconnection.
    
*   It divides networking into seven layers.
    
*   DNS resolution and TCP handshake happen before communication begins.
    
*   Each layer has a specific responsibility.
    
*   Layer 7 is closest to users, while Layer 1 handles physical transmission.
    
*   TCP/IP is the practical networking model used today.
    
*   Understanding the OSI model helps DevOps engineers troubleshoot network issues quickly and efficiently.
    

🚀 Once you understand the OSI model, networking becomes much easier because you can identify exactly where a problem is occurring instead of guessing.

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/96446282-491f-4c19-bc6b-a0528c217450.png align="center")

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
|✅ Bookmark it for future reference  
✅ Follow for more DevOps, AI, Cloud, Cybersecurity, and Software Engineering content

Thank you for reading and being part of this learning journey.

**Keep Learning. Keep Building. Keep Growing. 🚀**