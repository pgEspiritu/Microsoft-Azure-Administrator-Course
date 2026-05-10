# 💻 Module 8: Administer Azure Virtual Machines

## 📚 Overview

This module focuses on deploying, configuring, and managing Azure Virtual Machines (VMs). It covers:
- 🖥️ Creating Virtual Machines
- ⚙️ Managing VM Sizes
- 💽 Managing VM Disks
- 🌍 Availability Zones and Availability Sets
- 📈 Azure Virtual Machine Scale Sets (VMSS)

Azure Virtual Machines provide scalable and flexible cloud-based computing resources.

---

# 🧠 Core Concept of Azure Virtual Machines

A Virtual Machine (VM) is a software-based computer running in Azure.

It includes:
- Operating System
- CPU
- Memory
- Storage
- Networking

Azure VMs allow organizations to run applications and workloads in the cloud.

---

# 🖥️ Lesson 1: Create a Virtual Machine

# 📖 What is an Azure Virtual Machine?

An Azure VM is an Infrastructure as a Service (IaaS) resource that provides on-demand virtualized computing.

---

# 🎯 Purpose of Virtual Machines

- Run applications
- Host websites
- Perform development/testing
- Support enterprise workloads
- Provide remote desktops

---

# 📦 Components of a VM

| Component | Purpose |
|---|---|
| Virtual CPU 🧠 | Processing power |
| Memory 🧮 | RAM |
| OS Disk 💽 | Operating system storage |
| Data Disks 📀 | Additional storage |
| Network Interface 🌐 | Network connectivity |
| Public IP 🌍 | Internet access |

---

# 🛠️ Steps to Create a VM

1. Open Azure Portal 🌐
2. Search:
   - Virtual Machines
3. Click ➕ Create
4. Configure:
   - Subscription
   - Resource Group
   - VM name
   - Region
   - Availability options
   - Image (Windows/Linux)
   - VM size
   - Authentication
5. Configure disks and networking
6. Review and create

---

# 🔐 Authentication Options

| Method | Description |
|---|---|
| Password 🔑 | Traditional login |
| SSH Key 🔒 | Secure Linux authentication |

---

# 🌍 Common VM Operating Systems

| OS | Example |
|---|---|
| Windows 🪟 | Windows Server 2022 |
| Linux 🐧 | Ubuntu, Red Hat, CentOS |

---

# ⚙️ Lesson 2: Manage Virtual Machine Sizes

# 📖 What is VM Size?

VM size determines the:
- CPU
- Memory
- Storage performance
- Network capability

Of a virtual machine.

---

# 📦 VM Series Examples

| Series | Purpose |
|---|---|
| B-Series 💰 | Budget workloads |
| D-Series ⚙️ | General-purpose |
| E-Series 🧮 | Memory-intensive |
| F-Series ⚡ | Compute-intensive |
| N-Series 🎮 | GPU workloads |

---

# 🎯 Purpose of Resizing VMs

Administrators resize VMs to:
- Improve performance
- Reduce costs
- Match workload requirements

---

# 🔄 Resize Scenario

| Situation | Action |
|---|---|
| High CPU usage ⚡ | Increase VM size |
| Low utilization 💰 | Decrease VM size |

---

# 🛠️ Steps to Resize a VM

1. Open VM in Azure Portal
2. Select:
   - Size
3. Choose new VM size
4. Click ✅ Resize

---

# 💽 Lesson 3: Manage Virtual Machine Disks

# 📖 What are VM Disks?

VM disks provide storage for operating systems and data.

---

# 📦 Types of VM Disks

| Disk Type | Purpose |
|---|---|
| OS Disk 💽 | Stores operating system |
| Data Disk 📀 | Stores application/data files |
| Temporary Disk ⚡ | Short-term storage |

---

# 🔐 Managed Disks

Azure Managed Disks simplify storage management by automatically handling:
- Replication
- Availability
- Scaling

---

# 📊 Disk Performance Types

| Disk Type | Performance |
|---|---|
| Standard HDD 💾 | Low-cost basic storage |
| Standard SSD ⚡ | Balanced performance |
| Premium SSD 🚀 | High-performance workloads |
| Ultra Disk 🔥 | Extremely high IOPS |

---

# 🛠️ Disk Management Tasks

- Add disks ➕
- Resize disks 🔄
- Detach disks ❌
- Snapshot disks 📸
- Encrypt disks 🔐

---

# 📸 Disk Snapshots

Snapshots create point-in-time backups of disks.

---

# 🎯 Benefits
- Backup protection
- Disaster recovery
- Testing and rollback

---

# 🌍 Lesson 4: Deploy Virtual Machines to Availability Zones and Availability Sets

# 📖 What are Availability Zones?

Availability Zones are physically separate datacenters within an Azure region.

---

# 🎯 Purpose of Availability Zones

- Improve fault tolerance
- Protect against datacenter failures
- Increase application availability

---

# 🛠️ Example

```text
Zone 1 → VM1
Zone 2 → VM2
Zone 3 → VM3
``` id="az1"

---

# 📖 What are Availability Sets?

Availability Sets distribute VMs across:
- Fault Domains
- Update Domains

To minimize downtime.

---

# 🧩 Availability Set Concepts

| Concept | Purpose |
|---|---|
| Fault Domain 🔌 | Protects against hardware failure |
| Update Domain 🔄 | Protects during maintenance updates |

---

# 🛠️ Example Availability Set

```text
Availability Set
   ├── VM1
   ├── VM2
   └── VM3
``` id="aset1"

---

# 🌐 Availability Zones vs Availability Sets

| Feature | Availability Zones | Availability Sets |
|---|---|---|
| Physical Separation 🌍 | Yes | No |
| Datacenter Protection 🏢 | Yes | Limited |
| Regional Distribution 🌐 | Multiple zones | Single datacenter |

---

# 📈 Lesson 5: Deploy and Configure Azure Virtual Machine Scale Sets (VMSS)

# 📖 What is VM Scale Set (VMSS)?

VM Scale Sets allow automatic deployment and management of multiple identical VMs.

---

# 🎯 Purpose of VMSS

- Automatic scaling
- High availability
- Load balancing
- Simplified management

---

# 📦 VMSS Features

| Feature | Purpose |
|---|---|
| Autoscaling 📈 | Automatically add/remove VMs |
| Load Balancing ⚖️ | Distribute traffic |
| High Availability 🌍 | Improve uptime |
| Centralized Management ⚙️ | Manage multiple VMs easily |

---

# 📈 Autoscaling Concept

VMSS automatically adjusts VM count based on:
- CPU usage
- Memory usage
- Traffic load
- Schedules

---

# 🛠️ Example Scaling Scenario

| Condition | Action |
|---|---|
| CPU > 80% ⚡ | Add more VMs |
| CPU < 30% 💰 | Remove excess VMs |

---

# 🔗 VMSS Architecture

```text
Internet Users
      ↓
Load Balancer
      ↓
VM Scale Set
   ├── VM1
   ├── VM2
   ├── VM3
``` id="vmss1"

---

# 🛠️ Steps to Create VMSS

1. Open Azure Portal 🌐
2. Search:
   - Virtual Machine Scale Sets
3. Click ➕ Create
4. Configure:
   - VM image
   - VM size
   - Scaling rules
   - Load balancer
5. Deploy VMSS

---

# 🔐 Best Practices for Azure VMs

## ✅ Use Availability Zones
Improve fault tolerance.

---

## ✅ Use Managed Disks
Simplify disk management.

---

## ✅ Enable Backups
Protect VM data.

---

## ✅ Use NSGs
Secure VM network traffic.

---

## ✅ Implement Monitoring
Track VM performance and health.

---

# 🎯 Summary of Module 8

| Lesson | Focus |
|---|---|
| Create Virtual Machines | Deploy Azure VMs |
| Manage VM Sizes | Adjust performance and cost |
| Manage VM Disks | Configure VM storage |
| Availability Zones/Sets | Improve availability |
| VM Scale Sets | Automatic scaling and management |

---

# 📝 Final Summary

Module 8 focuses on administering Azure Virtual Machines. It teaches how to deploy and manage VMs, configure compute and storage resources, improve availability using Availability Zones and Availability Sets, and implement scalable infrastructure using Virtual Machine Scale Sets for modern cloud environments.
