# AZ-104 Reviewer
# Domain: Deploy and Manage Compute Resources

---

# 📚 Exam Coverage

This domain covers:
- Azure Virtual Machines (VMs)
- VM Availability Options
- VM Scale Sets (VMSS)
- Azure App Service
- Azure Container Services
- Azure Container Registry (ACR)
- Azure Kubernetes Service (AKS)
- ARM Templates and Bicep
- Azure Automation
- Managed Disks
- VM Backups and Recovery

Weight in Exam:
20–25%

---

# ☁️ Azure Compute Overview

Azure Compute provides:
- Virtual machines
- Containers
- Web hosting
- Scaling solutions
- Serverless compute

---

# 🔹 Compute Service Categories

| Service | Type |
|---|---|
| Virtual Machines | IaaS |
| App Service | PaaS |
| AKS | Container orchestration |
| Azure Functions | Serverless |
| Container Apps | Serverless containers |

---

# 🖥️ Azure Virtual Machines (VMs)

Provides Infrastructure as a Service (IaaS).

You manage:
- Operating system
- Applications
- Networking
- Security

---

# 🔹 VM Components

| Component | Description |
|---|---|
| OS Disk | Main operating system disk |
| Data Disk | Additional storage |
| NIC | Network interface |
| NSG | Traffic filtering |
| Public IP | Internet access |

---

# 🔹 VM Operating Systems

Supported:
- Windows Server
- Ubuntu
- Red Hat
- SUSE
- Debian

---

# 🔹 VM Deployment Methods

| Method | Description |
|---|---|
| Azure Portal | GUI |
| Azure CLI | Command-line |
| PowerShell | Automation |
| ARM Templates | IaC |
| Bicep | Simplified IaC |

---

# 🔹 VM Sizes

Different VM families optimized for workloads.

---

# 🔹 Common VM Series

| Series | Usage |
|---|---|
| B-series | Burstable workloads |
| D-series | General purpose |
| E-series | Memory optimized |
| F-series | Compute optimized |
| M-series | Large memory workloads |

---

# 🔹 VM States

| State | Billing |
|---|---|
| Running | Charged |
| Stopped | Charged |
| Stopped (Deallocated) | Not charged for compute |

---

# 🔹 Important VM Concepts

## Deallocate
Stops billing for compute resources.

---

## Redeploy
Moves VM to another Azure host.

---

## Resize
Changes VM size/SKU.

---

# 💾 Managed Disks

Azure-managed storage for VMs.

---

# 🔹 Disk Types

| Disk Type | Description |
|---|---|
| Standard HDD | Low-cost |
| Standard SSD | Balanced |
| Premium SSD | High performance |
| Ultra Disk | Highest performance |

---

# 🔹 Disk Types Usage

| Disk | Common Use |
|---|---|
| HDD | Backup/archive |
| SSD | General workloads |
| Premium SSD | Production databases |
| Ultra Disk | Mission-critical workloads |

---

# 🔹 Disk Encryption

Protects VM disks.

Can use:
- Platform-managed keys
- Customer-managed keys

---

# 🔹 Ephemeral OS Disk

Temporary OS disk stored locally.

Benefits:
- Faster deployment
- Faster reimaging

Limitation:
- Data lost if VM redeployed

---

# 🔹 Azure Disk Snapshots

Point-in-time backup of managed disks.

---

# 🏢 VM Availability Options

Ensures high availability and fault tolerance.

---

# 🔹 Availability Sets

Protect against:
- Hardware failures
- Planned maintenance

---

# 🔹 Fault Domains

Separate physical hardware.

---

# 🔹 Update Domains

Separate maintenance groups.

---

# 🔹 Availability Zones

Separate datacenters within a region.

Benefits:
- Higher SLA
- Datacenter failure protection

---

# 🔹 Availability Sets vs Zones

| Feature | Availability Set | Availability Zone |
|---|---|---|
| Datacenter protection | ❌ | ✅ |
| Rack protection | ✅ | ✅ |

---

# 🔹 Virtual Machine Scale Sets (VMSS)

Automatically scales VM instances.

---

# 🔹 VMSS Features

| Feature | Description |
|---|---|
| Autoscaling | Automatic scaling |
| Load balancing | Traffic distribution |
| High availability | Multiple instances |

---

# 🔹 VMSS Scaling

Scaling can occur based on:
- CPU usage
- Memory
- Schedules

---

# 🌐 Azure App Service

Platform as a Service (PaaS) web hosting.

---

# 🔹 App Service Uses

- Web applications
- REST APIs
- Mobile backends

---

# 🔹 Supported Languages

| Language |
|---|
| .NET |
| Java |
| Node.js |
| Python |
| PHP |
| Ruby |

---

# 🔹 App Service Plan

Defines:
- Pricing tier
- Region
- Compute resources

---

# 🔹 App Service Features

| Feature | Description |
|---|---|
| Autoscaling | Scale automatically |
| Deployment Slots | Staging environments |
| SSL Support | HTTPS |
| Backup | App backup |
| Custom Domains | Domain mapping |

---

# 🔹 Deployment Slots

Used for:
- Staging
- Blue/Green deployments

---

# 🔹 Slot Swap

Switches staging and production slots.

---

# 🔹 App Service Scaling

| Scaling Type | Description |
|---|---|
| Scale Up | Bigger VM |
| Scale Out | More instances |

---

# 📦 Containers in Azure

Containers package applications with dependencies.

---

# 🔹 Azure Container Instances (ACI)

Runs containers without managing VMs.

Best for:
- Simple workloads
- Short-lived tasks

---

# 🔹 Azure Container Registry (ACR)

Private Docker container registry.

Stores:
- Docker images
- OCI artifacts

---

# 🔹 Azure Kubernetes Service (AKS)

Managed Kubernetes service.

Features:
- Orchestration
- Scaling
- Self-healing

---

# 🔹 AKS Components

| Component | Description |
|---|---|
| Cluster | Kubernetes environment |
| Node Pool | Group of VMs |
| Pods | Running containers |

---

# 🔹 AKS Benefits

- Managed control plane
- Autoscaling
- Integrated monitoring

---

# 🔹 Azure Container Apps

Serverless container platform.

Features:
- Autoscaling
- Microservices
- Event-driven workloads

---

# 🏗️ ARM Templates

Infrastructure as Code (IaC) deployment method.

Uses JSON.

---

# 🔹 ARM Benefits

| Benefit | Description |
|---|---|
| Repeatability | Consistent deployments |
| Automation | Automated provisioning |
| Version Control | Store templates in Git |

---

# 🔹 ARM Template Structure

```json
{
  "$schema": "",
  "resources": []
}
```

---

# 🔹 Bicep

Simplified language for ARM deployments.

Benefits:
- Easier syntax
- Modular
- Cleaner than JSON

---

# 🔹 Bicep Example

```bicep
resource vm 'Microsoft.Compute/virtualMachines@2023-03-01' = {
  name: 'myVM'
}
```

---

# 🔄 VM Backups

Protects virtual machines from data loss.

---

# 🔹 Azure Backup

Uses:
- Recovery Services Vault

Supports:
- Full VM backup
- Disk backup

---

# 🔹 Backup Features

| Feature | Description |
|---|---|
| Scheduled Backup | Automatic |
| Retention Policies | Recovery periods |
| Restore Points | Point-in-time recovery |

---

# 🔹 Azure Site Recovery (ASR)

Disaster recovery service.

Features:
- Replication
- Failover
- Failback

---

# ⚙️ Azure Automation

Automates administrative tasks.

---

# 🔹 Automation Features

| Feature | Description |
|---|---|
| Runbooks | Automated scripts |
| Update Management | Patch VMs |
| Scheduling | Timed automation |

---

# 🔹 Runbook Types

| Type | Description |
|---|---|
| PowerShell | Script automation |
| Python | Automation scripts |
| Graphical | Visual workflow |

---

# 📊 Monitoring Compute Resources

Integrated with:
- Azure Monitor
- Log Analytics

---

# 🔹 VM Monitoring Metrics

| Metric | Description |
|---|---|
| CPU Usage | Processor utilization |
| Disk IOPS | Disk performance |
| Memory | RAM utilization |
| Network Throughput | Traffic |

---

# 🔹 Boot Diagnostics

Captures:
- VM screenshots
- Console logs

Useful for troubleshooting.

---

# 🔹 Azure Monitor Agent (AMA)

Collects monitoring data from VMs.

---

# 🔥 Important Exam Concepts

---

# 🔹 Availability Selection

| Requirement | Best Choice |
|---|---|
| Rack failure protection | Availability Set |
| Datacenter failure protection | Availability Zone |
| Automatic scaling | VMSS |

---

# 🔹 App Service vs VM

| App Service | VM |
|---|---|
| PaaS | IaaS |
| Microsoft manages OS | You manage OS |
| Easier scaling | More control |

---

# 🔹 Containers vs VMs

| Containers | VMs |
|---|---|
| Lightweight | Full OS |
| Faster startup | Slower |
| Share host kernel | Separate OS |

---

# ⚠️ Common Exam Confusions

---

# Stop vs Deallocate

| Action | Billing |
|---|---|
| Stop | Still charged |
| Deallocate | Compute billing stops |

---

# Scale Up vs Scale Out

| Scale Up | Scale Out |
|---|---|
| Bigger VM | More VMs |

---

# Availability Set vs Zone

| Availability Set | Zone |
|---|---|
| Same datacenter | Different datacenters |

---

# ACI vs AKS

| ACI | AKS |
|---|---|
| Simple containers | Full orchestration |
| No cluster management | Kubernetes |

---

# 🧪 Common Exam Scenarios

---

# Scenario 1

Requirement:
```text
Automatically add more VM instances during high CPU usage.
```

Answer:
```text
Virtual Machine Scale Set (VMSS)
```

---

# Scenario 2

Requirement:
```text
Protect applications from datacenter failure.
```

Answer:
```text
Availability Zones
```

---

# Scenario 3

Requirement:
```text
Deploy web app without managing operating system.
```

Answer:
```text
Azure App Service
```

---

# Scenario 4

Requirement:
```text
Store private Docker images.
```

Answer:
```text
Azure Container Registry (ACR)
```

---

# Scenario 5

Requirement:
```text
Stop paying compute charges for a VM.
```

Answer:
```text
Deallocate the VM
```

---

# Scenario 6

Requirement:
```text
Deploy repeatable infrastructure using code.
```

Answer:
```text
ARM Templates or Bicep
```

---

# 🧠 Memorization Tips

---

# Remember:

## VM
Full OS control

## App Service
PaaS web hosting

## VMSS
Automatic scaling

## Availability Zone
Datacenter protection

## Availability Set
Rack/host protection

## ACR
Private container registry

## AKS
Managed Kubernetes

## Deallocate
Stops compute billing

---

# 🛠️ Recommended Hands-On Practice

Practice:
- Create VMs
- Resize VMs
- Configure availability sets
- Configure availability zones
- Create VM Scale Sets
- Deploy App Services
- Configure deployment slots
- Deploy containers
- Create ACR repositories
- Deploy AKS cluster
- Create ARM templates
- Create Bicep deployments
- Configure VM backups

---

# 📖 Official Microsoft Resources

AZ-104 Skills Measured:
https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104/

Azure Virtual Machines:
https://learn.microsoft.com/en-us/azure/virtual-machines/

Azure App Service:
https://learn.microsoft.com/en-us/azure/app-service/

Azure Kubernetes Service:
https://learn.microsoft.com/en-us/azure/aks/

Azure Container Registry:
https://learn.microsoft.com/en-us/azure/container-registry/

ARM Templates:
https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/

Bicep Documentation:
https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/
