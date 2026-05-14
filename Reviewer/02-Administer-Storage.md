# AZ-104 Reviewer
# Domain: Administer Storage

---

# 📚 Exam Coverage

This domain covers:
- Storage Accounts
- Azure Blob Storage
- Azure Files
- Storage Security
- Storage Replication
- Shared Access Signatures (SAS)
- Access Keys
- Azure Storage Explorer
- AzCopy
- Lifecycle Management
- Import/Export Jobs

Weight in Exam:
15–20%

---

# ☁️ Azure Storage Overview

Azure Storage is Microsoft's cloud storage solution.

It provides:
- High availability
- Scalability
- Durability
- Security

---

# 🔹 Storage Services

| Service | Purpose |
|---|---|
| Blob Storage | Store unstructured data |
| Azure Files | SMB/NFS file shares |
| Queue Storage | Message storage |
| Table Storage | NoSQL key-value data |

---

# 🏢 Storage Accounts

A storage account provides a namespace for Azure Storage services.

Example:
```text
mystorageaccount
```

---

# 🔹 Storage Account Types

| Type | Description |
|---|---|
| General Purpose v2 (GPv2) | Recommended standard account |
| Premium | High-performance workloads |

---

# 🔹 Storage Account Performance Tiers

| Tier | Description |
|---|---|
| Standard | HDD-based |
| Premium | SSD-based |

---

# 🔹 Storage Account Endpoints

Example:
```text
https://mystorage.blob.core.windows.net
```

---

# 🔹 Important Storage Features

| Feature | Purpose |
|---|---|
| Encryption | Protect data |
| Replication | Redundancy |
| Access Control | Secure access |
| Lifecycle Management | Automated tiering |

---

# 🔄 Storage Replication

Provides data redundancy and availability.

---

# 🔹 Replication Types

| Replication | Description |
|---|---|
| LRS | Locally Redundant Storage |
| ZRS | Zone-Redundant Storage |
| GRS | Geo-Redundant Storage |
| RA-GRS | Read-access Geo-Redundant Storage |
| GZRS | Geo-zone-redundant |
| RA-GZRS | Read-access geo-zone-redundant |

---

# 🔹 Replication Comparison

| Type | Zones Protected | Region Protected |
|---|---|---|
| LRS | ❌ | ❌ |
| ZRS | ✅ | ❌ |
| GRS | ❌ | ✅ |
| GZRS | ✅ | ✅ |

---

# 🔹 Replication Concepts

## LRS
3 copies within same datacenter.

---

## ZRS
Copies across multiple availability zones.

---

## GRS
Replicates to secondary region asynchronously.

---

## RA-GRS
Provides read access to secondary region.

---

# 💾 Blob Storage

Used for unstructured data.

Examples:
- Images
- Videos
- Backups
- Logs

---

# 🔹 Blob Types

| Blob Type | Purpose |
|---|---|
| Block Blob | General file storage |
| Append Blob | Logging |
| Page Blob | Virtual machine disks |

---

# 🔹 Blob Access Tiers

| Tier | Usage |
|---|---|
| Hot | Frequently accessed |
| Cool | Infrequently accessed |
| Archive | Rarely accessed |

---

# 🔹 Tier Characteristics

| Tier | Cost to Store | Cost to Access |
|---|---|---|
| Hot | High | Low |
| Cool | Medium | Medium |
| Archive | Low | High |

---

# 🔹 Soft Delete

Protects deleted blobs from permanent removal.

Can restore deleted data within retention period.

---

# 🔹 Blob Versioning

Automatically maintains previous versions of blobs.

---

# 🔹 Snapshots

Read-only copies of blobs at a point in time.

---

# 🔹 Immutable Storage

Prevents modification/deletion.

Used for:
- Compliance
- Legal retention

---

# 🔹 Lifecycle Management

Automatically moves blobs between tiers.

Example:
```json
{
  "rules": [
    {
      "enabled": true
    }
  ]
}
```

---

# 📂 Azure Files

Managed file shares in Azure.

Supports:
- SMB
- NFS

---

# 🔹 Azure Files Uses

| Use Case | Description |
|---|---|
| Shared Storage | Multiple VM access |
| Lift-and-shift | Replace on-prem file servers |
| Hybrid Storage | Sync with on-prem |

---

# 🔹 Azure File Sync

Synchronizes:
- On-prem Windows Servers
- Azure file shares

---

# 🔹 SMB vs NFS

| Protocol | Common Usage |
|---|---|
| SMB | Windows |
| NFS | Linux |

---

# 🔐 Storage Security

Critical AZ-104 topic.

---

# 🔹 Encryption

Azure Storage encrypts data at rest automatically.

Uses:
- Microsoft-managed keys
OR
- Customer-managed keys

---

# 🔹 Customer-Managed Keys (CMK)

Stored in:
- Azure Key Vault

Provides:
- Greater control
- Compliance support

---

# 🔹 Secure Transfer Required

Forces HTTPS access only.

---

# 🔹 Shared Access Signature (SAS)

Provides temporary delegated access.

---

# 🔹 SAS Types

| SAS Type | Description |
|---|---|
| User Delegation SAS | Uses Entra credentials |
| Service SAS | Specific storage service |
| Account SAS | Multiple services |

---

# 🔹 SAS Components

| Component | Purpose |
|---|---|
| Permissions | Read/Write/Delete |
| Expiry Time | Access duration |
| Resource | Storage object |

---

# 🔹 SAS Example

```text
https://storage.blob.core.windows.net/container/file.txt?sv=...
```

---

# 🔑 Access Keys

Storage accounts have:
- Primary key
- Secondary key

Used for authentication.

---

# 🔹 Key Rotation

Best practice:
- Rotate keys regularly

---

# 🌐 Network Access to Storage

Controls connectivity.

---

# 🔹 Firewall Rules

Can allow:
- Selected networks
- IP ranges
- VNets

---

# 🔹 Public Endpoint

Accessible via internet.

---

# 🔹 Private Endpoint

Private IP inside VNet.

Benefits:
- No public internet exposure
- Increased security

---

# 🔹 Service Endpoint

Extends VNet identity to Azure services.

---

# 🔹 Private Endpoint vs Service Endpoint

| Feature | Private Endpoint | Service Endpoint |
|---|---|---|
| Private IP | ✅ | ❌ |
| Public Exposure | Minimal | Still public service |
| Security | Higher | Moderate |

---

# 📦 Azure Storage Explorer

GUI tool for managing storage.

Supports:
- Blob upload/download
- File management
- Queue management

---

# 🔹 AzCopy

Command-line utility for data transfer.

Example:
```bash
azcopy copy "source" "destination"
```

---

# 📥 Import/Export Jobs

Used for offline data transfer using physical disks.

---

# 🔹 Use Cases

- Large-scale migration
- Limited bandwidth environments

---

# 📊 Monitoring Storage

Storage integrates with:
- Azure Monitor
- Log Analytics

---

# 🔹 Metrics Examples

| Metric | Description |
|---|---|
| Availability | Uptime |
| Transactions | Number of requests |
| Latency | Response delay |

---

# 🔹 Alerts

Can create alerts for:
- Capacity usage
- Availability
- Transactions

---

# 🔥 Important Exam Concepts

---

# 🔹 Storage Redundancy Selection

| Requirement | Best Choice |
|---|---|
| Cheapest | LRS |
| Zone protection | ZRS |
| Regional DR | GRS |
| Read secondary region | RA-GRS |

---

# 🔹 Blob Tier Selection

| Scenario | Tier |
|---|---|
| Daily access | Hot |
| Monthly access | Cool |
| Long-term archive | Archive |

---

# 🔹 Storage Security

Remember:
- HTTPS only
- Firewall rules
- SAS tokens
- Private endpoints
- Encryption

---

# ⚠️ Common Exam Confusions

---

# Blob Storage vs Azure Files

| Blob | Azure Files |
|---|---|
| Object storage | SMB/NFS shares |
| REST access | File system access |

---

# SAS vs Access Keys

| SAS | Access Key |
|---|---|
| Temporary | Full account access |
| Limited permissions | Complete control |

---

# Private Endpoint vs Service Endpoint

| Private Endpoint | Service Endpoint |
|---|---|
| Private IP | No private IP |
| Most secure | Less secure |

---

# 🧪 Common Exam Scenarios

---

# Scenario 1

Requirement:
```text
Allow temporary read-only access to a blob for 2 hours.
```

Answer:
```text
Shared Access Signature (SAS)
```

---

# Scenario 2

Requirement:
```text
Provide disaster recovery to another region.
```

Answer:
```text
GRS or RA-GRS
```

---

# Scenario 3

Requirement:
```text
Prevent storage account public internet access.
```

Answer:
```text
Private Endpoint
```

---

# Scenario 4

Requirement:
```text
Store data rarely accessed for 5 years at lowest cost.
```

Answer:
```text
Archive Tier
```

---

# Scenario 5

Requirement:
```text
Provide shared file access to Windows servers.
```

Answer:
```text
Azure Files
```

---

# 🧠 Memorization Tips

---

# Remember:

## Blob Storage
Object storage

## Azure Files
SMB/NFS shares

## SAS
Temporary delegated access

## LRS
Single datacenter redundancy

## GRS
Cross-region redundancy

## Private Endpoint
Most secure network access

---

# 🛠️ Recommended Hands-On Practice

Practice:
- Create storage accounts
- Configure replication
- Upload blobs
- Configure lifecycle rules
- Generate SAS tokens
- Configure private endpoints
- Create Azure file shares
- Use Storage Explorer
- Configure soft delete
- Create monitoring alerts

---

# 📖 Official Microsoft Resources

AZ-104 Skills Measured:
https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104/

Azure Storage Documentation:
https://learn.microsoft.com/en-us/azure/storage/

Blob Storage Documentation:
https://learn.microsoft.com/en-us/azure/storage/blobs/

Azure Files Documentation:
https://learn.microsoft.com/en-us/azure/storage/files/

Azure Storage Security:
https://learn.microsoft.com/en-us/azure/storage/common/storage-security-guide/
