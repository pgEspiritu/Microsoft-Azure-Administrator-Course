# 🌐 Module 5: Administer Intersite Connectivity

## 📚 Overview

This module focuses on connecting Azure networks and securely accessing Azure resources. It covers:
- 🔗 Virtual Network Peering
- 🛣️ User-Defined Routes (UDRs)
- 🛡️ Azure Bastion

These services help organizations build secure, scalable, and connected cloud infrastructures.

---

# 🧠 Core Concept of Intersite Connectivity

Intersite connectivity allows communication between:
- 🌐 Azure virtual networks
- ☁️ Cloud environments
- 🏢 On-premises networks
- 🔒 Administrative access services

The goal is to provide:
- Secure communication
- Efficient traffic routing
- Simplified remote management

---

# 🔗 Lesson 1: Create and Configure Virtual Network Peering

# 📖 What is Virtual Network Peering?

Virtual Network (VNet) Peering connects two Azure VNets privately through Microsoft’s backbone network.

---

# 🎯 Purpose of VNet Peering

- 🌐 Connect separate VNets
- ⚡ Provide low-latency communication
- 🔒 Keep traffic private
- 🚀 Improve performance

---

# 📌 Benefits of VNet Peering

| Benefit | Description |
|---|---|
| Low Latency ⚡ | Fast communication |
| High Bandwidth 🚀 | Efficient data transfer |
| Private Traffic 🔒 | No public internet exposure |
| Seamless Connectivity 🌐 | VNets communicate as one network |

---

# 🧩 Types of VNet Peering

## 1️⃣ Regional VNet Peering 🌍

Connects VNets within the same Azure region.

### Example
- East US VNet ↔ East US VNet

---

## 2️⃣ Global VNet Peering 🌐

Connects VNets in different Azure regions.

### Example
- East US VNet ↔ Southeast Asia VNet

---

# 🛠️ Steps to Configure VNet Peering

1. Open Azure Portal 🌐
2. Navigate to:
   - Virtual Networks
3. Select a VNet
4. Go to:
   - Peerings
5. Click ➕ Add
6. Select remote VNet
7. Configure permissions
8. Create peering

---

# 🔄 Peering Communication

After peering:
- Resources communicate privately
- Traffic remains inside Microsoft network
- No VPN required

---

# ⚠️ Important Considerations

## ❌ Overlapping IP Address Spaces Not Allowed
Peered VNets must use different IP ranges.

---

## 🔐 NSGs Still Apply
Network Security Groups continue controlling traffic.

---

# 🛣️ Lesson 2: Configure User-Defined Routes (UDRs)

# 📖 What are User-Defined Routes?

User-Defined Routes (UDRs) allow administrators to customize network traffic routing in Azure.

---

# 🧠 Default Azure Routing

Azure automatically creates system routes for:
- Internet traffic 🌍
- Virtual network traffic 🌐
- VPN traffic 🔒

---

# 🎯 Purpose of UDRs

- Control traffic flow
- Force traffic through appliances
- Improve network security
- Implement custom routing paths

---

# 📦 Route Table Concept

A Route Table contains routing rules.

Each rule specifies:
- Destination network
- Next hop type

---

# 📌 Common Next Hop Types

| Next Hop | Purpose |
|---|---|
| Internet 🌍 | Send traffic to internet |
| Virtual Appliance 🔥 | Send traffic to firewall/NVA |
| Virtual Network 🌐 | Internal VNet communication |
| VPN Gateway 🔒 | Route to on-premises network |

---

# 🛠️ Example UDR Scenario

## 🔥 Firewall Routing

A company wants all outbound internet traffic to pass through a firewall appliance.

### Flow
```text
VM → Firewall Appliance → Internet
``` id="udr1"

---

# 🛠️ Steps to Configure UDRs

1. Open Azure Portal 🌐
2. Search:
   - Route Tables
3. Create route table
4. Add routes
5. Associate route table with subnet

---

# 🔐 Benefits of UDRs

- Improved traffic inspection
- Better security control
- Customized network architecture
- Centralized routing management

---

# 🛡️ Lesson 3: Implement Azure Bastion

# 📖 What is Azure Bastion?

Azure Bastion is a fully managed service that provides secure RDP and SSH access to virtual machines directly through the Azure Portal.

---

# 🎯 Purpose of Azure Bastion

- 🔒 Secure VM management
- 🌍 Eliminate public IP exposure
- 🛡️ Protect against attacks
- 🌐 Browser-based remote access

---

# 💻 Supported Protocols

| Protocol | Purpose |
|---|---|
| RDP 🖥️ | Windows VM access |
| SSH 💻 | Linux VM access |

---

# 🔐 Traditional Remote Access Problem

Without Bastion:
- VMs often require public IP addresses
- Open RDP/SSH ports increase attack risks

---

# ✅ Azure Bastion Solution

Azure Bastion:
- Uses private IP connectivity
- Removes need for public VM IPs
- Provides secure browser access

---

# 🧩 How Azure Bastion Works

```text
Administrator
      ↓
Azure Portal
      ↓
Azure Bastion
      ↓
Virtual Machine
``` id="bastion1"

---

# 🛠️ Steps to Deploy Azure Bastion

1. Open Azure Portal 🌐
2. Search:
   - Bastions
3. Click ➕ Create
4. Select:
   - Subscription
   - Resource Group
   - VNet
5. Create AzureBastionSubnet
6. Deploy Bastion

---

# 📌 AzureBastionSubnet Requirement

Azure Bastion requires a dedicated subnet named:

```text
AzureBastionSubnet
``` id="bastion2"

---

# 🔒 Benefits of Azure Bastion

| Benefit | Description |
|---|---|
| No Public IPs 🔐 | Reduced exposure |
| Secure Browser Access 🌐 | Portal-based connectivity |
| Centralized Management ⚙️ | Simplified administration |
| Protection Against Attacks 🛡️ | Reduces brute-force risks |

---

# ⚠️ Best Practices

## ✅ Use Bastion for Administrative Access
Avoid exposing RDP/SSH ports publicly.

---

## ✅ Combine with NSGs
Restrict unnecessary traffic.

---

## ✅ Use Separate Subnets
Organize workloads properly.

---

## ✅ Monitor Access Logs
Track remote access activities.

---

# 🔗 Connectivity Architecture Overview

```text
VNet Peering
      ↓
User-Defined Routes
      ↓
Azure Bastion
      ↓
Secure Resource Access
``` id="connect1"

---

# 🎯 Summary of Module 5

| Lesson | Focus |
|---|---|
| Virtual Network Peering | Connect Azure VNets privately |
| User-Defined Routes | Customize traffic routing |
| Azure Bastion | Secure VM remote access |

---

# 📝 Final Summary

Module 5 focuses on administering intersite connectivity in Azure. It teaches how to connect virtual networks using VNet Peering, control traffic using User-Defined Routes, and securely manage virtual machines using Azure Bastion for secure and scalable cloud networking.
