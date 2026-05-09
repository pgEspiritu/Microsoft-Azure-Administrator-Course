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

![Lab-6.1](images/Lab-6.1.png)

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

![Lab-6.2](images/Lab-6.2.png)
![Lab-6.3](images/Lab-6.3.png)
![Lab-6.4](images/Lab-6.4.png)

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

![Lab-6.5](images/Lab-6.5.png)

2. Configure:

| Setting | Value |
|---|---|
| Name | `CoreServicesVnet` |
| Address range | `10.0.0.0/16` |
| Subnet Name | `Core` |
| Subnet address range | `10.0.0.0/24` |

![Lab-6.6](images/Lab-6.6.png)

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

![Lab-6.7](images/Lab-6.7.png)

---

## 🚀 Step 7: Deploy the VM

1. Select:
   - **Review + create**

2. Select:
   - **Create**

![Lab-6.8](images/Lab-6.8.png)

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

![Lab-6.9](images/Lab-6.9.png)

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

![Lab-6.10](images/Lab-6.10.png)
![Lab-6.11](images/Lab-6.11.png)
![Lab-6.12](images/Lab-6.12.png)

Select:

- **Next : Disks >**

---

## 🌐 Step 3: Create ManufacturingVnet

1. Under **Virtual network**, select:
   - **Create new**

![Lab-6.13](images/Lab-6.13.png)

2. Configure:

| Setting | Value |
|---|---|
| Name | `ManufacturingVnet` |
| Address range | `172.16.0.0/16` |
| Subnet Name | `Manufacturing` |
| Subnet address range | `172.16.0.0/24` |

![Lab-6.14](images/Lab-6.14.png)

3. Select:
   - **OK**

---

## 📊 Step 4: Disable Boot Diagnostics

| Setting | Value |
|---|---|
| Boot diagnostics | `Disable` |

![Lab-6.15](images/Lab-6.15.png)

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

![Lab-6.16](images/Lab-6.16.png)

---

## ▶️ Step 3: Run Diagnostic Test

1. Select:
   - **Run diagnostic tests**

![Lab-6.17](images/Lab-6.17.png)

2. Wait for the results.

> ⚠️ Expected Result:  
> Connectivity status should be **Unreachable** because the virtual networks are not yet peered.

![Lab-6.18](images/Lab-6.18.png)

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

![Lab-6.19](images/Lab-6.19.png)

---

## ⚙️ Step 2: Configure Peering

| Parameter | Value |
|---|---|
| Peering link name | `ManufacturingVnet-to-CoreServicesVnet` |
| Virtual network | `ManufacturingVnet` |
| Allow access | `Enabled` |
| Allow forwarded traffic | `Enabled` |

![Lab-6.22](images/Lab-6.22.png)
![Lab-6.23](images/Lab-6.23.png)

---

## ⚙️ Step 3: Configure Reverse Peering

| Parameter | Value |
|---|---|
| Peering link name | `CoreServicesVnet-to-ManufacturingVnet` |
| Allow access | `Enabled` |
| Allow forwarded traffic | `Enabled` |

![Lab-6.20](images/Lab-6.20.png)
![Lab-6.21](images/Lab-6.21.png)

---

## 🚀 Step 4: Create Peering

1. Select:
   - **Add**

2. Verify:
   - Peering status becomes **Connected**

![Lab-6.24](images/Lab-6.24.png)
![Lab-6.25](images/Lab-6.25.png)

---

# 🧩 Task 5: Test Connectivity Using Azure PowerShell

---

## 🖥️ Step 1: Get Private IP of CoreServicesVM

1. Open:
   - `CoreServicesVM`

2. Record the:
   - **Private IP Address**

![Lab-6.26](images/Lab-6.26.png)

---

## ⚡ Step 2: Run PowerShell Command from ManufacturingVM

1. Open:
   - `ManufacturingVM`

2. Under **Operations**, select:
   - **Run command**

3. Select:
   - **RunPowerShellScript**

![Lab-6.27](images/Lab-6.27.png)

4. Run:

```powershell
Test-NetConnection <CoreServicesVM private IP> -Port 3389
```

Example:

```powershell
Test-NetConnection 10.0.0.4 -Port 3389
```

![Lab-6.28](images/Lab-6.28.png)

---

## ✅ Step 3: Verify Connectivity

Expected Result:

- `TcpTestSucceeded : True`

> 💡 Connectivity now works because virtual network peering was configured.

![Lab-6.29](images/Lab-6.29.png)

---

# 🧩 Task 6: Create a Custom Route

---

## 🌐 Step 1: Create a New Subnet

1. Open:
   - `CoreServicesVnet`

2. Select:
   - **Subnets**
   - **+ Subnet**

![Lab-6.30](images/Lab-6.30.png)

3. Configure:

| Setting | Value |
|---|---|
| Name | `perimeter` |
| Starting address | `10.0.1.0/24` |

4. Select:
   - **Add**

![Lab-6.31](images/Lab-6.31.png)

---

## 🛣️ Step 2: Create Route Table

1. Search for and select:
   - **Route tables**

2. Select:
   - **+ Create**

![Lab-6.32](images/Lab-6.32.png)

---

## ⚙️ Step 3: Configure Route Table

| Setting | Value |
|---|---|
| Resource group | `az104-rg5` |
| Region | `East US` |
| Name | `rt-CoreServices` |
| Propagate gateway routes | `No` |

![Lab-6.33](images/Lab-6.33.png)

4. Select:
   - **Review + create**
   - then **Create**

![Lab-6.34](images/Lab-6.34.png)

---

## ➕ Step 4: Add Route

1. Open:
   - `rt-CoreServices`

2. Under **Settings**, select:
   - **Routes**
   - **+ Add**

![Lab-6.35](images/Lab-6.35.png)

3. Configure:

| Setting | Value |
|---|---|
| Route name | `PerimetertoCore` |
| Destination type | `IP Addresses` |
| Destination IP addresses | `10.0.0.0/16` |
| Next hop type | `Virtual appliance` |
| Next hop address | `10.0.1.7` |

![Lab-6.36](images/Lab-6.36.png)

4. Select:
   - **Add**

---

## 🔗 Step 5: Associate Route Table to Subnet

1. Open:
   - **Subnets**

2. Select:
   - **+ Associate**

![Lab-6.37](images/Lab-6.37.png)

3. Configure:

| Setting | Value |
|---|---|
| Virtual network | `CoreServicesVnet` |
| Subnet | `perimeter` |

![Lab-6.38](images/Lab-6.38.png)

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
