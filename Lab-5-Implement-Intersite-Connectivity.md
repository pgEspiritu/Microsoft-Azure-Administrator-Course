# 🌐 Lab 05 - Implement Intersite Connectivity

---

# 📘 Lab Introduction

In this lab, you will explore communication between Azure virtual networks.

You will learn how to:

- Configure Virtual Network Peering
- Test network connectivity
- Use Azure Network Watcher
- Create custom routes

⏱️ **Estimated Time:** 50 minutes  
🌎 **Region Used:** East US

---

# 🏢 Lab Scenario

Your organization separates core IT services from manufacturing services for security and operational purposes.

However, there are situations where communication between these networks is required.

In this lab, you will configure connectivity between:

- 🖥️ Core IT Services
- 🏭 Manufacturing Services

This setup is commonly used to:

- Separate production and development environments
- Isolate subsidiaries or departments
- Improve security and management

---

# 🛠️ Job Skills

## Tasks Covered

- ✅ Task 1: Create a virtual machine in a virtual network
- ✅ Task 2: Create a virtual machine in another virtual network
- ✅ Task 3: Use Network Watcher to test connectivity
- ✅ Task 4: Configure virtual network peering
- ✅ Task 5: Test connectivity using Azure PowerShell
- ✅ Task 6: Create a custom route

---

# 🧩 Task 1: Create a Core Services VM and Virtual Network

---

## 🔐 Step 1: Sign in to Azure Portal

Open:

```text
https://portal.azure.com
```

---

## 🖥️ Step 2: Create CoreServicesVM

1. Search for and select:
   - **Virtual Machines**

2. Select:
   - **Create**
   - **Virtual Machine**

---

## ⚙️ Step 3: Configure Basic Settings

| Setting | Value |
|---|---|
| Resource group | `az104-rg5` |
| Virtual machine name | `CoreServicesVM` |
| Region | `(US) East US` |
| Availability options | `No infrastructure redundancy required` |
| Security type | `Standard` |
| Image | `Windows Server 2025 Datacenter - x64 Gen2` |
| Size | `Standard_D2s_v3` |
| Username | `localadmin` |
| Password | `Provide a complex password` |
| Public inbound ports | `None` |

Select:

- **Next : Disks >**

---

## 💽 Step 4: Configure Disk Settings

1. Keep default settings.

2. Select:
   - **Next : Networking >**

---

## 🌐 Step 5: Create Virtual Network

1. Under **Virtual network**, select:
   - **Create new**

2. Configure:

| Setting | Value |
|---|---|
| Name | `CoreServicesVnet` |
| Address range | `10.0.0.0/16` |
| Subnet Name | `Core` |
| Subnet address range | `10.0.0.0/24` |

3. Select:
   - **OK**

---

## 📊 Step 6: Disable Boot Diagnostics

1. Open the:
   - **Monitoring** tab

2. Set:

| Setting | Value |
|---|---|
| Boot diagnostics | `Disable` |

---

## 🚀 Step 7: Deploy the VM

1. Select:
   - **Review + create**

2. Select:
   - **Create**

> 💡 You do not need to wait for deployment before continuing.

---

# 🧩 Task 2: Create a VM in Another Virtual Network

---

## 🖥️ Step 1: Create ManufacturingVM

1. Navigate to:
   - **Virtual Machines**

2. Select:
   - **Create**
   - **Virtual Machine**

---

## ⚙️ Step 2: Configure Basic Settings

| Setting | Value |
|---|---|
| Resource group | `az104-rg5` |
| Virtual machine name | `ManufacturingVM` |
| Region | `(US) East US` |
| Security type | `Standard` |
| Availability options | `No infrastructure redundancy required` |
| Image | `Windows Server 2025 Datacenter - x64 Gen2` |
| Size | `Standard_D2s_v3` |
| Username | `localadmin` |
| Password | `Provide a complex password` |
| Public inbound ports | `None` |

Select:

- **Next : Disks >**

---

## 🌐 Step 3: Create ManufacturingVnet

1. Under **Virtual network**, select:
   - **Create new**

2. Configure:

| Setting | Value |
|---|---|
| Name | `ManufacturingVnet` |
| Address range | `172.16.0.0/16` |
| Subnet Name | `Manufacturing` |
| Subnet address range | `172.16.0.0/24` |

3. Select:
   - **OK**

---

## 📊 Step 4: Disable Boot Diagnostics

| Setting | Value |
|---|---|
| Boot diagnostics | `Disable` |

---

## 🚀 Step 5: Deploy ManufacturingVM

1. Select:
   - **Review + create**

2. Select:
   - **Create**

---

# 🧩 Task 3: Test Connectivity with Network Watcher

---

## 🔍 Step 1: Open Network Watcher

1. Search for and select:
   - **Network Watcher**

2. Under:
   - **Network diagnostic tools**

3. Select:
   - **Connection troubleshoot**

---

## ⚙️ Step 2: Configure Connectivity Test

| Field | Value |
|---|---|
| Source type | `Virtual machine` |
| Virtual machine | `CoreServicesVM` |
| Destination type | `Virtual machine` |
| Destination VM | `ManufacturingVM` |
| Preferred IP Version | `Both` |
| Protocol | `TCP` |
| Destination port | `3389` |

---

## ▶️ Step 3: Run Diagnostic Test

1. Select:
   - **Run diagnostic tests**

2. Wait for the results.

> ⚠️ Expected Result:  
> Connectivity status should be **Unreachable** because the virtual networks are not yet peered.

---

# 🧩 Task 4: Configure Virtual Network Peering

---

## 🔗 Step 1: Open CoreServicesVnet

1. Search for and select:
   - `CoreServicesVnet`

2. Under **Settings**, select:
   - **Peerings**

3. Select:
   - **+ Add**

---

## ⚙️ Step 2: Configure Peering

| Parameter | Value |
|---|---|
| Peering link name | `ManufacturingVnet-to-CoreServicesVnet` |
| Virtual network | `ManufacturingVnet` |
| Allow access | `Enabled` |
| Allow forwarded traffic | `Enabled` |

---

## ⚙️ Step 3: Configure Reverse Peering

| Parameter | Value |
|---|---|
| Peering link name | `CoreServicesVnet-to-ManufacturingVnet` |
| Allow access | `Enabled` |
| Allow forwarded traffic | `Enabled` |

---

## 🚀 Step 4: Create Peering

1. Select:
   - **Add**

2. Verify:
   - Peering status becomes **Connected**

---

# 🧩 Task 5: Test Connectivity Using Azure PowerShell

---

## 🖥️ Step 1: Get Private IP of CoreServicesVM

1. Open:
   - `CoreServicesVM`

2. Record the:
   - **Private IP Address**

---

## ⚡ Step 2: Run PowerShell Command from ManufacturingVM

1. Open:
   - `ManufacturingVM`

2. Under **Operations**, select:
   - **Run command**

3. Select:
   - **RunPowerShellScript**

4. Run:

```powershell
Test-NetConnection <CoreServicesVM private IP> -Port 3389
```

Example:

```powershell
Test-NetConnection 10.0.0.4 -Port 3389
```

---

## ✅ Step 3: Verify Connectivity

Expected Result:

- `TcpTestSucceeded : True`

> 💡 Connectivity now works because virtual network peering was configured.

---

# 🧩 Task 6: Create a Custom Route

---

## 🌐 Step 1: Create a New Subnet

1. Open:
   - `CoreServicesVnet`

2. Select:
   - **Subnets**
   - **+ Subnet**

3. Configure:

| Setting | Value |
|---|---|
| Name | `perimeter` |
| Starting address | `10.0.1.0/24` |

4. Select:
   - **Add**

---

## 🛣️ Step 2: Create Route Table

1. Search for and select:
   - **Route tables**

2. Select:
   - **+ Create**

---

## ⚙️ Step 3: Configure Route Table

| Setting | Value |
|---|---|
| Resource group | `az104-rg5` |
| Region | `East US` |
| Name | `rt-CoreServices` |
| Propagate gateway routes | `No` |

4. Select:
   - **Review + create**
   - then **Create**

---

## ➕ Step 4: Add Route

1. Open:
   - `rt-CoreServices`

2. Under **Settings**, select:
   - **Routes**
   - **+ Add**

3. Configure:

| Setting | Value |
|---|---|
| Route name | `PerimetertoCore` |
| Destination type | `IP Addresses` |
| Destination IP addresses | `10.0.0.0/16` |
| Next hop type | `Virtual appliance` |
| Next hop address | `10.0.1.7` |

4. Select:
   - **Add**

---

## 🔗 Step 5: Associate Route Table to Subnet

1. Open:
   - **Subnets**

2. Select:
   - **+ Associate**

3. Configure:

| Setting | Value |
|---|---|
| Virtual network | `CoreServicesVnet` |
| Subnet | `perimeter` |

4. Select:
   - **OK**

> 💡 This route directs traffic through a future Network Virtual Appliance (NVA).

---

# 🧹 Cleanup Resources

---

## 🗑️ Delete Resource Group via Azure Portal

1. Open:
   - Resource Group `az104-rg5`

2. Select:
   - **Delete resource group**

3. Enter:
   - `az104-rg5`

4. Select:
   - **Delete**

---

## ⚡ Delete Using Azure PowerShell

```powershell
Remove-AzResourceGroup -Name resourceGroupName
```

---

## ⚡ Delete Using Azure CLI

```bash
az group delete --name resourceGroupName
```

---

# 🤖 Extend Your Learning with Copilot

Try these prompts:

- Azure CLI commands for virtual network peering
- Azure monitoring tools comparison
- When to use custom routes in Azure
- Azure PowerShell examples for VNet peering

---

# 📚 Key Takeaways

- Virtual networks are isolated by default.
- Virtual Network Peering connects Azure VNets seamlessly.
- Peered VNets communicate using Microsoft's backbone network.
- User-defined routes override default system routes.
- Azure Network Watcher helps diagnose connectivity issues.
- Custom routes help control network traffic flow.

---

# 🎉 Lab Completion

Congratulations! You have successfully completed the lab.

Select **End** to mark the lab as complete.
