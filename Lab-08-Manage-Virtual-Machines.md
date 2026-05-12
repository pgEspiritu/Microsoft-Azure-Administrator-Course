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

> 📌 Notice the other deployment choices available in the drop-down list.

---

## 🔹 Step 3: Configure Availability Zones

1. On the **Basics** tab, locate the **Availability zone** drop-down menu.

2. Place a checkmark next to:

   ✅ Zone 2

3. This action should automatically select:

   - ✅ Zone 1
   - ✅ Zone 2

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

---

## 🔹 Step 6: Configure the Networking Tab

1. Click:

   ➡️ **Next : Networking >**

2. Take the default settings but do not configure a load balancer.

| Setting | Value |
|---|---|
| Delete public IP and NIC when VM is deleted | Checked |
| Load balancing options | None |

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

> 📘 **Note:**  
> Notice that Azure independently creates and manages the following resources:
>
> - Network Interface Cards (NICs)
> - Managed disks
> - Public IP addresses (if configured)

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

6. When prompted, confirm the resize operation.

> 📘 **Note:**  
> If the D2ds_v4 size is unavailable in your region or subscription, skip this resize step.

---

## 🔹 Step 2: Create and Attach a Data Disk

1. In the **Settings** section of the VM, select:

   💽 **Disks**

2. Under **Data disks**, click:

   ➕ **Create and attach a new disk**

3. Configure the following settings.

| Setting | Value |
|---|---|
| Disk name | vm1-disk1 |
| Storage type | Standard HDD |
| Size (GiB) | 32 |

4. Click:

   ✅ **Apply**

---

## 🔹 Step 3: Detach the Disk

1. After the disk is created, locate the disk entry.

2. Click:

   🔌 **Detach**

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

---

## 🔹 Step 5: Reattach the Existing Disk

1. Return to the virtual machine:

   🖥️ **az104-vm1**

2. Open:

   💽 **Disks**

3. Under the **Data disk** section, click:

   🔗 **Attach existing disks**

4. In the **Disk name** drop-down list, select:

   📀 VM1-DISK1

5. Verify that the storage type is now:

   ✅ Standard SSD

6. Click:

   ✅ **Apply**

> 📘 **Note:**  
> You have now:
>
> - Created a virtual machine
> - Resized the VM SKU
> - Modified the managed disk storage type

> 📘 In the next task, you will use Virtual Machine Scale Sets to automate scaling.
