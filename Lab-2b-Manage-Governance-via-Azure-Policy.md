# Lab 02b - Manage Governance via Azure Policy

## Lab Introduction

This lab focuses on implementing governance in Azure using:
- Azure Policy
- Resource tagging
- Resource locks

- **Estimated Time:** 30 minutes
- **Region Used:** East US

---

# Lab Scenario

Your organization needs to improve Azure governance by:

- Applying resource tags
- Enforcing tags using Azure Policy
- Updating existing resources with tags
- Protecting resources using resource locks

---

# Job Skills

## Tasks Covered

- Task 1: Create and assign tags via the Azure portal
- Task 2: Enforce tagging via Azure Policy
- Task 3: Apply tagging via Azure Policy
- Task 4: Configure and test resource locks

---

# Task 1: Assign Tags via the Azure Portal

## Step 1: Sign in to Azure Portal

1. Open the Azure Portal:
   https://portal.azure.com

---

## Step 2: Create a Resource Group

1. Search for and select:
   - **Resource groups**

2. Select:
   - **+ Create**

![Lab-3.1](images/Lab-3.1.png)

3. Configure the following settings:

| Setting | Value |
|---|---|
| Subscription | Your subscription |
| Resource group name | `az104-rg2` |
| Region | `East US` |

![Lab-3.2](images/Lab-3.2.png)

> **Note:**  
> A separate resource group is created for each lab to simplify management.

---

## Step 3: Add a Tag

1. Select:
   - **Next**

2. Open the:
   - **Tags** tab

3. Configure the tag:

| Setting | Value |
|---|---|
| Name | `Cost Center` |
| Value | `000` |

![Lab-3.3](images/Lab-3.3.png)

4. Select:
   - **Review + Create**
   - then **Create**

![Lab-3.4](images/Lab-3.4.png)

---

# Task 2: Enforce Tagging via Azure Policy

## Step 1: Open Azure Policy

1. Search for and select:
   - **Policy**

2. In the **Authoring** blade, select:
   - **Definitions**

3. Search for:
   - `Require a tag and its value on resources`

![Lab-3.5](images/Lab-3.5.png)

4. Review the policy definition.

---

## Step 2: Assign the Policy

1. Select:
   - **Assign policy**

![Lab-3.6](images/Lab-3.6.png)

2. Configure the scope:

| Setting | Value |
|---|---|
| Subscription | Your subscription |
| Resource Group | `az104-rg2` |

3. Select:
   - **Select**

![Lab-3.7](images/Lab-3.7.png)

---

## Step 3: Configure Policy Basics

Configure the following settings:

| Setting | Value |
|---|---|
| Assignment name | `Require Cost Center tag and its value on resources` |
| Description | `Require Cost Center tag and its value on all resources in the resource group` |
| Policy enforcement | `Enabled` |

4. Select:
   - **Next**

![Lab-3.8](images/Lab-3.8.png)

---

## Step 4: Configure Policy Parameters

Set the following values:

| Setting | Value |
|---|---|
| Tag Name | `Cost Center` |
| Tag Value | `000` |

![Lab-3.9](images/Lab-3.9.png)

1. Select:
   - **Next**

2. Leave:
   - **Create a Managed Identity** unchecked

3. Select:
   - **Review + Create**
   - then **Create**

![Lab-3.10](images/Lab-3.10.png)

> **Note:**  
> It may take 5–10 minutes for the policy assignment to take effect.

---

## Step 5: Test the Policy

1. Search for and select:
   - **Storage accounts**

2. Select:
   - **+ Create**

![Lab-3.11](images/Lab-3.11.png)

3. Configure the following:

| Setting | Value |
|---|---|
| Resource group | `az104-rg2` |
| Storage account name | Any globally unique name |

![Lab-3.12](images/Lab-3.12.png)

4. Select:
   - **Review**
   - then **Create**

> **Expected Result:**  
> Deployment should fail because the required tag was not added.

![Lab-3.13](images/Lab-3.13.png)

---

# Task 3: Apply Tagging via Azure Policy

## Step 1: Delete the Existing Policy Assignment

1. Search for and select:
   - **Policy**

2. In the **Authoring** section, select:
   - **Assignments**

3. Locate the policy assignment:
   - `Require a tag and its value on resources`

4. Select the ellipsis (**...**) and choose:
   - **Delete assignment**

![Lab-3.14](images/Lab-3.14.png)

---

## Step 2: Assign a New Policy

1. Select:
   - **Assign policy**

![Lab-3.15](images/Lab-3.15.png)

2. Configure the scope:

| Setting | Value |
|---|---|
| Subscription | Your subscription |
| Resource Group | `az104-rg2` |

---

## Step 3: Select Policy Definition

1. Search for and select:
   - `Inherit a tag from the resource group if missing`

![Lab-3.16](images/Lab-3.16.png)

2. Select:
   - **Add**

---

## Step 4: Configure Policy Basics

| Setting | Value |
|---|---|
| Assignment name | `Inherit the Cost Center tag and its value 000 from the resource group if missing` |
| Description | `Inherit the Cost Center tag and its value 000 from the resource group if missing` |
| Policy enforcement | `Enabled` |

![Lab-3.17](images/Lab-3.17.png)
![Lab-3.18](images/Lab-3.18.png)

1. Select:
   - **Next**

---

## Step 5: Configure Parameters

| Setting | Value |
|---|---|
| Tag Name | `Cost Center` |

![Lab-3.19](images/Lab-3.19.png)

1. Select:
   - **Next**

---

## Step 6: Configure Remediation

Configure the following settings:

| Setting | Value |
|---|---|
| Create a remediation task | Enabled |
| Policy to remediate | `Inherit a tag from the resource group if missing` |

![Lab-3.20](images/Lab-3.20.png)

> **Note:**  
> This policy uses the **Modify** effect and requires a managed identity.

1. Select:
   - **Review + Create**
   - then **Create**

![Lab-3.21](images/Lab-3.21.png)

---

## Step 7: Test the Policy

1. Search for and select:
   - **Storage accounts**

2. Select:
   - **+ Create**

3. Configure the following:

| Setting | Value |
|---|---|
| Resource group | `az104-rg2` |
| Storage account name | Any globally unique name |

![Lab-3.22](images/Lab-3.22.png)

4. Select:
   - **Review**
   - then **Create**

![Lab-3.23](images/Lab-3.23.png)

> **Expected Result:**  
> Deployment should succeed.

---

## Step 8: Verify the Tag

1. After deployment completes, select:
   - **Go to resource**

2. Open the:
   - **Tags** blade

3. Verify the following tag exists:

| Tag Name | Value |
|---|---|
| Cost Center | `000` |

![Lab-3.24](images/Lab-3.24.png)

---

# Task 4: Configure and Test Resource Locks

## Step 1: Open the Resource Group

1. Search for and select:
   - `az104-rg2`

---

## Step 2: Create a Resource Lock

1. In the **Settings** blade, select:
   - **Locks**

![Lab-3.25](images/Lab-3.25.png)

2. Select:
   - **Add**

3. Configure the following settings:

| Setting | Value |
|---|---|
| Lock name | `rg-lock` |
| Lock type | `Delete` |

![Lab-3.26](images/Lab-3.26.png)

4. Select:
   - **OK**

---

## Step 3: Test the Lock

1. Open the:
   - **Overview** blade

2. Select:
   - **Delete resource group**

3. Enter the resource group name:
   - `az104-rg2`

4. Select:
   - **Delete**

![Lab-3.27](images/Lab-3.27.png)
![Lab-3.28](images/Lab-3.28.png)

> **Expected Result:**  
> Deletion should fail because the resource group is protected by a lock.

![Lab-3.29](images/Lab-3.29.png)

---

# Cleanup Resources

## Delete the Resource Group Using Azure Portal

1. Remove the resource lock.

2. Open the resource group.

3. Select:
   - **Delete resource group**

4. Enter the resource group name.

5. Select:
   - **Delete**

---

## Delete Using Azure PowerShell

```powershell
Remove-AzResourceGroup -Name resourceGroupName
```

---

## Delete Using Azure CLI

```bash
az group delete --name resourceGroupName
```

---

# Extend Your Learning with Copilot

Try the following prompts in Microsoft Copilot:

- What are the Azure PowerShell and CLI commands for managing resource locks?
- Compare Azure Policy and Azure RBAC.
- How do you remediate non-compliant Azure resources?
- How can I generate reports for tagged Azure resources?

---

# Key Takeaways

- Azure tags are metadata stored as key-value pairs.
- Azure Policy enforces organizational standards and compliance.
- Policy remediation tasks bring resources into compliance automatically.
- Resource locks prevent accidental deletion or modification.
- Azure Policy is a pre-deployment governance tool.
- RBAC and resource locks provide post-deployment protection.

---

# Lab Completion

Congratulations! You have successfully completed the lab.

Select **End** to mark the lab as complete.
