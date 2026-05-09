# 🌐 Module 6: Administer Network Traffic

## 📚 Overview

This module focuses on managing and distributing network traffic in Azure. It covers:
- ⚖️ Azure Load Balancer
- 🌍 Public and Internal Load Balancers
- 🚪 Azure Application Gateway

These services improve:
- ⚡ Performance
- 🔄 High availability
- 🌐 Scalability
- 🛡️ Application delivery and security

---

# 🧠 Core Concept of Network Traffic Administration

Azure network traffic administration ensures:
- Requests are distributed efficiently
- Applications remain available
- Traffic is routed securely
- Services can scale automatically

---

# ⚖️ Lesson 1: Configure an Internal or Public Load Balancer

# 📖 What is Azure Load Balancer?

Azure Load Balancer is a Layer 4 (Transport Layer) load balancing service that distributes incoming and outgoing traffic across multiple resources.

---

# 🎯 Purpose of Azure Load Balancer

- ⚡ Improve application availability
- 🔄 Distribute traffic evenly
- 🚀 Increase scalability
- 🛡️ Prevent single points of failure

---

# 🧩 Types of Azure Load Balancer

| Type | Purpose |
|---|---|
| Public Load Balancer 🌍 | Handles internet-facing traffic |
| Internal Load Balancer 🔒 | Handles private/internal traffic |

---

# 🌍 Public Load Balancer

## 📖 Definition

A Public Load Balancer distributes traffic from the internet to Azure resources.

---

## 🛠️ Example Scenario

```text
Internet Users
      ↓
Public Load Balancer
      ↓
Web Servers
``` id="plb1"

---

## 🎯 Use Cases

- Public websites
- APIs
- Internet-facing applications

---

## 🔑 Features

- Public IP address
- External accessibility
- Supports TCP and UDP traffic

---

# 🔒 Internal Load Balancer (ILB)

## 📖 Definition

An Internal Load Balancer distributes traffic within a private Azure network.

---

## 🛠️ Example Scenario

```text
Application Servers
      ↓
Internal Load Balancer
      ↓
Database Servers
``` id="ilb1"

---

## 🎯 Use Cases

- Internal applications
- Backend services
- Database traffic

---

## 🔑 Features

- Private IP address only
- Internal communication
- No internet exposure

---

# ⚙️ Components of Azure Load Balancer

| Component | Purpose |
|---|---|
| Frontend IP 🖧 | Receives incoming traffic |
| Backend Pool 🖥️ | Group of servers/resources |
| Health Probe ❤️ | Checks resource health |
| Load Balancing Rule ⚖️ | Defines traffic distribution |

---

# ❤️ Health Probes

Health probes monitor backend resource availability.

---

## 🎯 Purpose

- Detect unhealthy servers
- Route traffic only to healthy resources

---

## 📌 Probe Types

| Type | Description |
|---|---|
| TCP Probe 🔌 | Tests TCP connection |
| HTTP Probe 🌍 | Tests web response |

---

# ⚖️ Load Balancing Rules

Rules determine:
- Incoming port
- Backend port
- Protocol
- Distribution behavior

---

# 🛠️ Steps to Create a Load Balancer

1. Open Azure Portal 🌐
2. Search:
   - Load Balancers
3. Click ➕ Create
4. Choose:
   - Public or Internal
5. Configure frontend IP
6. Add backend pool
7. Configure health probes
8. Create load balancing rules
9. Deploy

---

# 🚀 Benefits of Azure Load Balancer

- High availability
- Improved performance
- Automatic traffic distribution
- Fault tolerance

---

# 🚪 Lesson 2: Introduction to Azure Application Gateway

# 📖 What is Azure Application Gateway?

Azure Application Gateway is a Layer 7 (Application Layer) load balancer for web applications.

It provides:
- Intelligent traffic routing
- Web application protection
- SSL termination
- Advanced web traffic management

---

# 🎯 Purpose of Application Gateway

- 🌍 Manage HTTP/HTTPS traffic
- 🛡️ Protect web applications
- ⚡ Improve application delivery
- 🔀 Route traffic intelligently

---

# 🧠 Layer 4 vs Layer 7

| Feature | Load Balancer | Application Gateway |
|---|---|---|
| OSI Layer | Layer 4 | Layer 7 |
| Traffic Type | TCP/UDP | HTTP/HTTPS |
| Intelligent Routing | Limited | Advanced |
| Web Protection | No | Yes |

---

# 🔑 Key Features of Application Gateway

## 🌐 URL-Based Routing

Routes traffic based on URL paths.

### Example

```text
contoso.com/images → Image Server
contoso.com/api → API Server
``` id="appgw1"

---

## 🔄 Multi-Site Hosting

Hosts multiple websites using one gateway.

### Example
- app1.contoso.com
- app2.contoso.com

---

## 🔒 SSL Termination

Handles HTTPS encryption at the gateway level.

### Benefits
- Reduced backend workload
- Simplified certificate management

---

## 🛡️ Web Application Firewall (WAF)

Protects applications from common attacks.

---

# 🚨 Common Threats Blocked by WAF

| Threat | Description |
|---|---|
| SQL Injection 💉 | Database attack |
| Cross-Site Scripting (XSS) ⚠️ | Script injection |
| Malicious Requests 🚫 | Unauthorized traffic |

---

# 🧩 Components of Application Gateway

| Component | Purpose |
|---|---|
| Frontend IP 🌍 | Receives client traffic |
| Listener 👂 | Monitors incoming requests |
| Backend Pool 🖥️ | Web servers/resources |
| Routing Rules 🔀 | Direct traffic |
| WAF 🛡️ | Application protection |

---

# 🛠️ Application Gateway Traffic Flow

```text
Client Request
      ↓
Application Gateway
      ↓
Routing Rules
      ↓
Backend Web Servers
``` id="appgw2"

---

# ⚙️ Steps to Create an Application Gateway

1. Open Azure Portal 🌐
2. Search:
   - Application Gateway
3. Click ➕ Create
4. Configure:
   - Frontend IP
   - Backend pool
   - Listener
   - Routing rules
5. Enable WAF (optional)
6. Deploy

---

# 🔒 Benefits of Application Gateway

- Intelligent traffic routing
- Web application security
- SSL offloading
- Centralized web traffic management
- High availability

---

# ⚠️ Best Practices

## ✅ Use Health Probes
Ensure backend services remain healthy.

---

## ✅ Enable WAF
Protect web applications from attacks.

---

## ✅ Use Internal Load Balancers for Backend Services
Avoid exposing internal systems publicly.

---

## ✅ Use HTTPS
Secure client communication.

---

# 🔗 Network Traffic Architecture Overview

```text
Internet Users
      ↓
Public Load Balancer / Application Gateway
      ↓
Backend Servers
      ↓
Internal Load Balancer
      ↓
Database Servers
``` id="traffic1"

---

# 🎯 Summary of Module 6

| Lesson | Focus |
|---|---|
| Configure Internal/Public Load Balancer | Distribute network traffic |
| Introduction to Application Gateway | Intelligent web traffic routing and security |

---

# 📝 Final Summary

Module 6 focuses on administering Azure network traffic services. It teaches how to distribute traffic using Azure Load Balancer and how to manage and protect web applications using Azure Application Gateway to ensure scalable, secure, and highly available cloud applications.
