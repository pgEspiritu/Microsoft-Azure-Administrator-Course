# 🖥️ Lab 08 - Manage Virtual Machines

---

# 📘 Lab Introduction

In this lab, you create and compare virtual machines to virtual machine scale sets. You learn how to create, configure, and resize a single virtual machine. You also learn how to create a virtual machine scale set and configure autoscaling.

This lab requires an Azure subscription. Your subscription type may affect the availability of features in this lab. You may change the region, but the steps are written using **East US**.

⏱️ **Estimated timing:** 50 minutes

---

# 🏢 Lab Scenario

Your organization wants to explore deploying and configuring Azure virtual machines.

- First, you implement an Azure virtual machine with manual scaling.
- Next, you implement a Virtual Machine Scale Set and explore autoscaling.

---

# 🎯 Job Skills

## ✅ Tasks Covered

- 🖥️ Task 1: Deploy zone-resilient Azure virtual machines by using the Azure portal.
- 💾 Task 2: Manage compute and storage scaling for virtual machines.
- ⚙️ Task 3: Create and configure Azure Virtual Machine Scale Sets.
- 📈 Task 4: Scale Azure Virtual Machine Scale Sets.
- 💻 Task 5: Create a virtual machine using Azure PowerShell (optional 1).
- 🐧 Task 6: Create a virtual machine using the CLI (optional 2).

---

# 🏗️ Azure Virtual Machines Architecture Diagram

📌 Diagram of the VM architecture tasks.

---

# 🖥️ Task 1: Deploy Zone-Resilient Azure Virtual Machines by Using the Azure Portal

In this task, you will deploy two Azure virtual machines into different availability zones by using the Azure portal.

Availability zones offer the highest level of uptime SLA for virtual machines at **99.99%**. To achieve this SLA, you must deploy at least two virtual machines across different availability zones.

---

## 🔹 Step 1: Sign in to the Azure Portal

1. Open the Azure portal:

   https://portal.azure.com

---

## 🔹 Step 2: Open the Virtual Machines Service

1. Search for and select **Virtual machines**.

2. On the **Virtual machines** blade, click:

   ➕ **Create**

3. From the drop-down menu, select:

   🖥️ **Azure virtual machine**

![Lab-9.1](images/Lab-9.1.png)

> 📌 Notice the other deployment choices available in the drop-down list.

---

## 🔹 Step 3: Configure Availability Zones

1. On the **Basics** tab, locate the **Availability zone** drop-down menu.

2. Place a checkmark next to:

   ✅ Zone 2

3. This action should automatically select:

   - ✅ Zone 1
   - ✅ Zone 2

![Lab-9.2](images/Lab-9.2.png)

> 📘 **Note:**  
> This deployment creates two virtual machines in the selected region, with one VM placed in each availability zone.

> 📘 **Important:**  
> You achieve the 99.99% uptime SLA because you have at least two virtual machines distributed across at least two zones.

> 💡 Even if you only need one VM, deploying to another zone is considered a best practice for resiliency.

---

## 🔹 Step 4: Configure the Basics Tab

Complete the following settings.

| Setting | Value |
|---|---|
| Subscription | the name of your Azure subscription |
| Resource group | az104-rg8-lod61669901 |
| Virtual machine names | az104-vm1 and az104-vm2 |
| Region | westus2 |
| Availability options | Availability zone |
| Availability zone | Zone 1, 2 |
| Security type | Standard |
| Image (See all images) | Windows Server 2025 Datacenter - x64 Gen2 |
| Azure Spot instance | unchecked |
| Size | Standard D2s v3 |
| Username | localadmin |
| Password | Provide a secure password |
| Public inbound ports | None |
| Would you like to use an existing Windows Server license? | Unchecked |

> 📘 **Note:**  
> After selecting both availability zones, select **Edit names** under the VM name field to configure both VM names.

![Lab-9.3](images/Lab-9.3.png)
![Lab-9.4](images/Lab-9.4.png)
![Lab-9.5](images/Lab-9.5.png)
![Lab-9.6](images/Lab-9.6.png)

---

## 🔹 Step 5: Configure the Disks Tab

1. Click:

   ➡️ **Next : Disks >**

2. Configure the following settings.

| Setting | Value |
|---|---|
| OS disk type | Premium SSD |
| Delete with VM | checked (default) |
| Enable Ultra Disk compatibility | Unchecked |

![Lab-9.7](images/Lab-9.7.png)

---

## 🔹 Step 6: Configure the Networking Tab

1. Click:

   ➡️ **Next : Networking >**

2. Take the default settings but do not configure a load balancer.

| Setting | Value |
|---|---|
| Delete public IP and NIC when VM is deleted | Checked |
| Load balancing options | None |

![Lab-9.8](images/Lab-9.8.png)

---

## 🔹 Step 7: Review the Management Settings

1. Click:

   ➡️ **Next : Management >**

2. Review the settings.

3. Do not make any changes.

---

## 🔹 Step 8: Configure Monitoring

1. Click:

   ➡️ **Next : Monitoring >**

2. Configure the following setting.

| Setting | Value |
|---|---|
| Boot diagnostics | Disable |

![Lab-9.9](images/Lab-9.9.png)

---

## 🔹 Step 9: Review and Create the Virtual Machines

1. Click:

   ➡️ **Next : Advanced >**

2. Take the default settings.

3. Click:

   ✅ **Review + Create**

4. Wait for validation to complete.

5. After validation passes, click:

   🚀 **Create**

![Lab-9.10](images/Lab-9.10.png)

> 📘 **Note:**  

Notice that Azure independently creates and manages the following resources:
- Network Interface Cards (NICs)
- Managed disks
- - Public IP addresses (if configured)

---

## 🔹 Step 10: Verify Deployment

1. Wait for the deployment to complete.

2. Click:

   🔍 **Go to resource**

> 📘 **Note:**  
> Monitor the Azure Notification messages during deployment.

---

# 💾 Task 2: Manage Compute and Storage Scaling for Virtual Machines

In this task, you scale a virtual machine by adjusting its size to another SKU.

Azure provides flexibility in VM size selection so that you can adjust a VM for periods where additional compute or memory resources are required.

This scaling concept also applies to managed disks, where you can modify:
- Disk performance
- Disk type
- Allocated capacity

---

## 🔹 Step 1: Resize the Virtual Machine

1. Open the virtual machine:

   🖥️ **az104-vm1**

2. In the left-side menu, under:

   📂 **Availability + scale**

3. Select:

   📏 **Size**

4. Set the VM size to:

   ✅ D2ds_v4

5. Click:

   🔄 **Resize**

![Lab-9.11](images/Lab-9.11.png)

6. When prompted, confirm the resize operation.

> 📘 **Note:**  
> If the D2ds_v4 size is unavailable in your region or subscription, skip this resize step.

---

## 🔹 Step 2: Create and Attach a Data Disk

1. In the **Settings** section of the VM, select:

   💽 **Disks**

2. Under **Data disks**, click:

   ➕ **Create and attach a new disk**

![Lab-9.12](images/Lab-9.12.png)

3. Configure the following settings.

| Setting | Value |
|---|---|
| Disk name | vm1-disk1 |
| Storage type | Standard HDD |
| Size (GiB) | 32 |

4. Click:

   ✅ **Apply**

![Lab-9.13](images/Lab-9.13.png)

---

## 🔹 Step 3: Detach the Disk

1. After the disk is created, locate the disk entry.

2. Click:

   🔌 **Detach**

![Lab-9.14](images/Lab-9.14.png)

> 📘 **Note:**  
> You may need to scroll horizontally to locate the detach icon.

3. Click:

   ✅ **Apply**

> 📘 **Important:**  
> Detaching the disk removes it from the VM but keeps the disk resource stored in Azure for later use.

---

## 🔹 Step 4: Modify Disk Performance

1. Search for and select:

   💽 **Disks**

2. From the list of disks, select:

   📀 **vm1-disk1**

> 📘 **Note:**  
> The Overview blade displays performance and usage information for the disk.

3. In the left-side menu, select:

   ⚡ **Size + performance**

4. Change the storage type to:

   ✅ Standard SSD

5. Click:

   💾 **Save**

![Lab-9.15](images/Lab-9.15.png)

---

## 🔹 Step 5: Reattach the Existing Disk

1. Return to the virtual machine:

   🖥️ **az104-vm1**

2. Open:

   💽 **Disks**

3. Under the **Data disk** section, click:

   🔗 **Attach existing disks**

![Lab-9.16](images/Lab-9.16.png)

4. In the **Disk name** drop-down list, select:

   📀 VM1-DISK1

5. Verify that the storage type is now:

   ✅ Standard SSD

6. Click:

   ✅ **Apply**

![Lab-9.17](images/Lab-9.17.png)

> 📘 **Note:**

You have now:
- Created a virtual machine
- Resized the VM SKU
- Modified the managed disk storage type

> 📘 In the next task, you will use Virtual Machine Scale Sets to automate scaling.


---

# 🧱 Task 3: Create and configure Azure Virtual Machine Scale Sets

---

### ➕ Create VMSS

Search **Virtual machine scale sets** → Click **+ Create**

![Lab-9.18](images/Lab-9.18.png)

---

### ⚙️ Basics

| Setting | Value |
|--------|------|
| VMSS name | vmss1 |
| Region | westus2 |
| Availability zones | 1, 2, 3 |
| Orchestration mode | Uniform |
| Image | Windows Server 2025 |
| Size | Standard D2s_v3 |
| Username | localadmin |

![Lab-9.19](images/Lab-9.19.png)
![Lab-9.20](images/Lab-9.20.png)
![Lab-9.21](images/Lab-9.21.png)

---

### 🌐 Networking configuration

Edit virtual network:

| Setting | Value |
|--------|------|
| Name | vmss-vnet |
| Address range | 10.82.0.0/20 |
| Subnet | subnet0 |
| Subnet range | 10.82.0.0/24 |

![Lab-9.22](images/Lab-9.22.png)
![Lab-9.23](images/Lab-9.23.png)
![Lab-9.24](images/Lab-9.24.png)
![Lab-9.25](images/Lab-9.25.png)

---

### 🔐 NSG configuration

Create NSG:

| Setting | Value |
|--------|------|
| Name | vmss1-nsg |

![Lab-9.26](images/Lab-9.26.png)
![Lab-9.27](images/Lab-9.27.png)

Inbound rule:

| Setting | Value |
|--------|------|
| Service | HTTP |
| Action | Allow |
| Priority | 1010 |
| Name | allow-http |

![Lab-9.28](images/Lab-9.28.png)
![Lab-9.29](images/Lab-9.29.png)

---

### 🌍 Public IP

Enable Public IP for NIC

![Lab-9.30](images/Lab-9.30.png)

---

### ⚖️ Load balancer

Create:

| Setting | Value |
|--------|------|
| Load balancer name | vmss-lb |

![Lab-9.31](images/Lab-9.31.png)
![Lab-9.32](images/Lab-9.32.png)
![Lab-9.33](images/Lab-9.33.png)
![Lab-9.34](images/Lab-9.34.png)

---

### ✔️ Finalize

- Boot diagnostics: Disable
- Review + Create → Create

![Lab-9.35](images/Lab-9.35.png)
![Lab-9.36](images/Lab-9.36.png)

---

# 📈 Task 4: Scale Azure Virtual Machine Scale Sets

---

### 📊 Autoscale setup

Go to VMSS → **Scaling**

Select **Custom autoscale**

![Lab-9.37](images/Lab-9.37.png)

---

### 📤 Scale-out rule

| Setting | Value |
|--------|------|
| Metric | Percentage CPU |
| Operator | Greater than |
| Threshold | 70 |
| Duration | 10 minutes |
| Action | Increase by 50% |

Save

![Lab-9.38](images/Lab-9.38.png)
![Lab-9.39](images/Lab-9.39.png)

---

### 📥 Scale-in rule

| Setting | Value |
|--------|------|
| Operator | Less than |
| Threshold | 30 |
| Action | Decrease by 50% |

Save

![Lab-9.40](images/Lab-9.40.png)
![Lab-9.41](images/Lab-9.41.png)

---

### 📏 Instance limits

| Setting | Value |
|--------|------|
| Minimum | 2 |
| Maximum | 10 |
| Default | 2 |

Save

![Lab-9.42](images/Lab-9.42.png)

![Lab-9.43](images/Lab-9.43.png)

---

# 💻 Task 5: Azure PowerShell VM creation

---

### 🟦 Cloud Shell (PowerShell)

Run:

```powershell
New-AzVm `
-ResourceGroupName 'az104-rg8-lod61669901' `
-Name 'myPSVM' `
-Location 'westus2' `
-Image 'Win2019Datacenter' `
-Zone '1' `
-Size 'Standard_D2s_v3' `
-Credential (Get-Credential)
```

### 📋 Verify VM

```powershell
Get-AzVM -ResourceGroupName 'az104-rg8-lod61669901' -Status
```

### ⛔ Stop VM

```powershell
Stop-AzVM -ResourceGroupName 'az104-rg8-lod61669901' -Name 'myPSVM'
```

![Lab-9.44](images/Lab-9.44.png)
![Lab-9.45](images/Lab-9.45.png)

---

# 💻 Task 6: CLI VM creation

---

### 🐧 Bash Cloud Shell

```bash
az vm create --name myCLIVM --resource-group az104-rg8-lod61669901 --image Canonical:0001-com-ubuntu-server-jammy:22_04-lts:latest --admin-username localadmin --generate-ssh-keys --size Standard_D2s_v3
```

### 📋 Verify VM

```bash
az vm show --name myCLIVM --resource-group az104-rg8-lod61669901 --show-details --output table
```

### ⛔ Deallocate VM

```bash
az vm deallocate --resource-group az104-rg8-lod61669901 --name myCLIVM
```

![Lab-9.46](images/Lab-9.46.png)

---

# 🧹 Cleanup

Delete resource group:

Azure Portal → Delete Resource Group
PowerShell:
```powershell
Remove-AzResourceGroup -Name resourceGroupName
```

CLI:
```bash
az group delete --name resourceGroupName
```

---

# 📌 Key takeaways
- Azure VMs are scalable compute resources
- Scaling can be vertical and horizontal
- VMSS automates scaling
- Instances share same configuration
- Autoscaling reacts to demand

