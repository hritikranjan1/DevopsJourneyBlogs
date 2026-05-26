---
title: "DevOps Week 7 - Complete Kubernetes Fundamentals Guide ☸️ Part 2"
seoTitle: "Kubernetes Ingress, RBAC & Services Deep Dive | Week 7"
seoDescription: "Learn Kubernetes Services, Ingress, RBAC, OpenShift, traffic flow & security with beginner-friendly DevOps examples."
datePublished: 2026-05-25T14:52:16.924Z
cuid: cmplbrxcl00dn2cjvdoa6ey4z
slug: devops-week-7-complete-kubernetes-fundamentals-guide-part-2
cover: https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/1cdec501-0bf4-4a07-b9c7-ac8803894f38.png
tags: openshift, docker, aws, kubernetes, cloud-computing, devops, k8s, rbac, ingress, devops-journey

---

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/8842e5b1-e0f0-4da0-be71-7704f243229a.png align="center")

# 🔹 Why Kubernetes Services Are Important? 🤔

In Kubernetes, Pods are temporary.

If a Pod crashes:

```text
Kubernetes creates a new Pod with a new IP address
```

Because Pod IPs keep changing, applications cannot communicate reliably using direct Pod IPs.

This creates problems:  
❌ Frontend cannot find backend  
❌ Users lose connectivity  
❌ Traffic routing becomes unstable

* * *

# 🔹 Solution: Kubernetes Services 🌐

Kubernetes Services provide:  
✅ Stable networking  
✅ Service discovery  
✅ Load balancing  
✅ Reliable communication between Pods

A Service acts as:

```text
Stable entry point for Pods
```

Even if Pod IPs change, the Service remains constant.

* * *

# 🔹 Real-Life Example 💡

Imagine: Employees in a company keep changing desks daily.

Instead of contacting employees directly, customers contact:

```text
Reception Desk
```

The receptionist forwards requests to available employees.

Similarly:

```text
Kubernetes Service routes traffic to available Pods
```

* * *

# 🔹 Application Deployment in Kubernetes 🚀

The instructor first:  
✅ Created a sample Django/Python application  
✅ Built Docker image  
✅ Deployed application in Kubernetes  
✅ Created 2 Pod replicas

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/9e4a35c1-345e-4182-831c-4968db5fa860.png align="center")

# 🔹 Why Multiple Replicas Are Important? 🔄

Using multiple replicas helps in:  
✅ High availability  
✅ Load balancing  
✅ Better performance  
✅ Fault tolerance

If one Pod crashes, other Pods continue serving users.

* * *

# 🔹 Problem Without Services ⚠️

Suppose: Frontend application directly communicates with Pod IP.

If Pod gets deleted:  
❌ IP changes  
❌ Communication breaks  
❌ Application stops working

This is why:

```text
Direct Pod communication is not reliable
```

* * *

# 🔹 What is Service Discovery? 🔍

Service Discovery means:

```text
Automatically finding Pods inside Kubernetes
```

Kubernetes Services use:  
✅ Labels  
✅ Selectors

to identify Pods dynamically.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/7611ab37-8893-4397-aa89-9fdb02bc683d.png align="center")

# 🔹 What are Labels? 🏷️

Labels are key-value pairs attached to Kubernetes objects.

Example:

```yaml
app: django
env: production
```

Labels help Kubernetes identify Pods.

* * *

# 🔹 What are Selectors? 🎯

Selectors are used by Services to:

```text
Find matching Pods using labels
```

* * *

# 🔹 How Labels & Selectors Work Together? ⚙️

Example:

Pod Label:

```yaml
app: django
```

Service Selector:

```yaml
app: django
```

Now Service automatically connects to matching Pods.

* * *

# 🔹 Important Learning 💡

If labels are incorrect:  
❌ Service cannot discover Pods  
❌ Traffic routing fails

The instructor demonstrated this practically.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/ff96c40d-8cc4-4385-89f8-c45606447706.png align="center")

# 🔹 Kubernetes Service Types 🌍

The video explains two major Service types:

✅ NodePort |  
✅ LoadBalancer

* * *

# 🔹 NodePort Service 🌐

NodePort exposes application using:

```text
<Node-IP>:<Port>
```

This allows access from outside Kubernetes cluster.

* * *

# 🔹 How NodePort Works? ⚙️

Traffic Flow:

```text
User → Worker Node IP → Service → Pod
```

Kubernetes opens a port on every worker node.

Example:

```text
192.168.1.10:30007
```

* * *

# 🔹 Use Cases of NodePort 💡

Mostly used for:  
✅ Testing  
✅ Development  
✅ Internal applications

* * *

# 🔹 Limitations of NodePort ⚠️

❌ Not ideal for production internet exposure  
❌ Requires node IP knowledge  
❌ Limited scalability

* * *

# 🔹 LoadBalancer Service ☁️

LoadBalancer exposes application publicly using cloud provider integrations.

Used mainly in:

*   AWS
    
*   Azure
    
*   GCP
    

* * *

# 🔹 How LoadBalancer Works? 🌍

Traffic Flow:

```text
Internet → Cloud Load Balancer → Service → Pods
```

Cloud provider automatically:  
✅ Creates public IP  
✅ Configures external load balancer

* * *

# 🔹 Benefits of LoadBalancer 🚀

✅ Public internet access  
✅ Production-ready  
✅ Automatic traffic distribution  
✅ Better scalability

* * *

# 🔹 Traffic Load Balancing in Kubernetes ⚖️

One of the biggest advantages of Services is:

```text
Automatic traffic distribution
```

If multiple Pods exist: Kubernetes Service distributes requests across Pods.

* * *

# 🔹 Round Robin Load Balancing 🔄

The instructor demonstrated:

```text
Round Robin traffic distribution
```

Example:

*   Request 1 → Pod A
    
*   Request 2 → Pod B
    
*   Request 3 → Pod A
    

This improves:  
✅ Performance  
✅ Availability  
✅ Resource utilization

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/260b1980-2724-45f6-89bf-5f49e272a3de.png align="center")

# 🔹 What is KubeShark? 🦈

KubeShark is a Kubernetes traffic debugging and visualization tool.

It helps engineers:  
✅ Monitor traffic  
✅ Debug networking  
✅ Visualize request flow  
✅ Understand service communication

* * *

# 🔹 Why KubeShark is Useful? 🚀

Normally, network traffic inside Kubernetes is difficult to understand.

KubeShark makes it easy by showing:

```text
Real-time request & response flow
```

* * *

# 🔹 What Did the Instructor Demonstrate? 💡

Using KubeShark, the instructor showed:  
✅ Request origin  
✅ Traffic entering Service  
✅ Traffic routing to Pods  
✅ Load balancing behavior

* * *

# 🔹 Kubernetes Traffic Flow Explained 🔄

Complete request flow:

```text
User → Kubernetes Service → Selected Pod
```

If multiple Pods exist: Service automatically selects one Pod.

* * *

# 🔹 Real-Life Example 💡

Imagine: A restaurant has:

*   Multiple chefs (Pods)
    
*   One receptionist (Service)
    

Customers place orders at reception.

Reception distributes work among chefs equally.

This is exactly how:

```text
Kubernetes Services perform load balancing
```

* * *

# 🔹 Why Services Are Critical in Production? 🏢

Without Services:  
❌ Applications break when Pod IP changes  
❌ Scaling becomes difficult  
❌ Networking becomes unstable

Services provide:  
✅ Stability  
✅ Scalability  
✅ Reliable communication  
✅ Production-grade networking

* * *

# 🔹 Beginner-Friendly Summary 🧠

| Concept | Simple Meaning |
| --- | --- |
| Pod | Runs application |
| Service | Stable communication layer |
| Labels | Pod identification tags |
| Selectors | Used to find Pods |
| NodePort | Exposes app via node IP |
| LoadBalancer | Public internet access |
| KubeShark | Traffic monitoring tool |

* * *

# 🔹 Important kubectl Commands ⚙️

* * *

## ✔ View Services

```bash
kubectl get svc
```

* * *

## ✔ View Pods

```bash
kubectl get pods
```

* * *

## ✔ Describe Service

```bash
kubectl describe svc <service-name>
```

* * *

## ✔ Expose Deployment

```bash
kubectl expose deployment django-app --type=NodePort --port=80
```

* * *

# 🔥 Real-World Scenario Based Questions

* * *

# ❓ Why not use Pod IP directly?

### ✅ Answer:

Because Pod IPs are temporary and change whenever Pods restart or get recreated.

Services provide stable communication.

* * *

# ❓ How does Kubernetes achieve load balancing?

### ✅ Answer:

Kubernetes Services distribute incoming traffic across multiple Pods using round-robin method.

* * *

# ❓ What happens if labels don’t match selectors?

### ✅ Answer:

Service cannot discover Pods, so traffic routing fails.

* * *

# ❓ Why is LoadBalancer preferred in production?

### ✅ Answer:

Because it provides:  
✅ Public access  
✅ Scalability  
✅ Cloud integration  
✅ Better availability

* * *

# ❓ Why is KubeShark useful?

### ✅ Answer:

It helps DevOps engineers:  
✅ Visualize traffic  
✅ Debug networking  
✅ Monitor communication between services

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/eea5f467-da38-4515-9db2-204e1c315ae3.png align="center")

* * *

# 🔹 What Problem Exists with Kubernetes Services? 🤔

Kubernetes Services are great for:  
✅ Service discovery  
✅ Internal communication  
✅ Basic load balancing

But in real production environments, they are not enough.

* * *

# 🔹 Limitations of Basic Kubernetes Services ⚠️

Basic Services cannot easily handle:  
❌ Path-based routing  
❌ Host-based routing  
❌ Sticky sessions  
❌ Advanced HTTPS/TLS management  
❌ Centralized traffic management

* * *

# 🔹 Real-World Problem Example 💡

Imagine: Your company has:

*   Frontend application
    
*   API service
    
*   Admin dashboard
    
*   Payment service
    

If every application uses:

```text
Separate LoadBalancer service
```

then:  
❌ Multiple public IPs are created  
❌ Cloud cost increases  
❌ Management becomes difficult

* * *

# 🔹 Why LoadBalancer Services Become Expensive? 💰

Cloud providers like:

*   AWS
    
*   Azure
    
*   GCP
    

charge money for every:

```text
Public LoadBalancer IP
```

If a company has:

*   20 microservices
    
*   50 applications
    

then cost becomes very high.

* * *

# 🔹 Solution: Kubernetes Ingress 🚀

Ingress provides:  
✅ Centralized routing  
✅ Single entry point  
✅ Advanced load balancing  
✅ HTTPS support  
✅ Domain-based routing

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/b9a9bbf0-0259-4911-ae8a-a1eb40a366bb.png align="center")

# 🔹 What is Kubernetes Ingress? 🌐

Ingress is a Kubernetes resource used to:

```text
Manage external access to applications inside the cluster
```

It acts like:

```text
Smart traffic manager
```

for Kubernetes applications.

* * *

# 🔹 Real-Life Example 💡

Imagine a shopping mall.

Instead of every shop having:  
❌ Separate gate

the mall uses:

```text
One main entrance with security & routing
```

Visitors are guided to correct shops.

Similarly: Ingress routes users to correct services.

* * *

# 🔹 What Can Ingress Do? ⚙️

Ingress supports:  
✅ Host-based routing  
✅ Path-based routing  
✅ HTTPS/TLS  
✅ Load balancing  
✅ SSL termination  
✅ Reverse proxy functionality

* * *

# 🔹 What is Host-Based Routing? 🌍

Traffic routing based on domain names.

Example:

```text
api.myapp.com → API Service
admin.myapp.com → Admin Service
shop.myapp.com → Shopping Service
```

* * *

# 🔹 What is Path-Based Routing? 🛣️

Traffic routing based on URL paths.

Example:

```text
/api → Backend API
/admin → Admin dashboard
/products → Product service
```

* * *

# 🔹 What are Sticky Sessions? 🍪

Sticky sessions ensure:

```text
User continuously connects to same backend server
```

Useful for:

*   Login sessions
    
*   Shopping carts
    
*   Stateful applications
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/89572c1a-0fe0-4c7d-a5f7-72271365bf3f.png align="center")

# 🔹 Why Ingress is Important in Microservices? 🏢

Modern applications contain:

*   Many services
    
*   Multiple APIs
    
*   Separate frontend/backend systems
    

Ingress helps:  
✅ Manage traffic centrally  
✅ Simplify routing  
✅ Reduce infrastructure cost

* * *

# 🔹 Important Concept: Ingress Alone Does NOT Work ⚠️

This is the most important beginner concept.

Ingress resource only defines:

```text
Routing rules
```

But it cannot actually handle traffic by itself.

* * *

# 🔹 What is an Ingress Controller? 🎛️

Ingress Controller is the actual component that:  
✅ Reads Ingress rules  
✅ Configures load balancer  
✅ Routes traffic properly

* * *

# 🔹 Real-Life Example 💡

Think of:

```text
Ingress = Traffic rules document
Ingress Controller = Traffic police implementing rules
```

Without traffic police, rules cannot work.

* * *

# 🔹 Popular Ingress Controllers 🚀

Common controllers include:

*   NGINX Ingress Controller
    
*   HAProxy
    
*   Traefik
    
*   F5
    
*   AWS ALB Controller
    

* * *

# 🔹 NGINX Ingress Controller 🌐

The instructor used:

```text
NGINX Ingress Controller
```

because it is:  
✅ Popular  
✅ Beginner friendly  
✅ Production-ready  
✅ Widely used in industry

* * *

# 🔹 How Ingress Works? 🔄

Traffic Flow:

```text
User → Ingress Controller → Ingress Rules → Kubernetes Service → Pods
```

* * *

# 🔹 Complete Workflow Explained 💡

Step 1: User opens website.

Step 2: Ingress Controller receives traffic.

Step 3: Ingress rules decide:

```text
Where request should go
```

Step 4: Traffic forwarded to correct Kubernetes Service.

Step 5: Service sends traffic to Pods.

* * *

# 🔹 Practical Demo Covered in Video 🧪

The instructor demonstrated:  
✅ Creating Ingress resource  
✅ Installing NGINX Ingress Controller  
✅ Configuring routing rules  
✅ Exposing applications  
✅ Testing routing locally  
Video link - https://youtu.be/47ck6bh6dfI?si=mDTEXUXP1N50AinI

* * *

# 🔹 Important Beginner Mistake ⚠️

Many beginners think:

```text
Creating Ingress YAML is enough
```

But: ❌ Without Ingress Controller, Ingress does not function.

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/0309af66-c1ec-40cc-ba20-6ab7d9d450d9.png align="center")

# 🔹 Why Ingress Controller is Mandatory? 🤔

Because controller:  
✅ Watches Ingress resources  
✅ Applies routing configuration  
✅ Manages actual traffic flow

Without controller:

```text
No traffic routing happens
```

* * *

# 🔹 Local Testing Using /etc/hosts 🖥️

The instructor also showed:

```text
/etc/hosts file modification
```

for local domain testing.

Example:

```text
127.0.0.1 myapp.local
```

This helps simulate:  
✅ Real domain names  
✅ Local testing environment

* * *

# 🔹 Kubernetes Ingress vs LoadBalancer ⚔️

| LoadBalancer | Ingress |
| --- | --- |
| Separate public IP for each service | Single entry point |
| Expensive | Cost efficient |
| Limited routing | Advanced routing |
| Basic load balancing | Enterprise features |
| Difficult to manage | Centralized management |

* * *

# 🔹 Why Companies Prefer Ingress? 🏢

Ingress provides:  
✅ Better scalability  
✅ Lower cloud cost  
✅ Centralized traffic management  
✅ HTTPS support  
✅ Production-ready architecture

* * *

# 🔹 Beginner-Friendly Architecture Flow ☸️

```text
Internet
   ↓
Ingress Controller
   ↓
Ingress Rules
   ↓
Kubernetes Services
   ↓
Pods
```

* * *

# 🔹 Important kubectl Commands ⚙️

* * *

## ✔ View Ingress Resources

```bash
kubectl get ingress
```

* * *

## ✔ Describe Ingress

```bash
kubectl describe ingress
```

* * *

## ✔ View Services

```bash
kubectl get svc
```

* * *

## ✔ View Pods

```bash
kubectl get pods
```

* * *

# 🔹 Example Ingress YAML 📄

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: my-ingress
spec:
  rules:
  - host: myapp.local
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: frontend-service
            port:
              number: 80
```

* * *

# 🔥 Real-World Scenario Based Questions

* * *

# ❓ Why not use LoadBalancer for every service?

### ✅ Answer:

Because:  
❌ Cloud cost becomes very high  
❌ Multiple public IPs are difficult to manage

Ingress provides centralized routing using single entry point.

* * *

# ❓ What happens if Ingress Controller is missing?

### ✅ Answer:

Ingress rules will exist, but traffic routing will not work.

Because controller is responsible for implementing rules.

* * *

# ❓ Why is Ingress important for microservices?

### ✅ Answer:

Because microservices architecture contains many services, Ingress helps manage:  
✅ Routing  
✅ Security  
✅ HTTPS  
✅ Traffic management centrally

* * *

# ❓ What is the difference between Ingress and Service?

### ✅ Answer:

| Service | Ingress |
| --- | --- |
| Internal communication | External traffic management |
| Basic load balancing | Advanced routing |
| Works inside cluster | Entry point for external users |

* * *

# ❓ Why is NGINX Ingress Controller popular?

### ✅ Answer:

Because it is:  
✅ Open-source  
✅ Fast  
✅ Reliable  
✅ Production-ready  
✅ Easy to configure

* * *

# 🔥 Interview Tip 🚀

If interviewer asks:

```text
Why Ingress is needed?
```

Best answer:

```text
Ingress provides advanced routing, HTTPS security, and centralized traffic management while reducing cloud infrastructure cost.
```

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/82ddb46d-0eb5-4b89-9f8e-a4a40c347ec5.png align="center")

# 🔹 What is RBAC in Kubernetes? 🔐

RBAC stands for:

```text
Role-Based Access Control
```

It is a security mechanism used in Kubernetes to:

```text
Control who can access what inside the cluster
```

RBAC defines:  
✅ Who can access resources  
✅ What actions they can perform  
✅ Which resources they can manage

* * *

# 🔹 Why RBAC is Important? 🤔

In production environments, many people work on the same Kubernetes cluster.

Examples:

*   Developers
    
*   DevOps Engineers
    
*   Security Teams
    
*   QA Teams
    

Without RBAC:  
❌ Anyone could delete Pods  
❌ Anyone could change deployments  
❌ Security risks become very high

* * *

# 🔹 Real-Life Example 💡

Imagine a company office.

Different employees have different permissions:

*   HR can access employee records
    
*   Finance team can access salary data
    
*   Security guards control entry gates
    

Not everyone gets:

```text
Full admin access
```

Similarly, RBAC controls permissions inside Kubernetes.

* * *

# 🔹 What Does RBAC Control? ⚙️

RBAC controls actions like:  
✅ Creating Pods  
✅ Deleting Deployments  
✅ Viewing Logs  
✅ Accessing Secrets  
✅ Managing Namespaces

* * *

# 🔹 Core Components of Kubernetes RBAC 🧩

RBAC mainly consists of:

*   Users / Service Accounts
    
*   Roles / ClusterRoles
    
*   RoleBindings / ClusterRoleBindings
    

These components work together to manage permissions.

* * *

# 🔹 Users & Service Accounts 👤

These are identities requesting access.

Examples:

*   Developers
    
*   CI/CD pipelines
    
*   Applications
    
*   Automation tools
    

* * *

# 🔹 Difference Between User and Service Account ⚔️

| User | Service Account |
| --- | --- |
| Human identity | Application identity |
| Used by developers/admins | Used by Pods/apps |
| External authentication | Managed inside Kubernetes |

* * *

# 🔹 Important Beginner Concept ⚠️

Kubernetes does:

```text
NOT manage users directly
```

Instead, authentication is handled using external systems like:

*   AWS IAM
    
*   Okta
    
*   Keycloak
    
*   Azure AD
    

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/96b94e98-b597-466b-a00a-55f9645856d5.png align="center")

# 🔹 What is a Role? 🛡️

A Role defines:

```text
What actions are allowed
```

inside a specific namespace.

Example: A Role may allow:  
✅ View Pods  
✅ Read logs  
❌ Cannot delete deployments

* * *

# 🔹 Real-Life Example of Role 💡

Think of:

```text
Role = Job responsibilities
```

Example:

*   Manager permissions
    
*   Employee permissions
    
*   Intern permissions
    

* * *

# 🔹 What is a ClusterRole? 🌍

ClusterRole works across:

```text
Entire Kubernetes cluster
```

Unlike Roles, ClusterRoles are not limited to one namespace.

* * *

# 🔹 Difference Between Role and ClusterRole ⚔️

| Role | ClusterRole |
| --- | --- |
| Namespace-specific | Cluster-wide |
| Limited scope | Full cluster scope |
| Smaller permissions | Larger permissions |

* * *

# 🔹 What is RoleBinding? 🔗

RoleBinding connects:

```text
User/Service Account → Role
```

It assigns permissions to users.

Without RoleBinding:  
❌ Roles are useless

* * *

# 🔹 Real-Life Example 💡

Imagine:

```text
Role = Office ID card permissions
RoleBinding = Assigning ID card to employee
```

* * *

# 🔹 What is ClusterRoleBinding? 🌐

ClusterRoleBinding connects:

```text
User → ClusterRole
```

across the entire Kubernetes cluster.

* * *

# 🔹 How RBAC Works? 🔄

Complete Flow:

```text
User → RoleBinding → Role → Permissions → Kubernetes Resources
```

* * *

# 🔹 Example RBAC Workflow 💡

Developer wants to:

```text
View Pods in development namespace
```

RBAC checks:  
✅ Does user have Role?  
✅ Is RoleBinding configured?  
✅ Does Role allow action?

If yes:  
✅ Access granted

Otherwise:  
❌ Access denied

* * *

# 🔹 Why Companies Use RBAC? 🏢

RBAC helps organizations:  
✅ Improve security  
✅ Prevent accidental deletions  
✅ Control team permissions  
✅ Follow compliance rules  
✅ Separate responsibilities

* * *

# 🔹 What is OpenShift? ☁️

OpenShift is:

```text
Enterprise Kubernetes platform by Red Hat
```

It provides:  
✅ Kubernetes management  
✅ Security features  
✅ CI/CD integrations  
✅ Monitoring tools

* * *

# 🔹 OpenShift Sandbox for Beginners 🚀

The instructor demonstrated:

```text
Free 30-day OpenShift Sandbox
```

This gives learners:  
✅ Real Kubernetes environment  
✅ Hands-on practice  
✅ Production-like experience

without requiring cloud setup.

* * *

# 🔹 Benefits of OpenShift Sandbox 💡

Beginners can:  
✅ Practice Kubernetes  
✅ Deploy applications  
✅ Learn RBAC  
✅ Monitor workloads  
✅ Explore dashboards

* * *

# 🔹 OpenShift Dashboard 🖥️

The instructor also explored:  
✅ Deployments  
✅ Events  
✅ Pods  
✅ Monitoring tools  
✅ Resource usage

through the OpenShift UI dashboard.

* * *

# 🔹 CLI Login Using Token 🔑

OpenShift allows login using:

```text
CLI display token
```

This helps users securely connect to the cluster.

* * *

# 🔹 Why Learning RBAC is Important for DevOps Engineers? 🚀

RBAC is used daily in production environments.

DevOps Engineers manage:  
✅ Team access  
✅ Deployment permissions  
✅ Security policies  
✅ CI/CD authentication

* * *

# 🔹 Beginner-Friendly RBAC Architecture ☸️

```text
User / Service Account
          ↓
     RoleBinding
          ↓
      Role
          ↓
 Kubernetes Resources
```

* * *

# 🔹 Example Role YAML 📄

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: dev
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
```

* * *

# 🔹 Example RoleBinding YAML 📄

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: dev
subjects:
- kind: User
  name: developer1
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

* * *

# 🔹 Important kubectl Commands ⚙️

* * *

## ✔ View Roles

```bash
kubectl get roles
```

* * *

## ✔ View RoleBindings

```bash
kubectl get rolebindings
```

* * *

## ✔ View ClusterRoles

```bash
kubectl get clusterroles
```

* * *

## ✔ View ClusterRoleBindings

```bash
kubectl get clusterrolebindings
```

* * *

## ✔ Check User Permissions

```bash
kubectl auth can-i create pods
```

* * *

![](https://cdn.hashnode.com/uploads/covers/66fecde7cb0abd844c1a2f3c/4aafc932-8a38-4fca-a50d-914256c92c94.png align="center")

# 🔥 Real-World Scenario Based Questions

* * *

# ❓ Why is RBAC important in Kubernetes?

### ✅ Answer:

RBAC improves security by controlling who can access and modify Kubernetes resources.

* * *

# ❓ What happens if RBAC is not configured?

### ✅ Answer:

Anyone with access may:  
❌ Delete workloads  
❌ Modify configurations  
❌ Access sensitive data

This creates major security risks.

* * *

# ❓ Why does Kubernetes use external authentication providers?

### ✅ Answer:

Kubernetes focuses on cluster management, so authentication is delegated to systems like:

*   AWS IAM
    
*   Okta
    
*   Keycloak
    

* * *

# ❓ Difference between Role and ClusterRole?

### ✅ Answer:

| Role | ClusterRole |
| --- | --- |
| Namespace level | Cluster-wide |
| Limited scope | Global permissions |

* * *

# ❓ What is the purpose of RoleBinding?

### ✅ Answer:

RoleBinding assigns Roles to users or service accounts.

Without binding, permissions are not applied.

* * *

# 🔥 Interview Tip 🚀

If interviewer asks:

```text
What is RBAC?
```

Best answer:

```text
RBAC is a Kubernetes security mechanism that controls which users or applications can perform specific actions on cluster resources.
```

* * *