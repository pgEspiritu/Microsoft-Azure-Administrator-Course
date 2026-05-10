# 💾 Module 7: Administer Azure Storage

## 📚 Overview

This module focuses on administering and securing Azure Storage services. It covers:
- 🏗️ Storage Accounts
- 🔄 Storage Redundancy
- 🔐 Storage Encryption
- 🛡️ Firewalls and Virtual Networks
- 🔑 Shared Access Signature (SAS) Tokens
- 📦 Blob Storage
- ♻️ Blob Lifecycle Management
- 📊 Storage Tiers
- 📁 Azure File Shares

Azure Storage provides scalable, durable, secure, and highly available cloud storage services.

---

# 🧠 Core Concept of Azure Storage

Azure Storage is Microsoft’s cloud storage platform used to store:
- 📄 Files
- 🖼️ Images
- 📹 Videos
- 🗄️ Databases
- 📦 Backups
- 📊 Structured and unstructured data

---

# 📦 Types of Azure Storage Services

| Storage Service | Purpose |
|---|---|
| Blob Storage 🧱 | Store unstructured data |
| File Storage 📁 | Shared file access |
| Queue Storage 📬 | Messaging storage |
| Table Storage 📊 | NoSQL structured data |
| Disk Storage 💽 | VM disks |

---

# 🏗️ Lesson 1: Create and Configure Storage Accounts

# 📖 What is a Storage Account?

A Storage Account is a container that provides access to Azure Storage services.

---

# 🎯 Purpose of Storage Accounts

- Store cloud data
- Organize storage services
- Manage access and security
- Configure redundancy and performance

---

# 📌 Storage Account Types

| Type | Purpose |
|---|---|
| General-purpose v2 (GPv2) ⭐ | Recommended for most workloads |
| Blob Storage 🧱 | Blob-focused storage |
| Premium Storage ⚡ | High-performance workloads |

---

# 🛠️ Steps to Create a Storage Account

1. Open Azure Portal 🌐
2. Search:
   - Storage Accounts
3. Click ➕ Create
4. Configure:
   - Subscription
   - Resource Group
   - Storage account name
   - Region
   - Performance type
   - Redundancy
5. Review and create

---

# ⚙️ Storage Account Components

| Component | Purpose |
|---|---|
| Containers 📦 | Store blobs |
| File Shares 📁 | Shared files |
| Queues 📬 | Message storage |
| Tables 📊 | Structured data |

---

# 🔄 Lesson 2: Configure Azure Storage Redundancy

# 📖 What is Storage Redundancy?

Redundancy replicates storage data to protect against:
- Hardware failures
- Datacenter outages
- Regional disasters

---

# 🛡️ Types of Storage Redundancy

| Redundancy Type | Description |
|---|---|
| LRS 🔒 | Locally Redundant Storage |
| ZRS 🌍 | Zone-Redundant Storage |
| GRS 🌐 | Geo-Redundant Storage |
| RA-GRS 📖 | Read-access Geo-Redundant Storage |
| GZRS ⚡ | Geo-zone Redundant Storage |

---

# 📌 Redundancy Descriptions

## 🔒 LRS (Locally Redundant Storage)
- Copies data within one datacenter
- Lowest cost

---

## 🌍 ZRS (Zone-Redundant Storage)
- Replicates data across availability zones

---

## 🌐 GRS (Geo-Redundant Storage)
- Replicates data to another Azure region

---

## 📖 RA-GRS
- Provides read access to secondary region

---

# 🎯 Benefits of Redundancy

- High availability
- Disaster recovery
- Data durability
- Business continuity

---

# 🔐 Lesson 3: Configure Azure Storage Account Encryption

# 📖 What is Storage Encryption?

Azure automatically encrypts data at rest.

---

# 🔑 Encryption Types

| Encryption Type | Description |
|---|---|
| Microsoft-Managed Keys 🔐 | Azure manages keys |
| Customer-Managed Keys 🗝️ | Organization controls keys |

---

# 🎯 Purpose of Encryption

- Protect sensitive data
- Meet compliance requirements
- Prevent unauthorized access

---

# 🛡️ Encryption Scope

Azure encrypts:
- Blob data
- File shares
- Queue storage
- Table storage

---

# 🔒 Lesson 4: Configure Azure Storage Firewalls and Virtual Networks

# 📖 What are Storage Firewalls?

Storage Firewalls restrict access to storage accounts.

---

# 🎯 Purpose

- Prevent unauthorized access
- Limit network exposure
- Improve security

---

# 📌 Access Options

| Option | Description |
|---|---|
| Public Access 🌍 | Open internet access |
| Selected Networks 🔒 | Restricted network access |
| Private Endpoints 🛡️ | Private network access |

---

# 🌐 Virtual Network Integration

Storage accounts can allow access only from:
- Specific VNets
- Approved IP addresses
- Trusted services

---

# 🛠️ Example Scenario

```text
Virtual Machines
      ↓
Virtual Network
      ↓
Storage Account
``` id="storagefw1"

---

# 🔑 Lesson 5: Create and Use Shared Access Signature (SAS) Tokens

# 📖 What is a SAS Token?

A Shared Access Signature (SAS) token grants temporary delegated access to Azure Storage resources.

---

# 🎯 Purpose of SAS Tokens

- Share resources securely
- Provide limited access
- Avoid exposing storage account keys

---

# 📌 SAS Permissions

| Permission | Description |
|---|---|
| Read 👁️ | View data |
| Write ✏️ | Modify data |
| Delete 🗑️ | Remove data |
| List 📋 | View resource list |

---

# ⏰ SAS Features

- Temporary expiration
- Limited permissions
- Scoped access

---

# 🛠️ Example SAS Usage

```text
User receives secure temporary link to upload/download files.
``` id="sas1"

---

# 📦 Lesson 6: Create and Configure a Container in Blob Storage

# 📖 What is Blob Storage?

Blob Storage stores unstructured data such as:
- Images
- Videos
- Documents
- Backups

---

# 📦 What is a Container?

A container organizes blobs within a storage account.

---

# 🛠️ Steps to Create a Blob Container

1. Open Storage Account
2. Select:
   - Containers
3. Click ➕ Container
4. Enter container name
5. Configure access level
6. Create container

---

# 🔓 Container Access Levels

| Access Level | Description |
|---|---|
| Private 🔒 | No public access |
| Blob 🌍 | Public access to blobs only |
| Container 📂 | Public access to entire container |

---

# ♻️ Lesson 7: Configure Blob Lifecycle Management

# 📖 What is Lifecycle Management?

Lifecycle management automatically manages blob storage based on rules.

---

# 🎯 Purpose

- Reduce storage costs
- Automate data management
- Archive old data

---

# 📌 Lifecycle Actions

| Action | Purpose |
|---|---|
| Move to Cool Tier ❄️ | Lower storage cost |
| Move to Archive Tier 📦 | Long-term storage |
| Delete Old Blobs 🗑️ | Cleanup unused data |

---

# 🛠️ Example Policy

```text
Move blobs to Cool tier after 30 days.
Delete blobs after 365 days.
``` id="lifecycle1"

---

# 📊 Lesson 8: Configure Storage Tiers

# 📖 What are Storage Tiers?

Storage tiers optimize storage costs based on access frequency.

---

# 📌 Blob Storage Tiers

| Tier | Purpose |
|---|---|
| Hot 🔥 | Frequently accessed data |
| Cool ❄️ | Infrequently accessed data |
| Archive 📦 | Rarely accessed long-term storage |

---

# 🎯 Choosing the Right Tier

| Scenario | Recommended Tier |
|---|---|
| Active application files ⚡ | Hot |
| Monthly backups 💾 | Cool |
| Compliance archives 🗄️ | Archive |

---

# 📁 Lesson 9: Create and Configure a File Share in Azure Storage

# 📖 What is Azure File Share?

Azure File Share provides cloud-based shared file storage using the SMB protocol.

---

# 🎯 Purpose

- Shared access across devices
- Centralized file storage
- Hybrid cloud file sharing

---

# 🛠️ Steps to Create a File Share

1. Open Storage Account
2. Select:
   - File Shares
3. Click ➕ File Share
4. Enter:
   - Share name
   - Quota
5. Create file share

---

# 💻 Access Methods

| Method | Description |
|---|---|
| SMB 📂 | Windows/Linux shared access |
| Azure Portal 🌐 | Web management |
| Azure CLI 💻 | Command-line access |

---

# 🔗 Example File Share Architecture

```text
Users / Virtual Machines
         ↓
Azure File Share
         ↓
Storage Account
``` id="fileshare1"

---

# 🔐 Best Practices for Azure Storage

## ✅ Enable Encryption
Protect stored data.

---

## ✅ Use Redundancy
Ensure high availability.

---

## ✅ Restrict Network Access
Use firewalls and VNets.

---

## ✅ Use SAS Instead of Storage Keys
Provide secure temporary access.

---

## ✅ Use Lifecycle Policies
Reduce storage costs automatically.

---

# 🎯 Summary of Module 7

| Lesson | Focus |
|---|---|
| Create Storage Accounts | Configure cloud storage |
| Configure Redundancy | Protect against failures |
| Configure Encryption | Secure stored data |
| Configure Firewalls/VNets | Restrict access |
| SAS Tokens | Temporary delegated access |
| Blob Containers | Organize blob data |
| Lifecycle Management | Automate storage optimization |
| Storage Tiers | Optimize costs |
| Azure File Shares | Shared cloud file storage |

---

# 📝 Final Summary

Module 7 focuses on administering Azure Storage services. It teaches how to create and secure storage accounts, configure redundancy and encryption, manage network access, use SAS tokens, organize Blob Storage, automate lifecycle management, optimize storage tiers, and create Azure File Shares for scalable and secure cloud storage solutions.
