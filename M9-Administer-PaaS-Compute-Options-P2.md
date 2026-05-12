# 🐳 Module 9: Administer PaaS Compute Options (Part 2)

## 📚 Overview

This module focuses on administering container-based PaaS services in Azure. It covers:
- 📦 Azure Container Registry (ACR)
- 🐳 Azure Container Instances (ACI)
- 🚀 Azure Container Apps

These services allow organizations to build, store, deploy, and manage containerized applications in Azure.

---

# 🧠 Core Concept of Containers

## 📖 What is a Container?

A container is a lightweight, portable package that contains:
- Application code
- Runtime
- Libraries
- Dependencies

Containers allow applications to run consistently across environments.

---

# 🎯 Benefits of Containers

- ⚡ Fast deployment
- 📦 Portability
- 🔄 Consistent environments
- 💰 Efficient resource usage
- 📈 Easy scalability

---

# 📦 Lesson 1: Create and Manage an Azure Container Registry (ACR)

# 📖 What is Azure Container Registry?

Azure Container Registry (ACR) is a private registry used to store and manage container images.

---

# 🎯 Purpose of ACR

- Store Docker container images
- Secure container repositories
- Integrate with Azure services
- Support CI/CD pipelines

---

# 🧩 Container Workflow

```text
Build Container Image
        ↓
Push to Azure Container Registry
        ↓
Deploy to Azure Services
``` 

---

# 📦 What is a Container Image?

A container image is a packaged application template that includes:
- Code
- Runtime
- Dependencies
- Configuration

---

# 🔐 Benefits of ACR

| Benefit | Description |
|---|---|
| Private Registry 🔒 | Secure image storage |
| Azure Integration ☁️ | Works with Azure services |
| High Availability 🌍 | Reliable image hosting |
| CI/CD Support ⚙️ | Automated deployments |

---

# 🛠️ Steps to Create an ACR

1. Open Azure Portal 🌐
2. Search:
   - Container Registries
3. Click ➕ Create
4. Configure:
   - Registry name
   - Resource Group
   - Region
   - Pricing tier
5. Review and create

---

# 📌 ACR Pricing Tiers

| Tier | Purpose |
|---|---|
| Basic 💰 | Development/testing |
| Standard ⚙️ | Production workloads |
| Premium 🚀 | Advanced enterprise features |

---

# 🐳 Docker and ACR

## 📦 Push Image to ACR

```bash
docker push myregistry.azurecr.io/myapp:v1
``` 

---

## 📥 Pull Image from ACR

```bash
docker pull myregistry.azurecr.io/myapp:v1
``` 

---

# 🔐 Security Features of ACR

- Role-Based Access Control (RBAC)
- Microsoft Entra ID integration
- Private networking
- Image scanning support

---

# 🐳 Lesson 2: Provision a Container by Using Azure Container Instances (ACI)

# 📖 What is Azure Container Instances?

Azure Container Instances (ACI) is a serverless container service that allows you to run containers without managing servers or orchestration platforms.

---

# 🎯 Purpose of ACI

- Run containers quickly
- Simplify container deployment
- Avoid VM management
- Support short-term workloads

---

# 🧩 ACI Characteristics

| Feature | Description |
|---|---|
| Serverless ⚡ | No infrastructure management |
| Fast Startup 🚀 | Quick deployment |
| Pay-per-Use 💰 | Charged only while running |
| Lightweight 🪶 | Ideal for temporary workloads |

---

# 🛠️ Example ACI Workflow

```text
Container Image
      ↓
Azure Container Instance
      ↓
Running Application
``` 

---

# 📌 Common Use Cases

- Testing containers 🧪
- Background processing ⚙️
- Batch jobs 📦
- APIs 🌐
- Event-driven workloads 🔔

---

# 🛠️ Steps to Create an ACI

1. Open Azure Portal 🌐
2. Search:
   - Container Instances
3. Click ➕ Create
4. Configure:
   - Container image
   - CPU and memory
   - Networking
   - DNS name
5. Deploy container

---

# 🌐 Networking Options for ACI

| Option | Purpose |
|---|---|
| Public IP 🌍 | Internet access |
| VNet Integration 🌐 | Private network access |

---

# 🔐 Security Features

- Private container registry support
- Secure environment variables
- VNet integration
- Managed identity support

---

# 🚀 Lesson 3: Provision a Container by Using Azure Container Apps

# 📖 What are Azure Container Apps?

Azure Container Apps is a fully managed serverless platform for deploying modern containerized applications and microservices.

---

# 🎯 Purpose of Azure Container Apps

- Run microservices
- Host APIs
- Support event-driven applications
- Enable autoscaling

---

# 🧠 Container Apps vs ACI

| Feature | ACI | Container Apps |
|---|---|---|
| Serverless | ✅ | ✅ |
| Autoscaling 📈 | Limited | Advanced |
| Microservices 🧩 | Basic | Optimized |
| Traffic Management 🌐 | Basic | Advanced |
| Dapr/KEDA Support ⚙️ | No | Yes |

---

# 🧩 Key Features of Container Apps

| Feature | Purpose |
|---|---|
| Autoscaling 📈 | Scale automatically |
| Revision Management 🔄 | Version control |
| Ingress Support 🌐 | HTTP traffic routing |
| Microservices 🧩 | Distributed apps |
| Event-Driven Scaling 🔔 | Scale on events/messages |

---

# 📈 Autoscaling in Container Apps

Container Apps can scale based on:
- HTTP requests
- CPU usage
- Queue messages
- Events

---

# 🛠️ Example Container Apps Architecture

```text
Users
   ↓
Container App
   ↓
Microservices
   ↓
Databases / APIs
``` 

---

# 🔄 Revisions in Container Apps

Each deployment creates a revision.

---

# 🎯 Benefits of Revisions

- Rollback capability
- Safe deployments
- Traffic splitting
- Version management

---

# 🌐 Ingress in Container Apps

Ingress controls external access to applications.

---

# 📌 Types of Ingress

| Type | Purpose |
|---|---|
| External 🌍 | Public access |
| Internal 🔒 | Private access |

---

# 🛠️ Steps to Create Azure Container Apps

1. Open Azure Portal 🌐
2. Search:
   - Container Apps
3. Click ➕ Create
4. Configure:
   - Container image
   - Environment
   - Scaling settings
   - Ingress settings
5. Deploy application

---

# 🔐 Security Best Practices

## ✅ Use Private Container Registries
Protect container images.

---

## ✅ Enable Managed Identity
Avoid storing credentials in containers.

---

## ✅ Restrict Network Access
Use VNets and private endpoints.

---

## ✅ Use Autoscaling
Optimize performance and cost.

---

# 🔗 Container Platform Architecture Overview

```text
Azure Container Registry
        ↓
Container Image
        ↓
ACI / Azure Container Apps
        ↓
Running Containerized Application
```

---

# 🎯 Summary of Module 9 (Part 2)

| Lesson | Focus |
|---|---|
| Azure Container Registry | Store and manage container images |
| Azure Container Instances | Run serverless containers |
| Azure Container Apps | Deploy scalable microservices |

---

# 📝 Final Summary

Module 9 (Part 2) focuses on administering Azure container-based PaaS services. It teaches how to manage container images using Azure Container Registry, run lightweight serverless containers using Azure Container Instances, and deploy scalable microservices and modern applications using Azure Container Apps.
