---
title: "🐧 Linux for DevOps: Complete Beginner to Advanced Guide with Commands, Networking, Users, Permissions, AWK, SED, LVM & More"
seoTitle: "Linux for DevOps: Complete Guide with Commands"
seoDescription: "Learn Linux for DevOps with essential commands, networking, users, permissions, AWK, SED, storage, LVM, SSH, troubleshooting, and more."
datePublished: 2026-09-20T05:07:04.528Z
cuid: cmu9ctv2q00000agm1s8ra7g7
slug: linux-for-devops-guide
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/73dbe2d2-84d3-431f-9266-d86ae8763bdd.png
tags: linux, devops, linux-for-beginners, linux-kernel, linux-basics, devops-articles, linux-commands, linux-file-system, devops-journey, linux-file-permissions, system-administration, linux-administration

---

If you are starting your DevOps journey, you will quickly realize that many tools and platforms run on Linux.

For example:

```text
AWS EC2
Docker
Kubernetes
Jenkins
Nginx
Apache
Terraform
Ansible
Prometheus
Grafana
Git
```

All of these commonly involve Linux environments.

But many beginners start learning DevOps tools directly without properly understanding Linux.

That creates problems later.

You may know how to create a Docker container, but if you don't understand:

```text
Linux processes
File permissions
Users and groups
Networking
SSH
Disk management
Logs
File systems
Shell commands
```

troubleshooting becomes difficult.

This guide is designed to solve that problem.

We will start from the basics and gradually move toward **advanced Linux commands and storage management**, with practical examples throughout.

* * *

# 📌 What You Will Learn

In this complete Linux guide, we will cover:

1.  What is the Internet?
    
2.  How does the Internet work?
    
3.  What are servers?
    
4.  Data centers
    
5.  Optical fiber and submarine cables
    
6.  Client-server architecture
    
7.  What is Linux?
    
8.  Linux vs Windows
    
9.  Linux distributions
    
10.  Linux server
     
11.  Setting up a Linux server
     
12.  Connecting to a Linux server using SSH
     
13.  Linux terminal
     
14.  Basic Linux commands
     
15.  Directory structure
     
16.  File and directory management
     
17.  Creating files
     
18.  Copying files
     
19.  Moving and renaming files
     
20.  Deleting files
     
21.  Hard links
     
22.  Soft links
     
23.  Text processing
     
24.  `cat`
     
25.  `tee`
     
26.  `head`
     
27.  `tail`
     
28.  `sort`
     
29.  `vi/vim`
     
30.  Users and groups
     
31.  Root user
     
32.  `sudo`
     
33.  Creating users
     
34.  Password management
     
35.  Switching users
     
36.  Deleting users
     
37.  Groups
     
38.  Linux file permissions
     
39.  Read, Write, Execute
     
40.  Owner, Group, Others
     
41.  Numeric permissions
     
42.  `chmod`
     
43.  File transfer
     
44.  `scp`
     
45.  `rsync`
     
46.  Linux networking commands
     
47.  `ip`
     
48.  `ping`
     
49.  `netstat`
     
50.  `ss`
     
51.  `traceroute`
     
52.  `arp`
     
53.  `curl`
     
54.  `wget`
     
55.  DNS basics
     
56.  `grep`
     
57.  `find`
     
58.  `awk`
     
59.  `sed`
     
60.  Linux storage
     
61.  Block devices
     
62.  Mounting
     
63.  `lsblk`
     
64.  `df`
     
65.  `du`
     
66.  Filesystems
     
67.  `mkfs`
     
68.  `mount`
     
69.  `umount`
     
70.  LVM
     
71.  Physical Volume
     
72.  Volume Group
     
73.  Logical Volume
     
74.  LVM resizing
     
75.  DevOps use cases
     
76.  Linux troubleshooting
     
77.  Common mistakes
     
78.  Linux cheat sheet
     
79.  Linux interview questions
     

* * *

# 1\. 🌐 What Is the Internet?

Before understanding Linux servers, let's understand something more fundamental:

> **What actually happens when you open a website?**

Suppose you open:

```text
https://example.com
```

Your browser needs to communicate with a server somewhere on the Internet.

A simplified flow is:

```text
Your Computer
      |
      v
   Router
      |
      v
 Internet
      |
      v
 DNS
      |
      v
Web Server
      |
      v
 Website Response
      |
      v
 Your Browser
```

The Internet is essentially a massive network connecting computers and networks around the world.

* * *

# 2\. 🌍 How Does the Internet Work?

The Internet is not one single machine.

It is a network of:

*   Computers
    
*   Servers
    
*   Routers
    
*   Switches
    
*   Data centers
    
*   Internet Service Providers
    
*   Fiber-optic networks
    
*   Submarine cables
    
*   Wireless networks
    

When you access a website, data travels through multiple networks before reaching the destination.

A simplified example:

```text
Laptop
  ↓
Wi-Fi Router
  ↓
ISP
  ↓
Internet Backbone
  ↓
Data Center
  ↓
Server
```

The response travels back through the network.

* * *

# 3\. 🌊 How Does Internet Data Travel Between Countries?

A common misconception is:

> "Most Internet traffic travels through satellites."

In reality, a huge amount of international Internet traffic travels through **fiber-optic submarine cables** laid across the ocean floor.

![Image](https://images.openai.com/static-rsc-4/5UKON52-JO66tP31PVZL0wyM9Sdr96evCj1TkUbGjuDoSaF8IcIf_cI4XiwbWo4sELwMvY1MJdl-qDa1NZ7jMgCiRKKzWID_vQXA8l8agihQps7ctGl26SOUvW6zahtVWDRaWQpFcnUGkdsR9mGKd3seSvX1yO5cUOWBOn2tZTnofdm2ZAXVIN62elGEv-5R?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/NjY8Bm_Zdw4WGmWaNrn3q48EcEBmMXeCWC9COx6CihNKfMKEbdmEnAMd-RHCxEmT4dKonmuDHvFIjVGGgpacgPupwPEvH6YKpWhTyIzCylUKVx6IZNJVIEDuU7alHKynY9sPQQ-hps8mrnAgY54d4uqvfFfNQEo_Oj79oT-JYGkv7mrOGaJulLzuWgtfnbpx?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/MMc3DADRkr41ZVT3rKe8opZ34QEq9xteahQo5dg-3520A85az2U6agh5_BORGAYNNU3CdEdZzmrtRMsQM66aow7CS48YjUh9cRA7O1FmrtK6kGvFsdTr1wxsRpAj-1Ym9mgazCrDor7K467HEV5lQZUJts4j59mNUVnY968mrGfe9525Vp9hV3N9peALSn_O?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/3bGi8gLgHLrUKzzVDDmKkXGXKsT5TEWG5FLMaQLMChp5Imc2smp330YmtlOTFqTbr-9r2Oe4GKnWcBbM369YcLd2Vk7KbmXejTxIUCYlE-Rr0lvNATab6rSV6kGEdAZzlw8uNFQdBtg0tskE2wAxbZT9XiuHLOxQP_OFsh4kQwVbzjYOLNyMJCF8RaRNfIvN?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/tZ6oUn9IDUx0c6cDFwf5b6DBEHweNbV6Udozl1UZh-aueWA0z-hkWkn5zRS8WKYkRtINXtwuICar9ZQnvJXESaKge2Zw0DeXl_2W7alWpIAwNepNxyQhK8RT3N6aRB1J0Nf4u68Mkylrycp9Jjp6EOBJjL-Kcoi_0wgaUhcmhUSJDA41pZEfAGEAjp0qDxO2?purpose=fullsize align="center")

These cables connect different continents.

For example:

```text
Asia
 |
 | Submarine Cable
 |
Europe
```

or:

```text
India
  |
  ↓
Undersea Cable
  |
  ↓
Singapore
  |
  ↓
United States
```

These fiber-optic cables transmit data using light.

* * *

# 4\. 🏢 What Is a Data Center?

A **data center** is a facility containing computing infrastructure.

It can contain:

*   Servers
    
*   Storage systems
    
*   Network equipment
    
*   Power systems
    
*   Cooling systems
    
*   Security systems
    

A simplified data center:

```text
             DATA CENTER

 ┌─────────────────────────────┐
 │                             │
 │  Server  Server  Server     │
 │                             │
 │  Server  Server  Server     │
 │                             │
 │  Storage  Network Equipment │
 │                             │
 └─────────────────────────────┘
```

Cloud providers such as AWS operate large numbers of data centers around the world.

* * *

# 5\. 🖥️ What Is a Server?

A **server is a computer that provides services or resources to other computers.**

For example:

```text
Web Server
Database Server
File Server
DNS Server
Mail Server
Application Server
```

Suppose you open a website.

Your browser acts as a client:

```text
Client
  |
  | HTTP Request
  v
Web Server
  |
  | HTTP Response
  v
Client
```

This is called the **client-server model**.

* * *

# 6\. 🐧 What Is Linux?

Linux is an open-source operating-system family built around the **Linux kernel**.

The Linux kernel is responsible for interacting with hardware and providing core operating-system functionality.

In everyday DevOps discussions, when people say "Linux," they often mean a complete Linux distribution such as:

```text
Ubuntu
Debian
Rocky Linux
AlmaLinux
Fedora
RHEL
Amazon Linux
```

* * *

# 7\. Linux Kernel vs Linux Distribution

These terms are often confused.

### Linux Kernel

The kernel is the core component.

It manages things such as:

*   CPU
    
*   Memory
    
*   Processes
    
*   Devices
    
*   Networking
    
*   System calls
    

### Linux Distribution

A distribution combines the Linux kernel with other software.

For example:

```text
Ubuntu
   |
   +── Linux Kernel
   +── GNU utilities
   +── Package Manager
   +── Shell
   +── System utilities
   +── Applications
```

* * *

# 8\. Why Is Linux Important for DevOps?

Linux is extremely important in DevOps because many:

*   Cloud servers
    
*   Containers
    
*   Kubernetes nodes
    
*   CI/CD systems
    
*   Web servers
    
*   Databases
    
*   Monitoring systems
    

run on Linux.

A typical DevOps environment might look like:

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ↓
Linux Server
   ↓
Docker
   ↓
Kubernetes
   ↓
Application
```

So Linux knowledge becomes the foundation for many DevOps tasks.

* * *

# 9\. Popular Linux Distributions

Some popular distributions include:

| Distribution | Common Usage |
| --- | --- |
| Ubuntu | Servers, cloud, beginners |
| Debian | Servers, stability |
| RHEL | Enterprise |
| Rocky Linux | Enterprise-compatible environments |
| AlmaLinux | Enterprise-compatible environments |
| Fedora | Modern Linux development |
| Amazon Linux | AWS environments |

For beginners, **Ubuntu Server** is a very good starting point.

* * *

# 10\. Linux Server

A Linux server is simply a server running a Linux distribution.

For example:

```text
AWS EC2
   ↓
Ubuntu Server
   ↓
Nginx
   ↓
Website
```

or:

```text
AWS EC2
   ↓
Ubuntu
   ↓
Docker
   ↓
Application Container
```

* * *

# 11\. Setting Up a Linux Server

You can practice Linux using:

### Local Machine

Install Linux using:

*   VirtualBox
    
*   VMware
    
*   WSL
    

### Cloud

Create a virtual server using:

*   AWS EC2
    
*   Azure VM
    
*   Google Cloud VM
    

For DevOps practice, cloud VMs are especially useful because they simulate real server environments.

* * *

# 12\. Connecting to a Linux Server Using SSH

SSH stands for:

> **Secure Shell**

It allows you to securely connect to a remote machine.

Example:

```bash
ssh username@server-ip
```

For example:

```bash
ssh ubuntu@203.0.113.10
```

With an SSH private key:

```bash
ssh -i my-key.pem ubuntu@203.0.113.10
```

The general flow is:

```text
Your Laptop
     |
     | SSH
     ↓
Internet
     |
     ↓
Linux Server
```

* * *

# 13\. Linux Terminal

After connecting to a Linux server, you normally interact with the system through the terminal.

Example:

```bash
ubuntu@server:~$
```

This is called a **shell prompt**.

You can execute commands such as:

```bash
pwd
ls
cd
mkdir
touch
cp
mv
rm
```

* * *

# 14\. What Is a Shell?

A shell is a program that provides a command-line interface for interacting with the operating system.

Popular shells include:

```text
Bash
Zsh
Fish
```

Bash is extremely common on Linux systems.

Example:

```bash
echo "Hello Linux"
```

The shell interprets the command and asks the operating system to perform the requested operation.

* * *

# 15\. Linux Basic Commands

Let's start with the most important commands.

* * *

## `pwd`

`pwd` means:

> **Print Working Directory**

It tells you where you currently are.

```bash
pwd
```

Example:

```text
/home/ubuntu
```

* * *

# 16\. `ls`

`ls` displays files and directories.

```bash
ls
```

Example:

```text
app
backup
file.txt
logs
```

### Detailed listing

```bash
ls -l
```

### Show hidden files

```bash
ls -a
```

### Combine options

```bash
ls -la
```

* * *

# 17\. Understanding `ls -l`

Example:

```text
-rwxr-xr-- 1 ubuntu developers 1200 Sep 10 script.sh
```

This contains information about:

```text
Permissions
Links
Owner
Group
Size
Date
Filename
```

We will understand permissions in detail later.

* * *

# 18\. `cd`

`cd` means:

> **Change Directory**

Example:

```bash
cd /var/log
```

Go back one directory:

```bash
cd ..
```

Go to home directory:

```bash
cd ~
```

Return to the previous directory:

```bash
cd -
```

* * *

# 19\. `mkdir`

`mkdir` creates a directory.

```bash
mkdir projects
```

Create nested directories:

```bash
mkdir -p devops/docker/project
```

* * *

# 20\. `touch`

`touch` can create an empty file.

```bash
touch app.txt
```

Create multiple files:

```bash
touch file1.txt file2.txt file3.txt
```

It can also update file timestamps when used on an existing file.

* * *

# 21\. `cat`

`cat` displays file contents.

```bash
cat app.txt
```

Example:

```text
Hello Linux
Welcome to DevOps
```

You can also concatenate files:

```bash
cat file1.txt file2.txt
```

* * *

# 22\. `cp`

`cp` means:

> **Copy**

Copy a file:

```bash
cp app.txt backup.txt
```

Copy to another directory:

```bash
cp app.txt /tmp/
```

Copy a directory recursively:

```bash
cp -r project /backup/
```

The `-r` option is required for recursively copying directories.

* * *

# 23\. `mv`

`mv` means:

> **Move**

Move a file:

```bash
mv app.txt /tmp/
```

It can also rename files.

```bash
mv old.txt new.txt
```

So:

```text
mv = Move + Rename
```

* * *

# 24\. `rm`

`rm` removes files.

```bash
rm app.txt
```

Remove a directory recursively:

```bash
rm -r project/
```

Force removal:

```bash
rm -rf project/
```

⚠️ Be extremely careful with:

```bash
rm -rf
```

A mistake in the path can delete important data.

* * *

# 25\. Linux Directory Structure

Linux uses a hierarchical filesystem.

![Image](https://images.openai.com/static-rsc-4/IgsqSeQoRnwyyocectc0p-Ec0hfBuhptmbXJRzUur_mQ5fEeMh47Tl6Kq2HnKJetdki_BUF0JIJtrXmAFjJ_vZ-Sc82aWgZWmZrHGhokW7QrMrryX-uPvPcXvON9TiA4mrq9Sh7Y2-Jtz_GYUWSX2GKk-ZpsT_YjLEb4bkFimKh4q8DrmaQ4HjWKROFT3wUn?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/_ir45n-6W8I9D4bm52AMfJKYJb3ocd3XIhoTDJplgg5BWmCD8Ohk1Y2BZ18lOljJ9YnTkKRPDZ8RpiiQMkg6oiqhYoyM9BtOIqxN5Yo7O_sX0rnDPVQjIBiYX5S4Xrn7gUUNop0X6iCdeOWb5MdbJ8fzdwwv-ma3Npek154rnAFkRx12iSNkhIZLO7WY5UlU?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/o84Wkhq1n8L_RmnndEDTf6wTWCEc9JCjsh37lxmZzKTmrnWtHT18gsZL4qgI0kQ95CcnuE4-4pKXY591by_aCDzG_TlZKYIONAiIUZ1V-7GkWWVWHKZKSsNddaNoBXe2rzvB1mqXlPXxu4s6X973jeiX-bio1ku-w0di7jYoXJoSDZidqNQaBbZ7ZlhxYF5_?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/aLHCQHVo3lb3jhGVFsMhbzlQFfr4XSV_fRSao5HV8bbDKw9eyuFxtirGfrqfHLQEx2hPTa1HlPXInjlEKoWRoWJRsA8q00ZLdsuZQtgCxHQ_MpzZQ1_1uLMI3rcCktJV_W7TfKq16ZRljiWeItoHmbjLHYr7ohr3eu8WvwKXrHNTD1W8sAzc9GvMMNsIRLmW?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/GEJGy4JQxiSCjONLqWtsltLV-5jBghsft5g_ahqVOpkghqC_dhs9tVVTZlgc3cYEwRleDWZZH9l6wmk5IeU0cWKcH2I1-8rU270DtEsr-_99cr-_CQksqzHdZb3cbv_V3MOP2ZiBeijn61oo_GSXMM37-pLmfRWu8p7caj8DlhkUKQ0nB1ZwH6gztvZZDLDw?purpose=fullsize align="center")

Important directories include:

```text
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── opt
├── proc
├── root
├── run
├── sbin
├── tmp
├── usr
└── var
```

* * *

# 26\. Important Linux Directories

### `/`

Root of the filesystem.

Everything starts here.

* * *

### `/home`

Contains users' home directories.

Example:

```text
/home/ubuntu
/home/devops
/home/testuser
```

* * *

### `/root`

Home directory of the root user.

* * *

### `/etc`

Contains system and application configuration files.

Examples:

```text
/etc/ssh/
/etc/nginx/
/etc/hosts
```

* * *

### `/var`

Contains variable data.

Common examples:

```text
/var/log
/var/lib
/var/cache
```

Logs are commonly found under:

```text
/var/log
```

* * *

### `/tmp`

Temporary files.

* * *

### `/usr`

Contains many user-space programs, libraries, and shared resources.

* * *

### `/opt`

Often used for optional or third-party software.

* * *

### `/dev`

Contains device files.

* * *

### `/proc`

A virtual filesystem exposing process and kernel information.

* * *

# 27\. Absolute vs Relative Paths

### Absolute Path

Starts from `/`.

Example:

```bash
/home/ubuntu/project/app.py
```

### Relative Path

Starts from the current directory.

Example:

```bash
project/app.py
```

Suppose you're currently at:

```text
/home/ubuntu
```

Then:

```bash
project/app.py
```

refers to:

```text
/home/ubuntu/project/app.py
```

* * *

# 28\. Hidden Files

Linux files beginning with `.` are hidden.

Example:

```text
.bashrc
.gitconfig
.ssh
```

View them:

```bash
ls -a
```

* * *

# 29\. Hard Links and Soft Links

Linux supports two important types of links:

```text
Hard Link
Soft Link / Symbolic Link
```

![Image](https://images.openai.com/static-rsc-4/Bko56Ayxk-y-cwqsMUaI0hHNOcZtk6cfLYB10WH8Yt0XL8RpFpeDXL9hnTZWkjgq3EedQAQEc-yJjZNF2S363L376zf-QV6XdVTRLyM3aQ3xnpCUfY37bG_Nc7kQbFd6zrdlildYB0sFunYPZtqVEP3aybDrObLAV398pofYcHcOONASC1zbrthJt3sVzk3-?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/Zi6x0oSon3hJ0SLuXUxFdvi5z0hswO96GqhpHEXcYrIFMo8-GorOpa0t0j-Lpbmi3NJMwrBxc6iolm0X_w4vMtlx7j8ygU-6Wjui9vq1F4YiwCYS0WlXLnXXJLEe03ZfqxayEEFf0KcDs5gI0OHQDjwVRbpP_s1glDIzBOryBz6su7lqUYmQBgmYwlYLlWHq?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/RfjAwz0tAo0Sq9d0YL8Oq-7iVX6r3FU7je_h3GAA72GjhTCnXPoXMcD0sKBum0XG6_k3849eGYMQoLOBQj6sGKiqCdxZ85cEITDH-Qly1sX8g79jhvAtPTXNjt_VWPKHHl1M9t5JSRBUE3cqjjiQ_AWOGRo0qvHEB1VOW67DXs35jfPQEtmse5puPo0tJuvG?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/JjO9cVJeOlwWaFtDVNRpFP0Weckdt6W5eiBzM6DQVlUAv0tpj4I3qddIcLr_8R5NwDE33kDlu2uMq99QC2uwZG_jWgLmlbHH6XMx-dCkCLPs0ftoWtjkhLRH_FNp707T-fFuxieVyDUM2tQA-LucqZdYTXinj2sOkUm5lO-M9zJyFcwCHS_DxpYIYqo_444E?purpose=fullsize align="center")

* * *

# 30\. Soft Link

A symbolic link is similar to a shortcut.

Create one:

```bash
ln -s original.txt shortcut.txt
```

Example:

```text
original.txt
     ↑
     |
shortcut.txt
```

If the original file is removed:

```bash
rm original.txt
```

the symbolic link normally becomes broken.

* * *

# 31\. Hard Link

Create a hard link:

```bash
ln original.txt hardlink.txt
```

Both directory entries point to the same underlying file data/inode.

If the original filename is deleted:

```bash
rm original.txt
```

the data remains accessible through:

```text
hardlink.txt
```

as long as another hard link still references the inode.

* * *

# 32\. Hard Link vs Soft Link

| Feature | Hard Link | Soft Link |
| --- | --- | --- |
| Points to | Same inode/data | Path to target |
| `ln` | Yes | No |
| `ln -s` | No | Yes |
| Can cross filesystems | Generally no | Yes |
| Works with directories | Normally no | Yes |
| Target deleted | Still works | Becomes broken |

* * *

# 33\. Text Processing in Linux

Linux provides powerful commands for reading and processing text.

Important commands include:

```text
cat
less
head
tail
sort
grep
awk
sed
cut
uniq
wc
tee
```

These commands are extremely useful for DevOps because logs and configuration files are often plain text.

* * *

# 34\. `head`

`head` displays the beginning of a file.

```bash
head app.log
```

Show first 20 lines:

```bash
head -n 20 app.log
```

* * *

# 35\. `tail`

`tail` displays the end of a file.

```bash
tail app.log
```

Show last 20 lines:

```bash
tail -n 20 app.log
```

* * *

# 36\. `tail -f`

One of the most useful DevOps commands:

```bash
tail -f app.log
```

It continuously displays new lines added to the file.

This is extremely useful for monitoring logs.

Example:

```text
Application started
User logged in
Database connected
Request received
```

As new log entries appear, you see them immediately.

* * *

# 37\. `sort`

`sort` sorts lines.

Example file:

```text
banana
apple
orange
```

Command:

```bash
sort fruits.txt
```

Output:

```text
apple
banana
orange
```

Numeric sorting:

```bash
sort -n numbers.txt
```

Reverse:

```bash
sort -r fruits.txt
```

* * *

# 38\. `tee`

`tee` reads input and writes it both to the terminal and a file.

Example:

```bash
echo "Hello DevOps" | tee output.txt
```

You see:

```text
Hello DevOps
```

and the same content is written to:

```text
output.txt
```

Append instead of overwrite:

```bash
echo "Another line" | tee -a output.txt
```

* * *

# 39\. Linux `vi` / `vim`

`vi` is a terminal-based text editor.

Open a file:

```bash
vi file.txt
```

Important modes:

```text
Normal Mode
Insert Mode
Command Mode
```

* * *

# 40\. Basic `vi` Commands

Press:

```text
i
```

to enter insert mode.

Type your content.

Press:

```text
Esc
```

to return to normal mode.

Save:

```text
:w
```

Save and quit:

```text
:wq
```

Quit without saving:

```text
:q!
```

* * *

# 41\. Linux Users

Linux is a multi-user operating system.

Multiple users can exist on the same server.

Example:

```text
root
ubuntu
devops
developer
jenkins
```

This is very important for server security.

* * *

# 42\. Root User

The `root` user is the superuser.

Root has extensive privileges over the system.

For example, root can:

```text
Create users
Delete users
Install software
Change permissions
Modify system configuration
Stop services
Access protected files
```

Because root has powerful privileges, you should avoid using it unnecessarily.

* * *

# 43\. `sudo`

`sudo` allows an authorized user to execute a command with elevated privileges.

Example:

```bash
sudo apt update
```

Instead of switching permanently to root, you can run one command with elevated privileges.

Example:

```bash
sudo systemctl restart nginx
```

* * *

# 44\. Creating a User

Create a user:

```bash
sudo useradd devops
```

Create a home directory as well:

```bash
sudo useradd -m devops
```

* * *

# 45\. Setting a Password

```bash
sudo passwd devops
```

Linux asks you to enter the password.

* * *

# 46\. Switching Users

Use:

```bash
su devops
```

Switch to another user with a login environment:

```bash
su - devops
```

The `-` is important because it starts a login shell and loads the target user's environment appropriately.

* * *

# 47\. Delete a User

```bash
sudo userdel devops
```

Delete the user and their home directory:

```bash
sudo userdel -r devops
```

Be careful because deleting the home directory removes its contents.

* * *

# 48\. Linux Groups

Groups are used to organize users and permissions.

Example:

```text
Developers
QA
DevOps
Database
Admins
```

Create a group:

```bash
sudo groupadd devops
```

Add a user:

```bash
sudo gpasswd -a devopsuser devops
```

On many modern Linux distributions, you will also commonly see:

```bash
sudo usermod -aG devops devopsuser
```

The `-aG` form is especially important because `-a` preserves the user's existing supplementary groups.

* * *

# 49\. Remove a Group

```bash
sudo groupdel devops
```

* * *

# 50\. Check Current User

```bash
whoami
```

Example:

```text
ubuntu
```

* * *

# 51\. Check User Information

```bash
id
```

Example:

```text
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),27(sudo)
```

This tells you:

```text
UID
GID
Groups
```

* * *

# 52\. Linux File Permissions

One of the most important Linux concepts for DevOps is:

> **File permissions**

Every file and directory has permissions.

The three basic permissions are:

```text
r = Read
w = Write
x = Execute
```

And permissions are generally defined for:

```text
Owner
Group
Others
```

* * *

# 53\. Understanding Permissions

Suppose:

```bash
ls -l script.sh
```

returns:

```text
-rwxr-xr--
```

Break it down:

```text
- rwx r-x r--
  │   │   │
  │   │   └── Others
  │   └────── Group
  └────────── Owner
```

* * *

# 54\. Permission Meaning

### Read

```text
r = 4
```

Allows reading the file.

### Write

```text
w = 2
```

Allows modifying the file.

### Execute

```text
x = 1
```

Allows execution.

* * *

# 55\. Numeric Permissions

Add the values:

```text
Read    = 4
Write   = 2
Execute = 1
```

Therefore:

```text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2     = 6
r-x = 4 + 1     = 5
r-- = 4         = 4
```

* * *

# 56\. Permission `755`

When you see:

```bash
chmod 755 script.sh
```

it means:

```text
Owner  = 7 = rwx
Group  = 5 = r-x
Others = 5 = r-x
```

So:

```text
755
│││
││└── Others
│└─── Group
└──── Owner
```

* * *

# 57\. Permission `644`

```text
644
```

means:

```text
Owner  → rw-
Group  → r--
Others → r--
```

This is commonly appropriate for ordinary readable files.

* * *

# 58\. `chmod`

`chmod` means:

> **Change Mode**

Example:

```bash
chmod 755 script.sh
```

Make a script executable:

```bash
chmod +x script.sh
```

Remove write permission for others:

```bash
chmod o-w file.txt
```

* * *

# 59\. Change Owner

The `chown` command changes file ownership.

Example:

```bash
sudo chown ubuntu app.txt
```

Change owner and group:

```bash
sudo chown ubuntu:devops app.txt
```

* * *

# 60\. File Transfer in Linux

DevOps engineers frequently need to transfer files between machines.

Two important tools are:

```text
scp
rsync
```

* * *

# 61\. `scp`

`scp` means:

> **Secure Copy**

Copy local file to remote server:

```bash
scp app.txt ubuntu@server:/home/ubuntu/
```

Using an SSH key:

```bash
scp -i my-key.pem app.txt ubuntu@server:/home/ubuntu/
```

Copy a remote file to your local machine:

```bash
scp ubuntu@server:/home/ubuntu/app.txt .
```

* * *

# 62\. Copy a Directory with SCP

Use:

```bash
scp -r project/ ubuntu@server:/home/ubuntu/
```

The `-r` option recursively copies directories.

* * *

# 63\. `rsync`

`rsync` is useful for synchronizing files and directories efficiently.

Example:

```bash
rsync -av project/ ubuntu@server:/home/ubuntu/project/
```

Common options:

```text
-a = archive mode
-v = verbose
-z = compression
```

Example:

```bash
rsync -avz project/ ubuntu@server:/home/ubuntu/project/
```

* * *

# 64\. SCP vs Rsync

| SCP | Rsync |
| --- | --- |
| Simple file copying | Synchronization |
| Easy to understand | More efficient for repeated transfers |
| Transfers files | Transfers changed data efficiently |
| Good for simple tasks | Excellent for backups/deployments |

* * *

# 65\. Linux Networking

Networking knowledge is extremely important for DevOps.

You should understand:

```text
IP Address
MAC Address
Port
DNS
Gateway
Routing
TCP
UDP
HTTP
HTTPS
SSH
```

* * *

# 66\. `ip`

The modern command for network configuration and inspection is:

```bash
ip
```

Show addresses:

```bash
ip addr
```

Show routes:

```bash
ip route
```

Show links:

```bash
ip link
```

* * *

# 67\. `ping`

`ping` checks basic network reachability using ICMP.

Example:

```bash
ping google.com
```

or:

```bash
ping 8.8.8.8
```

Example:

```text
64 bytes from ...
```

This can help determine whether a destination is reachable, although a failed ping does **not** necessarily mean a service is unavailable because ICMP may be blocked.

* * *

# 68\. `ss`

`ss` is a modern tool for inspecting sockets and network connections.

Example:

```bash
ss -tuln
```

This can show listening TCP/UDP sockets.

Common options:

```text
-t = TCP
-u = UDP
-l = listening
-n = don't resolve service names
```

* * *

# 69\. `netstat`

You may still encounter:

```bash
netstat
```

Example:

```bash
netstat -tulnp
```

However, on many modern Linux systems, `ss` is preferred.

* * *

# 70\. Understanding Ports

A server can run multiple network services.

For example:

```text
SSH      → 22
HTTP     → 80
HTTPS    → 443
Jenkins  → 8080
```

Example:

```text
Client
  |
  | TCP 443
  ↓
Web Server
```

A port identifies a network service endpoint.

* * *

# 71\. `traceroute`

`traceroute` shows the network hops between your machine and a destination.

Example:

```bash
traceroute google.com
```

Conceptually:

```text
Your Computer
     ↓
Router
     ↓
ISP
     ↓
Router
     ↓
Router
     ↓
Destination
```

This is useful for investigating routing and latency problems.

* * *

# 72\. `arp`

ARP stands for:

> **Address Resolution Protocol**

In IPv4 local networks, ARP helps map an IP address to a MAC address.

You may encounter:

```bash
arp -a
```

On modern Linux, similar information can be inspected with:

```bash
ip neigh
```

Example:

```text
192.168.1.10 → MAC Address
```

* * *

# 73\. `curl`

`curl` is one of the most important commands for DevOps.

It transfers data using URLs and supports protocols such as HTTP and HTTPS.

Example:

```bash
curl https://example.com
```

Get only response headers:

```bash
curl -I https://example.com
```

Test an API:

```bash
curl https://api.example.com/users
```

* * *

# 74\. `curl` POST Request

Example:

```bash
curl -X POST https://api.example.com/users \
     -H "Content-Type: application/json" \
     -d '{"name":"Hritik"}'
```

This is extremely useful when testing REST APIs from a server.

* * *

# 75\. `curl` + `jq`

APIs often return JSON.

Example:

```bash
curl https://api.example.com/users
```

You can pipe the output into:

```bash
jq
```

Example:

```bash
curl https://api.example.com/users | jq
```

This makes JSON easier to read.

* * *

# 76\. `wget`

`wget` is commonly used for downloading files.

Example:

```bash
wget https://example.com/file.zip
```

Download with a specific name:

```bash
wget -O application.zip https://example.com/file.zip
```

* * *

# 77\. `grep`

`grep` searches text.

Suppose:

```text
application.log
```

contains:

```text
INFO Application started
ERROR Database connection failed
INFO User logged in
ERROR API request failed
```

Search for errors:

```bash
grep "ERROR" application.log
```

* * *

# 78\. Useful `grep` Options

Case-insensitive:

```bash
grep -i "error" application.log
```

Show line numbers:

```bash
grep -n "ERROR" application.log
```

Recursive search:

```bash
grep -r "database" /var/log/
```

Invert match:

```bash
grep -v "INFO" application.log
```

* * *

# 79\. `find`

`find` searches for files and directories.

Find a file:

```bash
find /home -name "app.txt"
```

Find all `.log` files:

```bash
find /var/log -name "*.log"
```

Find files larger than 100 MB:

```bash
find / -type f -size +100M
```

Find files modified recently:

```bash
find /var/log -type f -mtime -1
```

* * *

# 80\. `grep` vs `find`

Remember:

```text
find → Find files/directories

grep → Search inside text
```

Example:

```bash
find /var/log -name "*.log"
```

finds log files.

```bash
grep "ERROR" application.log
```

searches inside a log file.

* * *

# 81\. AWK

`awk` is one of the most powerful Linux text-processing tools.

It is particularly useful for:

*   Columns
    
*   Structured text
    
*   Reports
    
*   Logs
    
*   CSV/TSV-like data
    
*   Command output
    

Example:

```text
Alice  DevOps  50000
Bob    QA      45000
John   Cloud   60000
```

Suppose we want the first column:

```bash
awk '{print $1}' employees.txt
```

Output:

```text
Alice
Bob
John
```

* * *

# 82\. AWK Columns

For:

```text
Alice DevOps 50000
```

the fields are:

```text
$1 → Alice
$2 → DevOps
$3 → 50000
```

`$0` represents the complete line.

Example:

```bash
awk '{print $1, $3}' employees.txt
```

Output:

```text
Alice 50000
Bob 45000
John 60000
```

* * *

# 83\. AWK with Conditions

Example:

```bash
awk '$3 > 50000 {print $1}' employees.txt
```

This prints employees whose third column is greater than 50000.

* * *

# 84\. SED

`sed` stands for:

> **Stream Editor**

It is useful for searching, replacing, filtering, and transforming text.

Suppose:

```text
Hello World
Hello Linux
```

Replace `Hello` with `Hi`:

```bash
sed 's/Hello/Hi/g' file.txt
```

Output:

```text
Hi World
Hi Linux
```

* * *

# 85\. `sed` Editing a File

By default:

```bash
sed 's/old/new/g' file.txt
```

prints the modified content but doesn't modify the original file.

To edit the file in place on GNU/Linux:

```bash
sed -i 's/old/new/g' file.txt
```

Be careful when using `-i` because it modifies the original file.

* * *

# 86\. AWK vs SED

A simple way to remember:

```text
AWK
 ↓
Work with fields/data

SED
 ↓
Modify/transform text
```

Example:

```text
AWK → Extract column 3

SED → Replace "dev" with "prod"
```

Both are extremely useful in DevOps scripts.

* * *

# 87\. Linux Storage

Now let's move into another important DevOps topic:

> **Storage management**

Linux servers need storage for:

*   Applications
    
*   Databases
    
*   Logs
    
*   Docker images
    
*   Backups
    
*   Configuration
    
*   User data
    

* * *

# 88\. What Is a Disk?

A disk is physical or virtual storage.

Example:

```text
Server
 |
 +── Disk 1
 |
 +── Disk 2
 |
 +── Disk 3
```

In cloud environments, these may be virtual block-storage devices.

* * *

# 89\. What Is a Block Device?

A block device provides storage in blocks.

Examples include:

```text
/dev/sda
/dev/sdb
/dev/nvme0n1
```

These names depend on the hardware, VM, and Linux environment.

* * *

# 90\. `lsblk`

`lsblk` displays block devices.

```bash
lsblk
```

Example:

```text
NAME        SIZE TYPE MOUNTPOINTS
nvme0n1      30G disk
├─nvme0n1p1  29G part /
└─nvme0n1p2   1G part /boot
nvme1n1      50G disk
```

This helps you understand:

```text
Disk
 ↓
Partition
 ↓
Filesystem
 ↓
Mount Point
```

* * *

# 91\. What Is a Filesystem?

A filesystem organizes data on a storage device.

Common Linux filesystems include:

```text
ext4
XFS
Btrfs
```

For example:

```text
Disk
 ↓
Partition
 ↓
ext4 filesystem
 ↓
/data
```

* * *

# 92\. `df`

`df` displays filesystem disk usage.

Human-readable format:

```bash
df -h
```

Example:

```text
Filesystem      Size  Used Avail Use%
/dev/root        30G   15G   14G  52%
```

This tells you how much filesystem space is:

```text
Total
Used
Available
```

* * *

# 93\. `du`

`du` shows disk usage of files/directories.

Example:

```bash
du -sh /var/log
```

Find which directories consume space:

```bash
du -h --max-depth=1 /var
```

This is useful when a server's disk is filling up.

* * *

# 94\. `mkfs`

`mkfs` creates a filesystem on a device.

For example:

```bash
sudo mkfs.ext4 /dev/sdb
```

This formats the device with an ext4 filesystem.

⚠️ **Important:** Formatting a device can destroy existing data. Always verify the device name before using `mkfs`.

* * *

# 95\. Mounting

A filesystem must be mounted to make its contents accessible through the Linux directory tree.

Example:

```bash
sudo mkdir /data
```

Mount:

```bash
sudo mount /dev/sdb /data
```

Now:

```bash
cd /data
```

can access the mounted filesystem.

Conceptually:

```text
/dev/sdb
    |
    v
Filesystem
    |
    v
/data
```

* * *

# 96\. `umount`

To safely unmount:

```bash
sudo umount /data
```

Notice the command is:

```text
umount
```

not:

```text
unmount
```

* * *

# 97\. Temporary vs Persistent Mount

A command such as:

```bash
mount /dev/sdb /data
```

may not automatically make the mount persistent across reboot.

For persistent mounts, Linux commonly uses:

```text
/etc/fstab
```

Example entry:

```text
UUID=xxxx-xxxx  /data  ext4  defaults  0  2
```

Using UUIDs is generally safer than relying on device names that may vary.

* * *

# 98\. What Is LVM?

LVM stands for:

> **Logical Volume Manager**

LVM provides a flexible way to manage storage.

Without LVM, storage might look like:

```text
Disk
 ↓
Partition
 ↓
Filesystem
 ↓
Mount
```

With LVM:

```text
Disk
 ↓
Physical Volume
 ↓
Volume Group
 ↓
Logical Volume
 ↓
Filesystem
 ↓
Mount Point
```

![Image](https://images.openai.com/static-rsc-4/MqEImyNv9vDrF9d9mu94e-LjI4q_rDI4aOT-O25eAdPs0ROMWukTPKQSwd-0zekrmmUCTB0vyl4k_3eHZzi3aoPpOJmQ8v09y8vwvhX6RTlr0wcae6OOZUEGJiBz9m5moo2fX8q8MM6gAOr2H06b13iCXdYnoIn4qfwT6qKMbdp_cF67YUgdFsgCZAY5dAiN?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/i7cbB9bkS7rca2nqx6vrGmtZpkd6mVJQhuQJ5ePaGCe9LUumy5XfWNnYK9cmfPENCdYEpRWP3SlmkFBceJTu6scRSvywiBZ4M0elwt1C3ZdMBGvWJEO80CmeNr7_i-hQNkjkbed3T9_nGfwQUE24Oq1y4fyi2LftuIU1koER-HbfVKxBnmm7lCJx6yAHby4G?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/Y870qAiVGHcTSmsdtmTuhHPzAoq-Us715I4npDqUd0FfpdjfrRSwZ8uWJtAfY83aqmRAwGd_iYBk4PRydN7R-xhSXhMUhRDAppP6iCjM_2j7mSaujOrrxrBQ9PzNFym6sQzIckaQq-xJ9OoL9StYervraafP599NlmcdyhLgijUgh1KGf686HUk6Eepavb00?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/3o3y-XJphIlspq3By2Uk9MlFtcjsDCEnOXU9Vop20za2PcXcXYJyu-gj3rFAQITwltCXUrU8pxm_djw5BoqUvI9cEahTxTyDZERuEKlplm3dPs6XGAk39EIM-lamFhmVn_ahXG9uEz5nDwIasODOB6N2bzU6_4ivyn3suGVx8-zDsmGtwpg7hZQ0tqMJlshX?purpose=fullsize align="center")

![Image](https://images.openai.com/static-rsc-4/9VLRG4zgHVWKaC2cPnY5dSFK_7qX4MZ3WyXgwFaG4IU0T_d_dO5F0uUY2CJYNCngz_vR48JALcoAFiWAkASSRR4Gnz-Mv4NWULoArnW4ZR3zNowvIYOdIBDBgPhwqytabb4pB3f3Kf1lpqnUTU9jmtJzRspQTHRBWHlNXqkhnQXqXvErqKBkVn9XE3MLTwwR?purpose=fullsize align="center")

* * *

# 99\. LVM Components

There are three major components.

```text
PV
 ↓
VG
 ↓
LV
```

Meaning:

```text
PV = Physical Volume

VG = Volume Group

LV = Logical Volume
```

* * *

# 100\. Physical Volume

A **Physical Volume (PV)** is a storage device or partition prepared for LVM.

Example:

```bash
sudo pvcreate /dev/sdb
```

Check:

```bash
sudo pvs
```

* * *

# 101\. Volume Group

A **Volume Group (VG)** combines one or more physical volumes into a storage pool.

Example:

```bash
sudo vgcreate devops-vg /dev/sdb
```

Check:

```bash
sudo vgs
```

Conceptually:

```text
/dev/sdb
/dev/sdc
    |
    v
devops-vg
```

* * *

# 102\. Logical Volume

A Logical Volume is created from free space in a Volume Group.

Example:

```bash
sudo lvcreate -L 10G -n data-lv devops-vg
```

Now:

```text
PV
 ↓
VG
 ↓
LV
```

* * *

# 103\. Format the Logical Volume

Create an ext4 filesystem:

```bash
sudo mkfs.ext4 /dev/devops-vg/data-lv
```

Create mount point:

```bash
sudo mkdir /data
```

Mount:

```bash
sudo mount /dev/devops-vg/data-lv /data
```

* * *

# 104\. Complete LVM Flow

The complete process is:

```text
Physical Disk
     |
     v
Physical Volume
     |
     v
Volume Group
     |
     v
Logical Volume
     |
     v
Filesystem
     |
     v
Mount Point
```

Example:

```text
/dev/sdb
   ↓
pvcreate
   ↓
PV
   ↓
vgcreate
   ↓
devops-vg
   ↓
lvcreate
   ↓
data-lv
   ↓
mkfs.ext4
   ↓
/data
```

* * *

# 105\. Why Use LVM?

The major advantage is flexibility.

Suppose:

```text
/data = 10 GB
```

and later your application requires:

```text
/data = 20 GB
```

With appropriate free space and filesystem support, you can extend the logical volume and filesystem.

For example:

```bash
sudo lvextend -L +10G /dev/devops-vg/data-lv
```

Then resize the filesystem.

For ext4:

```bash
sudo resize2fs /dev/devops-vg/data-lv
```

For XFS, filesystem growth is normally performed using `xfs_growfs` on the mounted filesystem.

* * *

# 106\. LVM Advantages

### Flexible Storage

Logical volumes can be resized.

### Storage Pooling

Multiple physical devices can contribute to a volume group.

### Easier Management

Storage can be managed logically rather than being tightly tied to individual partitions.

### Snapshots

LVM supports snapshots, which can be useful for certain backup and testing scenarios.

* * *

# 107\. LVM Important Commands

### Physical Volumes

```bash
pvcreate
pvs
pvdisplay
```

### Volume Groups

```bash
vgcreate
vgs
vgdisplay
```

### Logical Volumes

```bash
lvcreate
lvs
lvdisplay
lvextend
lvreduce
```

### Filesystems

```bash
mkfs
mount
umount
df
```

* * *

# 108\. Linux Logs

Logs are extremely important for DevOps troubleshooting.

Common location:

```text
/var/log
```

Examples can include:

```text
/var/log/syslog
/var/log/auth.log
```

The exact files depend on your Linux distribution and logging system.

* * *

# 109\. Monitoring Logs

Use:

```bash
tail -f /var/log/syslog
```

Search errors:

```bash
grep -i "error" /var/log/syslog
```

Find recent entries:

```bash
tail -n 100 /var/log/syslog
```

This is a common troubleshooting workflow.

* * *

# 110\. Linux Troubleshooting Workflow

Suppose an application is not working.

Don't randomly run commands.

Follow a structured approach.

### Step 1 — Check the process

```bash
ps aux
```

### Step 2 — Check listening ports

```bash
ss -tuln
```

### Step 3 — Check logs

```bash
tail -f application.log
```

### Step 4 — Check disk

```bash
df -h
```

### Step 5 — Check memory

```bash
free -h
```

### Step 6 — Check CPU/processes

```bash
top
```

or:

```bash
htop
```

if installed.

### Step 7 — Test the service

```bash
curl http://localhost:8080
```

This systematic approach is much better than guessing.

* * *

# 111\. Useful Linux System Commands

### Check memory

```bash
free -h
```

### Check CPU/processes

```bash
top
```

### Check hostname

```bash
hostname
```

### Check OS information

```bash
cat /etc/os-release
```

### Check kernel

```bash
uname -r
```

### Check uptime

```bash
uptime
```

### Check current date

```bash
date
```

* * *

# 112\. Linux + DevOps: Real-World Example

Imagine you're deploying a Dockerized application on AWS EC2.

Your architecture might look like:

```text
Developer
   |
   v
GitHub
   |
   v
Jenkins
   |
   v
AWS EC2
   |
   +── Linux
   |
   +── Docker
   |
   +── Nginx
   |
   +── Application
   |
   +── Logs
   |
   +── Storage
```

You might use Linux commands to:

```text
Check disk
Check memory
Inspect logs
Change permissions
Create users
Transfer files
Check ports
Test APIs
Manage services
Mount storage
Troubleshoot applications
```

That's why Linux is fundamental to DevOps.

* * *

# 113\. Real DevOps Troubleshooting Example

Suppose your website is not opening.

You could follow:

```text
Website Not Working
       |
       v
Is server reachable?
       |
      ping
       |
       v
Is application running?
       |
      ps
       |
       v
Is port listening?
       |
      ss
       |
       v
Is firewall/security group correct?
       |
       v
Check application logs
       |
      grep
       |
       v
Test locally
       |
      curl
```

This is how Linux knowledge directly helps DevOps engineers.

* * *

# 114\. Most Important Linux Commands Cheat Sheet

| Category | Commands |
| --- | --- |
| Navigation | `pwd`, `ls`, `cd` |
| Files | `touch`, `cp`, `mv`, `rm` |
| Directories | `mkdir`, `rmdir` |
| Reading | `cat`, `less`, `head`, `tail` |
| Editing | `vi`, `vim` |
| Text | `grep`, `awk`, `sed`, `sort`, `tee` |
| Search | `find`, `locate` |
| Users | `useradd`, `passwd`, `userdel`, `su` |
| Groups | `groupadd`, `gpasswd`, `groupdel` |
| Permissions | `chmod`, `chown`, `chgrp` |
| Networking | `ip`, `ping`, `ss`, `traceroute` |
| HTTP/API | `curl`, `wget` |
| Transfer | `scp`, `rsync` |
| Storage | `lsblk`, `df`, `du`, `mount`, `umount` |
| LVM | `pvcreate`, `vgcreate`, `lvcreate`, `pvs`, `vgs`, `lvs` |
| System | `uname`, `free`, `top`, `uptime` |
| Services | `systemctl`, `journalctl` |

* * *

# 115\. Linux Commands You Should Practice

If you're a beginner, don't just read these commands.

Open a Linux terminal and practice.

### Day 1

```bash
pwd
ls
cd
mkdir
touch
cat
cp
mv
rm
```

### Day 2

```bash
head
tail
sort
tee
grep
find
```

### Day 3

```bash
useradd
passwd
su
id
groupadd
gpasswd
```

### Day 4

```bash
chmod
chown
ls -l
```

### Day 5

```bash
ip
ping
ss
curl
wget
scp
```

### Day 6

```bash
awk
sed
```

### Day 7

```bash
lsblk
df -h
du -sh
mount
umount
```

Then move to:

```text
LVM
Docker
Jenkins
Kubernetes
AWS
```

* * *

# 116\. Linux Interview Questions for Beginners

## Q1. What is Linux?

Linux is an open-source operating-system ecosystem built around the Linux kernel and distributed through distributions such as Ubuntu, Debian, and RHEL.

* * *

## Q2. What is the Linux kernel?

The kernel is the core component responsible for managing hardware resources and providing essential services to applications.

* * *

## Q3. What is a Linux distribution?

A distribution packages the Linux kernel with system utilities, libraries, package-management tools, and applications.

* * *

## Q4. What is SSH?

SSH is a secure protocol used to remotely access and manage systems.

* * *

## Q5. What is the root user?

Root is the Linux superuser with extensive administrative privileges.

* * *

## Q6. What is sudo?

`sudo` allows an authorized user to execute commands with elevated privileges.

* * *

## Q7. What is chmod?

`chmod` changes file or directory permissions.

* * *

## Q8. What does 755 mean?

```text
Owner  → rwx
Group  → r-x
Others → r-x
```

* * *

## Q9. Hard link vs soft link?

A hard link references the same inode/data, while a symbolic link references the target through a pathname.

* * *

## Q10. What is grep?

`grep` searches text for matching patterns.

* * *

## Q11. What is AWK?

AWK is a text-processing language particularly useful for processing structured, field-based data.

* * *

## Q12. What is SED?

SED is a stream editor used for filtering and transforming text.

* * *

## Q13. What is LVM?

LVM stands for Logical Volume Manager and provides flexible logical storage management.

* * *

## Q14. What are PV, VG and LV?

```text
PV = Physical Volume
VG = Volume Group
LV = Logical Volume
```

* * *

## Q15. What does `df -h` do?

It displays filesystem disk usage in a human-readable format.

* * *

## Q16. What does `lsblk` do?

It displays block devices and their relationships, partitions, and mount points.

* * *

# 117\. 🎯 Linux for DevOps — The Big Picture

If you're learning DevOps, think about Linux like this:

```text
                    LINUX
                      |
       +--------------+--------------+
       |              |              |
     Files          Users         Networking
       |              |              |
    Permissions      sudo           IP
       |              |              |
     Storage         Groups          Ports
       |                             |
      LVM                            DNS
       |                             |
       +-------------+---------------+
                     |
                     v
                 Processes
                     |
                     v
                  Services
                     |
                     v
                   Logs
                     |
                     v
                Troubleshooting
                     |
                     v
                  DEVOPS
```

Linux isn't just another topic in DevOps.

It is the **foundation on which many DevOps tools operate**.

* * *

# 118\. 🚀 Linux → Docker → Jenkins → Kubernetes

Once you understand Linux, your DevOps learning becomes much easier.

A typical learning path is:

```text
Linux
  ↓
Git & GitHub
  ↓
Networking
  ↓
AWS
  ↓
Docker
  ↓
Jenkins
  ↓
Kubernetes
  ↓
Terraform
  ↓
Monitoring
  ↓
Advanced DevOps
```

For example, when learning Docker, you will encounter:

```text
Linux processes
Namespaces
cgroups
Filesystems
Networking
Permissions
Volumes
```

When learning Kubernetes, you'll encounter:

```text
Linux nodes
Processes
Networking
Storage
Containers
Services
```

When learning Jenkins:

```text
Linux servers
SSH
Users
Permissions
Processes
Logs
Networking
```

So Linux knowledge keeps appearing everywhere.

* * *

# 119\. 🧠 The Most Important Linux Concepts for DevOps

If you don't have time to learn every Linux command immediately, prioritize these topics:

### ⭐ Must Know

```text
1. Files & directories
2. Permissions
3. Users & groups
4. SSH
5. Processes
6. Services
7. Networking
8. Logs
9. Disk management
10. Shell scripting
```

### ⭐ Advanced

```text
11. AWK
12. SED
13. LVM
14. System troubleshooting
15. Performance monitoring
16. Networking troubleshooting
17. Bash scripting
18. Cron
19. Systemd
20. Security
```

* * *

# 120\. 🏆 Final Linux DevOps Cheat Sheet

Keep this section bookmarked.

```bash
# Current directory
pwd

# List files
ls
ls -la

# Change directory
cd /path

# Create directory
mkdir project

# Create file
touch file.txt

# Read file
cat file.txt

# Copy
cp file.txt backup.txt

# Copy directory
cp -r project backup/

# Move / Rename
mv old.txt new.txt

# Delete
rm file.txt

# Delete directory
rm -rf project/

# Search text
grep "error" app.log

# Find files
find /var/log -name "*.log"

# First lines
head file.txt

# Last lines
tail file.txt

# Follow logs
tail -f app.log

# Sort
sort file.txt

# Text processing
awk '{print $1}' file.txt

# Replace text
sed 's/old/new/g' file.txt

# Create symbolic link
ln -s original.txt link.txt

# Create hard link
ln original.txt hardlink.txt

# Current user
whoami

# User information
id

# Create user
sudo useradd -m devops

# Password
sudo passwd devops

# Switch user
su - devops

# Create group
sudo groupadd devops

# Add user to group
sudo usermod -aG devops devops

# Permissions
chmod 755 script.sh

# Ownership
sudo chown user:group file.txt

# IP information
ip addr

# Routing
ip route

# Test connectivity
ping google.com

# Listening ports
ss -tuln

# HTTP request
curl https://example.com

# Download
wget https://example.com/file.zip

# Copy remote file
scp file.txt user@server:/tmp/

# Synchronize
rsync -av project/ user@server:/tmp/project/

# Block devices
lsblk

# Disk usage
df -h

# Directory size
du -sh /var/log

# Mount
sudo mount /dev/sdb /data

# Unmount
sudo umount /data

# LVM
sudo pvcreate /dev/sdb
sudo vgcreate devops-vg /dev/sdb
sudo lvcreate -L 10G -n data-lv devops-vg
sudo mkfs.ext4 /dev/devops-vg/data-lv
sudo mount /dev/devops-vg/data-lv /data
```

* * *

# 🎯 Conclusion

Linux is one of the most important foundations for a DevOps engineer.

You don't need to memorize hundreds of commands on day one.

Instead, understand **what problem each command solves**.

For example:

```text
Need to find a file?
        ↓
      find

Need to search inside a file?
        ↓
      grep

Need to process columns?
        ↓
      awk

Need to replace text?
        ↓
      sed

Need to check disk?
        ↓
      df / du

Need to check disks?
        ↓
      lsblk

Need to check network?
        ↓
      ip / ping / ss

Need to transfer files?
        ↓
      scp / rsync

Need to manage permissions?
        ↓
      chmod / chown

Need flexible storage?
        ↓
      LVM
```

The goal is not to become a Linux command memorization machine.

The goal is to become comfortable enough with Linux that when a **Jenkins pipeline fails, Docker container doesn't start, EC2 server runs out of disk, application port isn't reachable, or logs show an error**, you know where to look and which commands to use.

Once you are comfortable with Linux fundamentals, technologies such as **Docker, Jenkins, Kubernetes, AWS, Terraform and Ansible** become much easier to understand.

* * *

# 🚀 What's Next?

If you're following this as a DevOps learning series, the next logical topics are:

```text
Linux
  ↓
Git & GitHub
  ↓
AWS Fundamentals
  ↓
Docker
  ↓
Jenkins
  ↓
Kubernetes
  ↓
Terraform
  ↓
Ansible
  ↓
Prometheus + Grafana
  ↓
Advanced DevOps Projects
```

**Linux is not just a prerequisite for DevOps — it is one of the core skills you will continuously use throughout your DevOps career.**

* * *

## 📚 Recommended Practice Project

Don't stop after reading this article.

Create an **Ubuntu AWS EC2 server** and practice:

```text
✅ SSH
✅ Users
✅ Groups
✅ Permissions
✅ Files/directories
✅ Nginx
✅ Logs
✅ Networking
✅ SCP/rsync
✅ Disk management
✅ LVM
✅ Bash scripting
```

Then deploy a simple application on the server.

That practical experience will teach you far more than memorizing Linux commands.

* * *

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

## 🔖 Tags

`#Linux` `#DevOps` `#LinuxForDevOps` `#DevOpsForBeginners` `#LinuxCommands` `#AWS` `#CloudComputing` `#Docker` `#Jenkins` `#Kubernetes` `#LinuxAdministration` `#SystemAdministration` `#DevOpsLearning` `#LVM` `#LinuxNetworking`