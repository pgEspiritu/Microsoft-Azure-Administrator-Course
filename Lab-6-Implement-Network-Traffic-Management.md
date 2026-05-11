# 🌐 Lab 06 - Implement Network Traffic Management

---

# 📖 Lab Introduction

In this lab, you learn how to configure and test a public Load Balancer and an Application Gateway.

> ⚠️ This lab requires an Azure subscription. Your subscription type may affect the availability of features in this lab. You may change the region, but the steps are written using East US.

⏱️ **Estimated Timing:** 50 minutes

---

# 🧩 Lab Scenario

Your organization has a public website. You need to load balance incoming public requests across different virtual machines. You also need to provide images and videos from different virtual machines. You plan on implementing:

- ⚖️ Azure Load Balancer
- 🌐 Azure Application Gateway

All resources are in the same region.

---

# 🛠️ Job Skills

- ✅ Task 1: Use a template to provision an infrastructure
- ✅ Task 2: Configure an Azure Load Balancer
- ✅ Task 3: Configure an Azure Application Gateway

---

# 🏗️ Task 1: Use a Template to Provision an Infrastructure

In this task, you will use a template to deploy:

- 🌐 One virtual network
- 🔒 One network security group
- 💻 Three virtual machines

---

## 📥 Download the Lab Files

Download the following lab files:

- `az104-06-vms-template.json`
- `az104-06-vms-parameters.json`

> 📌 If you already downloaded the lab files from the previous page, you may skip this step.

---

## 🔐 Sign in to Azure Portal

Open the Azure Portal:

```plaintext
https://portal.azure.com
```

---

## 🚀 Deploy the ARM Template

### Step 1: Open Custom Deployment

1. Search for and select **Deploy a custom template**
2. On the custom deployment page, select:

```plaintext
Build your own template in the editor
```

---

### Step 2: Load the Template File

1. On the Edit template page, select:

```plaintext
Load file
```

2. Locate and select:

```plaintext
\Allfiles\Labs\06\az104-06-vms-template.json
```

3. Select:

```plaintext
Open
```

4. Select:

```plaintext
Save
```

---

### Step 3: Load the Parameters File

1. Select:

```plaintext
Edit parameters
```

2. Load the following file:

```plaintext
\Allfiles\Labs\06\az104-06-vms-parameters.json
```

3. Select:

```plaintext
Save
```

---

## ⚙️ Configure Deployment Settings

Use the following information to complete the fields on the custom deployment page.

| Setting | Value |
|---|---|
| Subscription | Your Azure subscription |
| Resource Group | `az104-rg6` (Create new if necessary) |
| Password | Provide a secure password |

> ⚠️ If you receive an error that the VM size is unavailable, select another available SKU with at least 2 cores.

---

## ✅ Deploy the Resources

1. Select:

```plaintext
Review + create
```

2. Select:

```plaintext
Create
```

> ⏳ Wait approximately 5 minutes for the deployment to complete before continuing.

---

## 📌 Resources Deployed

The template deploys:

- 🌐 One virtual network
- 🔒 One network security group
- 💻 Three virtual machines
- 🧩 Three subnets

---

# ⚖️ Task 2: Configure an Azure Load Balancer

In this task, you implement an Azure Load Balancer in front of two Azure virtual machines in the virtual network.

Azure Load Balancer provides:

- ⚡ Layer 4 (TCP/UDP) load balancing
- 🌍 Public traffic distribution
- 🔄 High availability

---

# 🏗️ Create the Azure Load Balancer

---

## Step 1: Open Load Balancers

1. Search for and select:

```plaintext
Load balancers
```

2. On the Load balancers blade, select:

```plaintext
+ Create
```

---

## ⚙️ Configure Basic Settings

Use the following settings:

| Setting | Value |
|---|---|
| Subscription | Your Azure subscription |
| Resource Group | `az104-rg6` |
| Name | `az104-lb` |
| Region | Same region as the deployed VMs |
| SKU | Standard |
| Type | Public |
| Tier | Regional |

Select:

```plaintext
Next : Frontend IP configuration
```

---

# 🌐 Configure Frontend IP

---

## ➕ Add Frontend IP Configuration

Select:

```plaintext
Add a frontend IP configuration
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-fe` |
| IP type | IP address |
| Gateway Load balancer | None |
| Public IP address | Create new |

---

## 🌍 Configure Public IP Address

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-lbpip` |
| SKU | Standard |
| Tier | Regional |
| Assignment | Static |
| Routing Preference | Microsoft network |

Select:

```plaintext
Save
```

Then select:

```plaintext
Next : Backend pools
```

---

# 🖥️ Configure Backend Pool

---

## ➕ Add Backend Pool

Select:

```plaintext
Add a backend pool
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-be` |
| Virtual network | `az104-06-vnet1 (az104-rg6)` |
| Backend Pool Configuration | NIC |

---

## ➕ Add Virtual Machines

Select the following virtual machines:

- ☑️ `az104-06-vm0`
- ☑️ `az104-06-vm1`

Select:

```plaintext
Add
```

Then select:

```plaintext
Save
```

Select:

```plaintext
Next : Inbound rules
```

---

# 📥 Configure Load Balancing Rule

---

## ➕ Add Load Balancing Rule

Navigate to:

```plaintext
Settings → Load balancing rules
```

Select:

```plaintext
+ Add
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-lbrule` |
| IP Version | IPv4 |
| Frontend IP Address | `az104-fe` |
| Backend pool | `az104-be` |
| Protocol | TCP |
| Port | 80 |
| Backend port | 80 |

---

## ❤️ Configure Health Probe

Select:

```plaintext
Create new
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-hp` |
| Protocol | TCP |
| Port | 80 |
| Interval | 5 |

Select:

```plaintext
Save
```

---

## ⚙️ Additional Load Balancer Settings

| Setting | Value |
|---|---|
| Session persistence | None |
| Idle timeout (minutes) | 4 |
| Enable TCP reset | Disabled |
| Enable Floating IP | Disabled |
| Outbound source network address translation (SNAT) | Recommended |

Select:

```plaintext
Save
```

---

# 🌍 Test the Load Balancer

---

## 📋 Copy Public IP Address

1. Navigate to:

```plaintext
Frontend IP configuration
```

2. Copy the Public IP address.

---

## 🌐 Open Browser

Open another browser tab and navigate to the public IP address.

You should see either:

```plaintext
Hello World from az104-06-vm0
```

or

```plaintext
Hello World from az104-06-vm1
```

---

## 🔄 Verify Load Balancing

Refresh the browser multiple times.

You should observe traffic alternating between:

- 💻 `az104-06-vm0`
- 💻 `az104-06-vm1`

> 📌 You may need to open an InPrivate/Incognito window to observe the change.

---

# 🚪 Task 3: Configure an Azure Application Gateway

In this task, you implement an Azure Application Gateway in front of two Azure virtual machines.

Azure Application Gateway provides:

- 🌐 Layer 7 load balancing
- 🔥 Web Application Firewall (WAF)
- 🔒 SSL termination
- 🛣️ Path-based routing

---

# 🧩 Create Dedicated Application Gateway Subnet

---

## Step 1: Open Virtual Networks

1. Search for and select:

```plaintext
Virtual networks
```

2. Select:

```plaintext
az104-06-vnet1
```

---

## ➕ Add a Subnet

Navigate to:

```plaintext
Settings → Subnets
```

Select:

```plaintext
+ Subnet
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `subnet-appgw` |
| Starting address | `10.60.3.224` |
| Size | `/27` |

> ⚠️ Ensure the starting address remains `10.60.3.224`.

Select:

```plaintext
Add
```

> 📌 Application Gateway requires a dedicated subnet of `/27` or larger.

---

# 🚀 Create the Application Gateway

---

## Step 1: Open Application Gateways

1. Search for and select:

```plaintext
Application gateways
```

2. Select:

```plaintext
+ Create
```

---

# ⚙️ Configure Basic Settings

Use the following settings:

| Setting | Value |
|---|---|
| Subscription | Your Azure subscription |
| Resource Group | `az104-rg6` |
| Application gateway name | `az104-appgw` |
| Region | Same Azure region used in Task 1 |
| Tier | Standard V2 |
| Enable autoscaling | No |
| Instance count | 2 |
| HTTP2 | Disabled |
| Virtual network | `az104-06-vnet1` |
| Subnet | `subnet-appgw (10.60.3.224/27)` |

Select:

```plaintext
Next : Frontends
```

---

# 🌐 Configure Frontend

Use the following settings:

| Setting | Value |
|---|---|
| Frontend IP address type | Public |
| Public IP address | Add new |
| Name | `az104-gwpip` |
| Availability zone | 1 |

Select:

```plaintext
OK
```

Then select:

```plaintext
Next : Backends
```

---

# 🖥️ Configure Backend Pools

---

## 🔹 Backend Pool 1

Select:

```plaintext
Add a backend pool
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-appgwbe` |
| Add backend pool without targets | No |
| Virtual machine | `az104-06-nic1 (10.60.1.4)` |
| Virtual machine | `az104-06-nic2 (10.60.2.4)` |

Select:

```plaintext
Add
```

---

## 🖼️ Backend Pool for Images

Select:

```plaintext
Add a backend pool
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-imagebe` |
| Add backend pool without targets | No |
| Virtual machine | `az104-06-nic1 (10.60.1.4)` |

Select:

```plaintext
Add
```

---

## 🎥 Backend Pool for Videos

Select:

```plaintext
Add a backend pool
```

Use the following settings:

| Setting | Value |
|---|---|
| Name | `az104-videobe` |
| Add backend pool without targets | No |
| Virtual machine | `az104-06-nic2 (10.60.2.4)` |

Select:

```plaintext
Add
```

---

# 🛣️ Configure Routing Rules

Select:

```plaintext
Next : Configuration
```

Select:

```plaintext
Add a routing rule
```

---

## ⚙️ Configure Listener

Use the following settings:

| Setting | Value |
|---|---|
| Rule name | `az104-gwrule` |
| Priority | 10 |
| Listener name | `az104-listener` |
| Frontend IP | Public IPv4 |
| Protocol | HTTP |
| Port | 80 |
| Listener type | Basic |

---

# 🎯 Configure Backend Targets

Move to the Backend targets tab.

Use the following settings:

| Setting | Value |
|---|---|
| Backend target | `az104-appgwbe` |
| Backend settings | `az104-http` (Create new) |

Select:

```plaintext
Add
```

---

# 🖼️ Configure Path-Based Routing

Select:

```plaintext
Add multiple targets
```

---

## 🖼️ Image Routing Rule

Use the following settings:

| Setting | Value |
|---|---|
| Path | `/image/*` |
| Target name | `images` |
| Backend settings | `az104-http` |
| Backend target | `az104-imagebe` |

Select:

```plaintext
Add
```

---

## 🎥 Video Routing Rule

Use the following settings:

| Setting | Value |
|---|---|
| Path | `/video/*` |
| Target name | `videos` |
| Backend settings | `az104-http` |
| Backend target | `az104-videobe` |

Select:

```plaintext
Add
```

---

# ✅ Deploy the Application Gateway

1. Select:

```plaintext
Next : Tags
```

2. No changes are required.

3. Select:

```plaintext
Next : Review + create
```

4. Select:

```plaintext
Create
```

> ⏳ Deployment takes approximately 5–10 minutes.

---

# 🩺 Verify Backend Health

After deployment:

1. Search for and select:

```plaintext
az104-appgw
```

2. Navigate to:

```plaintext
Monitoring → Backend health
```

✅ Both backend servers should display:

```plaintext
Healthy
```

---

# 🌍 Test Application Gateway Routing

---

## 🖼️ Test Image Routing

1. Copy the Frontend Public IP address.
2. Open a browser window and test:

```plaintext
http://<frontend-ip>/image/
```

✅ You should be routed to the image server:

```plaintext
vm1
```

---

## 🎥 Test Video Routing

Open another browser window and test:

```plaintext
http://<frontend-ip>/video/
```

✅ You should be routed to the video server:

```plaintext
vm2
```

> 📌 You may need to refresh multiple times or use an InPrivate/Incognito window.

---

# 🧹 Cleanup Resources

If you are working in your own subscription, remove the lab resources to minimize cost.

---

## 🗑️ Delete Resource Group Using Azure Portal

1. Open the resource group.
2. Select:

```plaintext
Delete resource group
```

3. Enter the resource group name:

```plaintext
az104-rg6
```

4. Select:

```plaintext
Delete
```

---

## 💻 Delete Using Azure PowerShell

```powershell
Remove-AzResourceGroup -Name resourceGroupName
```

---

## 💻 Delete Using Azure CLI

```bash
az group delete --name resourceGroupName
```

---

# 🤖 Extend Your Learning with Copilot

Try these prompts in Copilot:

- Compare Azure Load Balancer and Azure Application Gateway
- What tools are available to troubleshoot Azure Load Balancer connections?
- Provide a checklist for configuring Azure Application Gateway
- Compare Azure load balancing solutions

---

# 📚 Learn More with Self-Paced Training

---

## 🌐 Introduction to Azure Load Balancer

Learn:

- Load balancing concepts
- Layer 4 traffic distribution
- High availability configuration

---

## 🚪 Introduction to Azure Application Gateway

Learn:

- Layer 7 load balancing
- SSL termination
- Web Application Firewall (WAF)
- Path-based routing

---

# 📝 Key Takeaways

- ✅ Azure Load Balancer distributes traffic at Layer 4 (TCP/UDP)
- ✅ Public Load Balancer distributes internet traffic to VMs
- ✅ Standard Load Balancer provides high availability and redundancy
- ✅ Azure Application Gateway provides Layer 7 HTTP/HTTPS routing
- ✅ Application Gateway supports:
  - Path-based routing
  - SSL termination
  - WAF protection
  - HTTP header inspection

---

# 🎉 Congratulations

You have successfully completed:

# 🌟 Lab 06 - Implement Network Traffic Management 🌟

Click **End** to mark the lab as complete.
