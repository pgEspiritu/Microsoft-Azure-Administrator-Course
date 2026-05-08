# 🌐 Module 4: Administer Virtual Networking

## 📚 Overview

This module focuses on configuring and managing Azure virtual networking services. It covers:
- 🌐 Virtual Networks (VNets)
- 🧩 Subnets
- 🔐 Network Security Groups (NSGs)
- 👥 Application Security Groups (ASGs)
- 📡 Azure DNS

These services help organizations build secure, scalable, and connected cloud environments.

---

# 🧠 Core Concept of Azure Virtual Networking

Azure Virtual Networking allows Azure resources to securely communicate with:
- ☁️ Other Azure resources
- 🌍 The internet
- 🏢 On-premises networks

It functions similarly to a traditional network but operates in the cloud.

---

# 🌐 Lesson 1: Create and Configure Virtual Networks and Subnets

# 📖 What is a Virtual Network (VNet)?

A Virtual Network (VNet) is a private network in Azure that allows Azure resources to securely communicate with each other.

---

## 🎯 Purpose of VNets

- 🖧 Isolate Azure resources
- 🔐 Secure communications
- 🌍 Connect cloud and on-premises environments
- 🚦 Control network traffic

---

# 🧩 Components of a VNet

| Component | Description |
|---|---|
| Address Space | IP address range for the VNet |
| Subnet | Smaller network segment the VNet |
| Network Interface | Connects resources to the network |
| Route Tables | Controls traffic routing |

---

# 📌 Example VNet Structure

```text
Virtual Network: 10.0.0.0/16
   ├── Subnet A: 10.0.1.0/24
   ├── Subnet B: 10.0.2.0/24
   └── Subnet C: 10.0.3.0/24
``` 

---

# 🧩 What is a Subnet?

A subnet is a smaller network segment within a VNet.

---

## 🎯 Purpose of Subnets

- 🔐 Improve security
- 📊 Organize resources
- 🚦 Separate workloads
- ⚡ Improve traffic management

---

## 🛠️ Example Use Cases

| Subnet | Purpose |
|---|---|
| Web Subnet 🌍 | Web servers |
| App Subnet ⚙️ | Application servers |
| DB Subnet 🗄️ | Databases |

---

# 🛠️ Steps to Create a VNet

1. Open Azure Portal 🌐
2. Search for:
   - Virtual Networks
3. Click ➕ Create
4. Configure:
   - Name
   - Region
   - Address space
5. Add subnets
6. Review and create

---

# 🔗 VNet Peering

## 📖 What is VNet Peering?

VNet Peering connects two Azure virtual networks privately.

---

## ✅ Benefits

- Low latency
- High bandwidth
- Private communication
- No internet exposure

---

# 🔐 Lesson 2: Create and Configure Network Security Groups (NSGs) and ASGs

# 🛡️ What is a Network Security Group (NSG)?

An NSG is a security feature that filters inbound and outbound network traffic.

---

# 🚦 NSG Rules

NSGs use rules to:
- Allow traffic ✅
- Deny traffic ❌

---

## 📌 NSG Rule Components

| Component | Description |
|---|---|
| Priority | Rule order |
| Source | Traffic origin |
| Destination | Traffic target |
| Port | Communication port |
| Protocol | TCP/UDP |
| Action | Allow or Deny |

---

# 🛠️ Example NSG Rules

| Rule | Purpose |
|---|---|
| Allow HTTP (Port 80) 🌍 | Web traffic |
| Allow HTTPS (Port 443) 🔒 | Secure web traffic |
| Deny All Other Traffic ❌ | Block unauthorized access |

---

# 🎯 Purpose of NSGs

- 🔐 Secure virtual machines
- 🚦 Control traffic flow
- 🛡️ Protect applications
- 📊 Segment networks

---

# 📍 NSG Association

NSGs can be associated with:
- 🧩 Subnets
- 💻 Network interfaces (NICs)

---

# 👥 What is an Application Security Group (ASG)?

ASGs logically group virtual machines based on applications.

---

## 🎯 Purpose of ASGs

- Simplify NSG management
- Group servers by role
- Reduce complex IP-based rules

---

# 🛠️ Example ASG Scenario

| ASG Name | Members |
|---|---|
| Web-ASG 🌍 | Web servers |
| App-ASG ⚙️ | Application servers |
| DB-ASG 🗄️ | Database servers |

---

# 🔗 NSG + ASG Example

Rule:
> Allow traffic from Web-ASG to App-ASG on Port 443.

This avoids manually entering IP addresses.

---

# 📡 Lesson 3: Configure Azure DNS

# 📖 What is Azure DNS?

Azure DNS is a hosting service for DNS domains using Azure infrastructure.

---

# 🌍 What is DNS?

DNS (Domain Name System) translates domain names into IP addresses.

---

## 🧩 Example

```text
www.contoso.com → 20.45.10.5
``` id="dns1"

---

# 🎯 Purpose of Azure DNS

- 🌐 Host DNS zones
- ⚡ Fast domain resolution
- 🔐 Secure DNS management
- ☁️ Integrate with Azure services

---

# 📦 DNS Components

| Component | Description |
|---|---|
| DNS Zone | Container for DNS records |
| DNS Record | Maps names to IP addresses |
| Name Server | Resolves DNS queries |

---

# 📌 Common DNS Record Types

| Record Type | Purpose |
|---|---|
| A Record | Maps hostname to IPv4 address |
| AAAA Record | Maps hostname to IPv6 address |
| CNAME | Alias for another domain |
| MX Record | Mail server configuration |
| TXT Record | Verification and text data |

---

# 🛠️ Steps to Configure Azure DNS

1. Open Azure Portal 🌐
2. Search:
   - DNS Zones
3. Click ➕ Create
4. Enter:
   - Domain name
5. Create DNS records
6. Configure name servers

---

# 🔗 Public vs Private DNS

| Type | Purpose |
|---|---|
| Public DNS 🌍 | Internet-facing domains |
| Private DNS 🔒 | Internal Azure network resolution |

---

# 🔒 Azure Private DNS

Used for:
- Internal name resolution
- Private VNets
- Secure communication

---

# 🧠 Best Practices for Virtual Networking

## ✅ Use Subnets for Segmentation
Separate workloads into different subnets.

---

## ✅ Apply NSGs
Restrict unnecessary traffic.

---

## ✅ Use ASGs
Simplify security rule management.

---

## ✅ Implement Private DNS
Secure internal communication.

---

## ✅ Plan IP Addressing Carefully
Avoid overlapping address spaces.

---

# 🔗 Networking Relationship Overview

```text
Virtual Network (VNet)
   ├── Subnets
   │     ├── Virtual Machines
   │     ├── NSGs
   │     └── ASGs
   │
   └── Azure DNS
``` id="netflow1"

---

# 🎯 Summary of Module 4

| Lesson | Focus |
|---|---|
| Create and Configure VNets and Subnets | Build private cloud networks |
| Configure NSGs and ASGs | Secure and organize traffic |
| Configure Azure DNS | Manage domain name resolution |

---

# 📝 Final Summary

Module 4 focuses on administering Azure virtual networking services. It teaches how to create secure cloud networks using VNets and subnets, control traffic using NSGs and ASGs, and manage name resolution with Azure DNS to support scalable and secure Azure environments.
