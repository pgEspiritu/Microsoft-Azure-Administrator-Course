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

![Lab-5.1](images/Lab-5.1.png)

3. Configure the following settings:

| Option | Value |
|---|---|
| Resource Group | `az104-rg4` |
| Name | `CoreServicesVnet` |
| Region | `(US) East US` |

![Lab-5.2](images/Lab-5.2.png)

---

## 📡 Step 3: Configure Address Space

1. Open the:
   - **IP Addresses** tab

2. Replace the default address space with:

| Setting | Value |
|---|---|
| IPv4 address space | `10.20.0.0/16` |

![Lab-5.3](images/Lab-5.3.png)

---

## 🧱 Step 4: Create Subnets

### 🔹 SharedServicesSubnet

| Setting | Value |
|---|---|
| Subnet name | `SharedServicesSubnet` |
| Starting address | `10.20.10.0` |
| Size | `/24` |

![Lab-5.4](images/Lab-5.4.png)
![Lab-5.5](images/Lab-5.5.png)

---

### 🔹 DatabaseSubnet

| Setting | Value |
|---|---|
| Subnet name | `DatabaseSubnet` |
| Starting address | `10.20.20.0` |
| Size | `/24` |

![Lab-5.6](images/Lab-5.6.png)

> ⚠️ Delete the default subnet before deployment.

> 💡 **Note:**  
> Azure reserves 5 IP addresses in every subnet.

![Lab-5.7](images/Lab-5.7.png)

---

## 🚀 Step 5: Deploy the Virtual Network

1. Select:
   - **Review + Create**

2. Confirm validation passes.

3. Select:
   - **Create**

![Lab-5.8](images/Lab-5.8.png)

4. After deployment, select:
   - **Go to resource**

 ![Lab-5.9](images/Lab-5.9.png)

---

## 📤 Step 6: Export the ARM Template

1. In the **Automation** section, select:
   - **Export template**

2. Download:
   - `template.json`
   - `parameters.json`

![Lab-5.10](images/Lab-5.10.png)
![Lab-5.11](images/Lab-5.11.png)

3. Save both files locally.

![Lab-5.12](images/Lab-5.12.png)

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

![Lab-5.13](images/Lab-5.13.png)
![Lab-5.14](images/Lab-5.14.png)

---

## 🔄 Step 2: Modify Subnet Information

| Original | New Value |
|---|---|
| `SharedServicesSubnet` | `SensorSubnet1` |
| `10.20.10.0/24` | `10.30.20.0/24` |
| `DatabaseSubnet` | `SensorSubnet2` |
| `10.20.20.0/24` | `10.30.21.0/24` |

![Lab-5.15](images/Lab-5.15.png)
![Lab-5.16](images/Lab-5.16.png)
![Lab-5.17](images/Lab-5.17.png)
![Lab-5.18](images/Lab-5.18.png)


3. Save the file.

---

## ⚙️ Step 3: Edit Parameters File

1. Open:
   - `parameters.json`

2. Replace:

| Original | New Value |
|---|---|
| `CoreServicesVnet` | `ManufacturingVnet` |

![Lab-5.19](images/Lab-5.19.png)

3. Save the file.

---

## 🚀 Step 4: Deploy the Template

1. Search for and select:
   - **Deploy a custom template**

2. Select:
   - **Build your own template in the editor**

![Lab-5.20](images/Lab-5.20.png)

3. Upload:
   - `template.json`

![Lab-5.21](images/Lab-5.21.png)
![Lab-5.22](images/Lab-5.22.png)

4. Upload:
   - `parameters.json`

![Lab-5.23](images/Lab-5.23.png)
![Lab-5.24](images/Lab-5.24.png)
![Lab-5.25](images/Lab-5.25.png)

5. Ensure resource group:
   - `az104-rg4`

![Lab-5.26](images/Lab-5.26.png)

6. Select:
   - **Review + Create**
   - then **Create**

![Lab-5.27](images/Lab-5.27.png)

7. Verify:
   - `ManufacturingVnet`
   - `SensorSubnet1`
   - `SensorSubnet2`

were successfully created.

![Lab-5.28](images/Lab-5.28.png)

---

# 🧩 Task 3: Configure Communication Between ASG and NSG

---

# 🔹 Create the Application Security Group (ASG)

## Step 1: Create ASG

1. Search for and select:
   - **Application security groups**

2. Select:
   - **Create**

![Lab-5.29](images/Lab-5.29.png)

3. Configure:

| Setting | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `asg-web` |
| Region | `East US` |

![Lab-5.30](images/Lab-5.30.png)

4. Select:
   - **Review + Create**
   - then **Create**

![Lab-5.31](images/Lab-5.31.png)
![Lab-5.32](images/Lab-5.32.png)

---

# 🔹 Create the Network Security Group (NSG)

## Step 2: Create NSG

1. Search for and select:
   - **Network security groups**

2. Select:
   - **+ Create**

![Lab-5.33](images/Lab-5.33.png)

3. Configure:

| Setting | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `myNSGSecure` |
| Region | `East US` |

![Lab-5.34](images/Lab-5.34.png)

4. Select:
   - **Review + Create**
   - then **Create**

![Lab-5.35](images/Lab-5.35.png)

---

## 🔗 Step 3: Associate NSG with Subnet

1. Open:
   - `myNSGSecure`

2. Under **Settings**, select:
   - **Subnets**
   - then **Associate**

![Lab-5.36](images/Lab-5.36.png)

3. Configure:

| Setting | Value |
|---|---|
| Virtual network | `CoreServicesVnet` |
| Subnet | `SharedServicesSubnet` |

![Lab-5.37](images/Lab-5.37.png)

4. Select:
   - **OK**

---

# 🔹 Configure Inbound Security Rule

## Step 4: Allow ASG Traffic

1. Open:
   - **Inbound security rules**

2. Select:
   - **+ Add**

![Lab-5.38](images/Lab-5.38.png)

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

![Lab-5.39](images/Lab-5.39.png)
![Lab-5.40](images/Lab-5.40.png)


---

# 🔹 Configure Outbound Security Rule

## Step 5: Deny Internet Access

1. Open:
   - **Outbound security rules**

2. Select:
   - **+ Add**

![Lab-5.41](images/Lab-5.41.png)

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

![Lab-5.42](images/Lab-5.42.png)
![Lab-5.43](images/Lab-5.43.png)

---

# 🧩 Task 4: Configure Public and Private Azure DNS Zones

---

# 🌍 Configure Public DNS Zone

## Step 1: Create Public DNS Zone

1. Search for and select:
   - **DNS zones**

2. Select:
   - **+ Create**

![Lab-5.44](images/Lab-5.44.png)

3. Configure:

| Property | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `contoso.com` |
| Region | `East US` |

![Lab-5.45](images/Lab-5.45.png)

4. Select:
   - **Review + Create**
   - then **Create**

![Lab-5.46](images/Lab-5.46.png)

![Lab-5.47](images/Lab-5.47.png)

---

## 📝 Step 2: Create DNS Record

1. Open:
   - **Recordsets**

2. Select:
   - **+ Add**

![Lab-5.48](images/Lab-5.48.png)

3. Configure:

| Property | Value |
|---|---|
| Name | `www` |
| Type | `A` |
| TTL | `1` |
| IP Address | `10.1.1.4` |

4. Select:
   - **Add**

![Lab-5.49](images/Lab-5.49.png)
![Lab-5.50](images/Lab-5.50.png)

---

## 🔍 Step 3: Test DNS Resolution

Run the following command:

```bash
nslookup www.contoso.com <name-server>
```

Confirm:
- `www.contoso.com` resolves successfully

![Lab-5.51](images/Lab-5.51.png)

---

# 🔒 Configure Private DNS Zone

## Step 4: Create Private DNS Zone

1. Search for and select:
   - **Private DNS zones**

2. Select:
   - **+ Create**

![Lab-5.52](images/Lab-5.52.png)

3. Configure:

| Property | Value |
|---|---|
| Resource group | `az104-rg4` |
| Name | `private.contoso.com` |
| Region | `East US` |

![Lab-5.53](images/Lab-5.53.png)

4. Select:
   - **Review + Create**
   - then **Create**

![Lab-5.54](images/Lab-5.54.png)

---

## 🔗 Step 5: Link Virtual Network

1. Open:
   - **Virtual network links**

![Lab-5.55](images/Lab-5.55.png)

2. Configure:

| Property | Value |
|---|---|
| Link name | `manufacturing-link` |
| Virtual network | `ManufacturingVnet` |

3. Select:
   - **Create**

![Lab-5.56](images/Lab-5.56.png)

---

## 📝 Step 6: Create Private DNS Record

1. Open:
   - **Recordsets**

2. Select:
   - **+ Recordset**

![Lab-5.57](images/Lab-5.57.png)

3. Configure:

| Property | Value |
|---|---|
| Name | `sensorvm` |
| Type | `A` |
| TTL | `1` |
| IP Address | `10.1.1.4` |

![Lab-5.58](images/Lab-5.58.png)

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
