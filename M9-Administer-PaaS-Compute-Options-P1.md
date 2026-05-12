# ☁️ Module 9: Administer PaaS Compute Options

## 📚 Overview

This module focuses on administering Azure Platform as a Service (PaaS) compute solutions using Azure App Service. It covers:
- 🏗️ App Service Plans
- 📈 Scaling App Services
- 🌐 Creating App Services
- 🔄 Deployment Slots
- 🌐 Networking Configuration

Azure App Service allows developers to host web applications, APIs, and backend services without managing infrastructure.

---

# 🧠 Core Concept of PaaS

## 📖 What is PaaS?

Platform as a Service (PaaS) provides a cloud platform where developers can:
- Deploy applications
- Run web services
- Manage APIs

Without managing:
- Physical servers
- Operating systems
- Infrastructure maintenance

---

# 🎯 Benefits of PaaS

- ⚡ Faster application deployment
- 🔧 Reduced infrastructure management
- 📈 Automatic scaling
- 🔐 Built-in security features
- 🌍 High availability

---

# 🏗️ Lesson 1: Provision an App Service Plan

# 📖 What is an App Service Plan?

An App Service Plan defines the:
- 💻 Compute resources
- ⚙️ Pricing tier
- 📈 Scaling capabilities
- 🌍 Region

Used by Azure App Services.

---

# 🧩 Relationship

```text
App Service Plan
      ↓
Hosts
      ↓
App Services
```

---

# 📦 App Service Plan Pricing Tiers

| Tier | Purpose |
|---|---|
| Free 🆓 | Testing and learning |
| Shared 🤝 | Low-cost shared resources |
| Basic ⚙️ | Small production workloads |
| Standard 🌐 | Production apps with scaling |
| Premium 🚀 | High-performance workloads |
| Isolated 🔒 | Dedicated environments |

---

# 🎯 Purpose of App Service Plans

- Provide compute resources
- Define scaling limits
- Determine pricing and performance

---

# 🛠️ Steps to Create an App Service Plan

1. Open Azure Portal 🌐
2. Search:
   - App Service Plans
3. Click ➕ Create
4. Configure:
   - Subscription
   - Resource Group
   - Name
   - Region
   - Pricing tier
5. Review and create

---

# 📈 Lesson 2: Configure Scaling for an App Service Plan

# 📖 What is Scaling?

Scaling increases or decreases application resources based on workload demand.

---

# 🧩 Types of Scaling

| Scaling Type | Description |
|---|---|
| Vertical Scaling ⬆️ | Increase VM size/resources |
| Horizontal Scaling ↔️ | Increase number of instances |

---

# ⬆️ Vertical Scaling (Scale Up)

Improves performance by increasing:
- CPU
- Memory
- Storage

---

# ↔️ Horizontal Scaling (Scale Out)

Adds more application instances to handle increased traffic.

---

# 📈 Autoscaling

Azure can automatically scale App Services based on:
- CPU usage
- Memory usage
- HTTP queue length
- Schedules

---

# 🛠️ Example Autoscale Rule

| Condition | Action |
|---|---|
| CPU > 70% ⚡ | Add instance |
| CPU < 30% 💰 | Remove instance |

---

# 🛠️ Steps to Configure Scaling

1. Open App Service Plan
2. Select:
   - Scale Up
   - Scale Out
3. Configure scaling settings
4. Save changes

---

# 🌐 Lesson 3: Create App Services

# 📖 What is Azure App Service?

Azure App Service is a fully managed PaaS platform for hosting:
- Web apps
- REST APIs
- Mobile backends

---

# 🎯 Supported Technologies

| Technology | Examples |
|---|---|
| .NET ⚙️ | ASP.NET |
| Java ☕ | Spring |
| Node.js 🟢 | Express |
| Python 🐍 | Flask/Django |
| PHP 🐘 | Laravel |

---

# 🛠️ Steps to Create an App Service

1. Open Azure Portal 🌐
2. Search:
   - App Services
3. Click ➕ Create
4. Configure:
   - Subscription
   - Resource Group
   - App name
   - Runtime stack
   - Region
   - App Service Plan
5. Deploy application

---

# 🌍 App Service Features

| Feature | Purpose |
|---|---|
| Custom Domains 🌐 | Use personal domain names |
| SSL Certificates 🔒 | Secure HTTPS access |
| Deployment Slots 🔄 | Safe deployments |
| Autoscaling 📈 | Dynamic scaling |
| CI/CD Integration ⚙️ | Automated deployments |

---

# 🔄 Lesson 4: Configure Deployment Slots for an App Service

# 📖 What are Deployment Slots?

Deployment Slots are separate live environments within an App Service.

---

# 🎯 Purpose of Deployment Slots

- Test updates safely
- Minimize downtime
- Support blue-green deployments
- Rollback failed deployments

---

# 📦 Common Deployment Slots

| Slot | Purpose |
|---|---|
| Production 🌍 | Live application |
| Staging 🧪 | Testing environment |
| Development ⚙️ | Development environment |

---

# 🔁 Slot Swap Concept

A slot swap exchanges:
- Staging app
- Production app

Without downtime.

---

# 🛠️ Deployment Slot Workflow

```text
Deploy to Staging
      ↓
Test Application
      ↓
Swap with Production
``` 

---

# 🛠️ Steps to Create Deployment Slots

1. Open App Service
2. Select:
   - Deployment Slots
3. Click ➕ Add Slot
4. Configure slot name
5. Deploy application to slot
6. Swap slots when ready

---

# 🌐 Lesson 5: Configure Networking Settings for an App Service

# 📖 Why Configure Networking?

Networking settings control:
- Access
- Security
- Connectivity

For App Services.

---

# 🔐 Networking Features

| Feature | Purpose |
|---|---|
| Access Restrictions 🚫 | Restrict traffic |
| VNet Integration 🌐 | Connect to VNets |
| Private Endpoints 🔒 | Private connectivity |
| Hybrid Connections 🔗 | Connect on-premises resources |

---

# 🌐 VNet Integration

Allows App Services to securely access:
- Databases
- APIs
- Internal services

Inside Azure VNets.

---

# 🔒 Private Endpoints

Private Endpoints allow App Services to use:
- Private IP addresses
- Secure internal communication

Without internet exposure.

---

# 🚫 Access Restrictions

Administrators can:
- Allow trusted IPs
- Block unauthorized traffic
- Restrict regions or networks

---

# 🛠️ Example App Service Network Flow

```text
Internet Users
      ↓
Azure App Service
      ↓
VNet Integration
      ↓
Database / Backend Services
```

---

# 🔐 Security Best Practices

## ✅ Enable HTTPS
Secure client communication.

---

## ✅ Use Deployment Slots
Avoid downtime during updates.

---

## ✅ Configure Autoscaling
Handle traffic spikes automatically.

---

## ✅ Restrict Access
Limit traffic using IP restrictions and VNets.

---

## ✅ Use Private Endpoints
Secure internal communication.

---

# 🎯 Summary of Module 9

| Lesson | Focus |
|---|---|
| Provision App Service Plan | Define compute resources |
| Configure Scaling | Scale applications dynamically |
| Create App Services | Host web applications |
| Configure Deployment Slots | Safe application deployment |
| Configure Networking Settings | Secure application connectivity |

---

# 📝 Final Summary

Module 9 focuses on administering Azure PaaS compute options using Azure App Service. It teaches how to provision App Service Plans, configure scaling, deploy web applications, manage deployment slots, and secure application networking for scalable and highly available cloud-hosted applications.
