# 🚀 Lab 03 - Manage Azure Resources by Using Azure Resource Manager Templates

---

# 📘 Lab Introduction

In this lab, you will learn how to automate Azure resource deployments using:

- Azure Resource Manager (ARM) Templates
- Azure Bicep Templates
- Azure PowerShell
- Azure CLI
- Azure Cloud Shell

⏱️ **Estimated Time:** 50 minutes  
🌎 **Region Used:** East US

---

# 🏢 Lab Scenario

Your organization wants to:
- Automate resource deployments
- Reduce administrative overhead
- Minimize human error
- Improve deployment consistency

---

# 🛠️ Job Skills

## Tasks Covered

- ✅ Task 1: Create an Azure Resource Manager template
- ✅ Task 2: Edit and redeploy an ARM template
- ✅ Task 3: Deploy a template using Azure PowerShell
- ✅ Task 4: Deploy a template using Azure CLI
- ✅ Task 5: Deploy a resource using Azure Bicep

---

# 🧩 Task 1: Create an Azure Resource Manager Template

## 🔐 Step 1: Sign in to Azure Portal

1. Open the Azure Portal:
   https://portal.azure.com

---

## 💽 Step 2: Create a Managed Disk

1. Search for and select:
   - **Disks**

2. Select:
   - **Create**

3. Configure the following settings:

| Setting | Value |
|---|---|
| Subscription | Your subscription |
| Resource Group | `az104-rg3` |
| Disk name | `az104-disk1` |
| Region | `East US` |
| Availability zone | `No infrastructure redundancy required` |
| Source type | `None` |
| Performance | `Standard HDD` |
| Size | `32 GiB` |

> 💡 **Note:**  
> Managed disks are block-level storage volumes managed by Azure.

4. Select:
   - **Review + Create**
   - then **Create**

---

## 📤 Step 3: Export the ARM Template

1. After deployment completes, select:
   - **Go to resource**

2. In the **Automation** blade, select:
   - **Export template**

3. Review:
   - Template file
   - Parameters file

4. Download both files:
   - `template.json`
   - `parameters.json`

5. Verify both files exist in your local **Downloads** folder.

---

# 🧩 Task 2: Edit and Redeploy the ARM Template

## 🛠️ Step 1: Open Custom Deployment

1. Search for and select:
   - **Deploy a custom template**

2. Select:
   - **Build your own template in the editor**

---

## 📂 Step 2: Upload and Modify the Template

1. Select:
   - **Load file**

2. Upload:
   - `template.json`

3. Modify the template:

| Original | New Value |
|---|---|
| `disks_az104_disk1_name` | `disk_name` |
| `az104-disk1` | `az104-disk2` |

4. Select:
   - **Save**

---

## ⚙️ Step 3: Upload and Modify Parameters

1. Select:
   - **Edit parameters**

2. Upload:
   - `parameters.json`

3. Modify the parameter:

| Original | New Value |
|---|---|
| `disks_az104_disk1_name` | `disk_name` |

4. Select:
   - **Save**

---

## 🚀 Step 4: Deploy the Template

Configure the following settings:

| Setting | Value |
|---|---|
| Subscription | Your subscription |
| Resource Group | `az104-rg3` |
| Region | `(US) East US` |
| Disk_name | `az104-disk2` |

1. Select:
   - **Review + Create**
   - then **Create**

2. Verify:
   - `az104-disk2` was created successfully

3. Open:
   - Resource group `az104-rg3`

4. Confirm both disks exist:
   - `az104-disk1`
   - `az104-disk2`

---

## 📋 Step 5: Review Deployment History

1. In the resource group, select:
   - **Deployments**

2. Open a deployment and review:
   - Inputs
   - Template

> 💡 **Note:**  
> Azure stores deployment history for troubleshooting and auditing.

---

# ☁️ Task 3: Deploy a Template with Azure PowerShell

## 🖥️ Step 1: Open Cloud Shell

1. Select the **Cloud Shell** icon in the Azure Portal.

2. Choose:
   - **PowerShell**

---

## 💾 Step 2: Configure Cloud Shell Storage

1. Select:
   - **Mount storage account**

2. Configure:

| Setting | Value |
|---|---|
| Resource Group | `az104-rg3` |
| Region | Your region |
| Storage account | Globally unique name |
| File share | `fs-cloudshell` |

3. Select:
   - **Create**

---

## 📤 Step 3: Upload Template Files

1. Switch to:
   - **Classic Cloud Shell**

2. Select:
   - **Upload/Download files**
   - then **Upload**

3. Upload:
   - `template.json`
   - `parameters.json`

---

## ✏️ Step 4: Modify the Template

1. Open the editor.

2. Edit the template:
   - Change disk name to `az104-disk3`

3. Save the file:
   - `Ctrl + S`

4. Close the editor:
   - `Ctrl + Q`

---

## 🚀 Step 5: Deploy Using PowerShell

Run the following command:

```powershell
New-AzResourceGroupDeployment `
-ResourceGroupName az104-rg3 `
-TemplateFile template.json `
-TemplateParameterFile parameters.json
```

---

## ✅ Step 6: Verify Deployment

Run the following command:

```powershell
Get-AzDisk | ft Name,ResourceGroupName,Location,DiskSizeGb,ProvisioningState
```

Confirm:
- `ProvisioningState` is `Succeeded`

---

# 💻 Task 4: Deploy a Template with Azure CLI

## 🔄 Step 1: Switch to Bash

1. In Cloud Shell, switch to:
   - **Bash**

2. Verify uploaded files:

```bash
ls
```

---

## ✏️ Step 2: Modify the Template

1. Open the editor.

2. Change the disk name to:
   - `az104-disk4`

3. Save:
   - `Ctrl + S`

4. Exit:
   - `Ctrl + Q`

---

## 🚀 Step 3: Deploy Using Azure CLI

Run the following command:

```bash
az deployment group create \
--resource-group az104-rg3 \
--template-file template.json \
--parameters parameters.json
```

---

## ✅ Step 4: Verify Deployment

Run the following command:

```bash
az disk list --resource-group az104-rg3 --output table
```

---

# 🧱 Task 5: Deploy a Resource Using Azure Bicep **(Got issue with the lab, missing bicep file)**

## 📂 Step 1: Upload the Bicep File

1. Locate:
   - `F:\Allfiles\Labs\03\azuredeploydisk.bicep`

2. Upload the file to Cloud Shell.

---

## ✏️ Step 2: Modify the Bicep File

1. Open:
   - `azuredeploydisk.bicep`

2. Make the following changes:

| Setting | New Value |
|---|---|
| managedDiskName | `az104-disk5` |
| diskSizeinGiB | `32` |
| sku name | `StandardSSD_LRS` |

3. Save:
   - `Ctrl + S`

4. Exit:
   - `Ctrl + Q`

---

## 🚀 Step 3: Deploy the Bicep Template

Run the following command:

```bash
az deployment group create \
--resource-group az104-rg3 \
--template-file azuredeploydisk.bicep
```

---

## ✅ Step 4: Verify Deployment

Run the following command:

```bash
az disk list --resource-group az104-rg3 --output table
```

> 🎉 You should now have:
> - az104-disk1
> - az104-disk2
> - az104-disk3
> - az104-disk4
> - az104-disk5

---

# 🧹 Cleanup Resources

## 🗑️ Delete Resource Group via Azure Portal

1. Open:
   - Resource group `az104-rg3`

2. Select:
   - **Delete resource group**

3. Enter:
   - `az104-rg3`

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

Try these prompts in Microsoft Copilot:

- What is the format of an ARM template?
- How do I use an existing ARM template?
- Compare ARM templates and Bicep templates.

---

# 📚 Key Takeaways

- ARM templates automate Azure deployments.
- ARM templates use JSON syntax.
- Parameters can be stored separately in parameter files.
- Templates can be deployed using:
  - Azure Portal
  - Azure PowerShell
  - Azure CLI
- Azure Bicep simplifies Infrastructure as Code (IaC).
- Bicep provides:
  - Cleaner syntax
  - Type safety
  - Reusability
