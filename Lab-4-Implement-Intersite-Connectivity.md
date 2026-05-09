# 🌐 Lab 04 - Implement Virtual Networking

---

# 📘 Lab Introduction

This lab introduces the fundamentals of Azure virtual networking.

In this lab, you will learn about:

- Virtual Networks (VNets)
- Subnets
- Network Security Groups (NSGs)
- Application Security Groups (ASGs)
- Azure DNS Zones and Records

⏱️ **Estimated Time:** 50 minutes  
🌎 **Region Used:** East US

---

# 🏢 Lab Scenario

Your organization plans to implement Azure virtual networks to support current and future growth.

### 📌 CoreServicesVnet
- Hosts the largest number of resources
- Requires a large address space for future expansion

### 📌 ManufacturingVnet
- Supports manufacturing systems and connected devices
- Requires multiple subnets for scalability

> 💡 **Best Practice:**  
> Avoid overlapping IP address ranges to simplify troubleshooting and future network expansion.

---

# 🛠️ Job Skills

## Tasks Covered

- ✅ Task 1: Create a virtual network with subnets using the portal
- ✅ Task 2: Create a virtual network and subnets using a template
- ✅ Task 3: Configure ASG and NSG communication
- ✅ Task 4: Configure public and private Azure DNS zones

---

# 🧩 Task 1: Create a Virtual Network with Subnets Using the Portal

## 🔐 Step 1: Sign in to Azure Portal

1. Open the Azure Portal:
   https://portal.azure.com

---

## 🌐 Step 2: Create the CoreServicesVnet

1. Search for and select:
   - **Virtual Networks**

2. Select:
   - **Create**

3. Configure the following settings:

| Option | Value |
|---|---|
| Resource Group | `az104-rg4` |
| Name | `CoreServicesVnet` |
| Region | `(US) East US` |

---

## 📡 Step 3: Configure Address Space

1. Open the:
   - **IP Addresses** tab

2. Replace the default address space with:

| Setting | Value |
|---|---|
| IPv4 address space | `10.20.0.0/16` |

---

## 🧱 Step 4: Create Subnets

### 🔹 SharedServicesSubnet

| Setting | Value |
|---|---|
| Subnet name | `SharedServicesSubnet` |
| Starting address | `10.20.10.0` |
| Size | `/24` |

---

### 🔹 DatabaseSubnet

| Setting | Value |
|---|---|
| Subnet name | `DatabaseSubnet` |
| Starting address | `10.20.20.0` |
| Size | `/24` |

> ⚠️ Delete the default subnet before deployment.

> 💡 **Note:**  
> Azure reserves 5 IP addresses in every subnet.

---

## 🚀 Step 5: Deploy the Virtual Network

1. Select:
   - **Review + Create**

2. Confirm validation passes.

3. Select:
   - **Create**

4. After deployment, select:
   - **Go to resource**

---

## 📤 Step 6: Export the ARM Template

1. In the **Automation** section, select:
   - **Export template**

2. Download:
   - `template.json`
   - `parameters.json`

3. Save both files locally.

---

# 🧩 Task 2: Create a Virtual Network Using a Template

## 📂 Step 1: Edit the Template File

1. Open:
   - `template.json`

2. Replace the following values:

| Original | New Value |
|---|---|
| `CoreServicesVnet` | `ManufacturingVnet` |
| `10.20.0.0` | `10.30.0.0` |

---

## 🔄 Step 2: Modify Subnet Information

| Original | New Value |
|---|---|
| `SharedServicesSubnet` | `SensorSubnet1` |
| `10.20.10.0/24` | `10.30.20.0/24` |
| `DatabaseSubnet` | `SensorSubnet2` |
| `10.20.20.0/24` | `10.30.21.0/24` |

3. Save the file.

---

## ⚙️ Step 3: Edit Parameters File

1. Open:
   - `parameters.json`

2. Replace:

| Original | New Value |
|---|---|
| `CoreServicesVnet` | `ManufacturingVnet` |

3. Save the file.

---

## 🚀 Step 4: Deploy the Template

1. Search for and select:
   - **Deploy a custom template**

2. Select:
   - **Build your own template in the editor**

3. Upload:
   - `template.json`

4. Upload:
   - `parameters.json`

5. Ensure resource group:
   - `az104-rg4`

6. Select:
   - **Review + Create**
   - then **Create**

7. Verify:
   - `ManufacturingVnet`
   - `SensorSubnet1`
   - `SensorSubnet2`

were successfully created.

---

# 🧩 Task 3: Configure Communication Between ASG and NSG

---

# 🔹 Create the Application Security Group (ASG)

## Step 1: Create ASG

1. Search for and select:
   - **Application security groups**

2. Select:
   - **Create**

3. Configure:

| Setting | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `asg-web` |
| Region | `East US` |

4. Select:
   - **Review + Create**
   - then **Create**

---

# 🔹 Create the Network Security Group (NSG)

## Step 2: Create NSG

1. Search for and select:
   - **Network security groups**

2. Select:
   - **+ Create**

3. Configure:

| Setting | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `myNSGSecure` |
| Region | `East US` |

4. Select:
   - **Review + Create**
   - then **Create**

---

## 🔗 Step 3: Associate NSG with Subnet

1. Open:
   - `myNSGSecure`

2. Under **Settings**, select:
   - **Subnets**
   - then **Associate**

3. Configure:

| Setting | Value |
|---|---|
| Virtual network | `CoreServicesVnet` |
| Subnet | `SharedServicesSubnet` |

4. Select:
   - **OK**

---

# 🔹 Configure Inbound Security Rule

## Step 4: Allow ASG Traffic

1. Open:
   - **Inbound security rules**

2. Select:
   - **+ Add**

3. Configure:

| Setting | Value |
|---|---|
| Source | `Application security group` |
| Source ASG | `asg-web` |
| Destination port ranges | `80,443` |
| Protocol | `TCP` |
| Action | `Allow` |
| Priority | `100` |
| Name | `AllowASG` |

4. Select:
   - **Add**

---

# 🔹 Configure Outbound Security Rule

## Step 5: Deny Internet Access

1. Open:
   - **Outbound security rules**

2. Select:
   - **+ Add**

3. Configure:

| Setting | Value |
|---|---|
| Source | `Any` |
| Destination | `Service tag` |
| Destination service tag | `Internet` |
| Protocol | `Any` |
| Action | `Deny` |
| Priority | `4096` |
| Name | `DenyInternetOutbound` |

4. Select:
   - **Add**

---

# 🧩 Task 4: Configure Public and Private Azure DNS Zones

---

# 🌍 Configure Public DNS Zone

## Step 1: Create Public DNS Zone

1. Search for and select:
   - **DNS zones**

2. Select:
   - **+ Create**

3. Configure:

| Property | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `contoso.com` |
| Region | `East US` |

4. Select:
   - **Review + Create**
   - then **Create**

---

## 📝 Step 2: Create DNS Record

1. Open:
   - **Recordsets**

2. Select:
   - **+ Add**

3. Configure:

| Property | Value |
|---|---|
| Name | `www` |
| Type | `A` |
| TTL | `1` |
| IP Address | `10.1.1.4` |

4. Select:
   - **Add**

---

## 🔍 Step 3: Test DNS Resolution

Run the following command:

```bash
nslookup www.contoso.com <name-server>
```

Confirm:
- `www.contoso.com` resolves successfully

---

# 🔒 Configure Private DNS Zone

## Step 4: Create Private DNS Zone

1. Search for and select:
   - **Private DNS zones**

2. Select:
   - **+ Create**

3. Configure:

| Property | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `private.contoso.com` |
| Region | `East US` |

4. Select:
   - **Review + Create**
   - then **Create**

---

## 🔗 Step 5: Link Virtual Network

1. Open:
   - **Virtual network links**

2. Configure:

| Property | Value |
|---|---|
| Link name | `manufacturing-link` |
| Virtual network | `ManufacturingVnet` |

3. Select:
   - **Create**

---

## 📝 Step 6: Create Private DNS Record

1. Open:
   - **Recordsets**

2. Select:
   - **+ Recordset**

3. Configure:

| Property | Value |
|---|---|
| Name | `sensorvm` |
| Type | `A` |
| TTL | `1` |
| IP Address | `10.1.1.4` |

4. Select:
   - **OK**

---

# 🧹 Cleanup Resources

## 🗑️ Delete Resource Group via Azure Portal

1. Open:
   - Resource group `az104-rg4`

2. Select:
   - **Delete resource group**

3. Enter:
   - `az104-rg4`

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

- Best practices for Azure virtual networks
- Azure PowerShell and CLI commands for VNets
- NSG inbound and outbound rules
- Difference between NSGs and ASGs
- Azure networking troubleshooting guide

---

# 📚 Key Takeaways

- A Virtual Network (VNet) represents your network in Azure.
- Subnets organize and secure network resources.
- Avoid overlapping IP ranges.
- NSGs control inbound and outbound traffic.
- ASGs simplify security management for server groups.
- Azure DNS supports both public and private name resolution.

---

# 🎉 Lab Completion

Congratulations! You have successfully completed the lab.

Select **End** to mark the lab as complete.
