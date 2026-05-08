# Lab 02a - Manage Subscriptions and RBAC

## Lab Introduction

This lab focuses on:
- Role-Based Access Control (RBAC)
- Permissions and scopes
- Management groups
- Custom Azure roles

- **Estimated Time:** 20 minutes
- **Region Used:** East US

---

# Lab Scenario

Your organization requires:
- A management group that contains all Azure subscriptions
- Permission delegation for Help Desk personnel to:
  - Create and manage virtual machines
  - Create support request tickets
- Restricted permissions to prevent adding Azure providers

---

# Job Skills

## Tasks Covered

- Task 1: Implement management groups
- Task 2: Review and assign a built-in Azure role
- Task 3: Create a custom RBAC role
- Task 4: Monitor role assignments with the Activity Log

---

# Task 1: Implement Management Groups

## Step 1: Sign in to Azure Portal

1. Open the Azure Portal:
   https://portal.azure.com

---

## Step 2: Open Microsoft Entra ID

1. Search for and select:
   - **Microsoft Entra ID**

2. In the **Manage** blade, select:
   - **Properties**

![Lab-2.1](images/Lab-2.1.png)
![Lab-2.2](images/Lab-2.2.png)

3. Review the:
   - **Access management for Azure resources** section

![Lab-2.3](images/Lab-2.3.png)

---

## Step 3: Open Management Groups

1. Search for and select:
   - **Management groups**

2. On the **Management groups** blade, select:
   - **+ Create**

![Lab-2.4](images/Lab-2.4.png)

---

## Step 4: Create a Management Group

Configure the following settings:

| Setting | Value |
|---|---|
| Management group ID | `az104-mg161582618` |
| Management group display name | `az104-mg161582618` |

![Lab-2.5](images/Lab-2.5.png)

1. Select:
   - **Submit**

2. Refresh the page and confirm the management group was created.

![Lab-2.6](images/Lab-2.6.png)

> **Note:**  
> The root management group contains all subscriptions and management groups within the tenant hierarchy.

---

# Task 2: Review and Assign a Built-in Azure Role

## Step 1: Open the Management Group

1. Select the:
   - `az104-mg161582618` management group

2. Open:
   - **Access control (IAM)**

![Lab-2.7](images/Lab-2.7.png)

3. Select the:
   - **Roles** tab

4. Review available built-in roles.

![Lab-2.8](images/Lab-2.8.png)

---

## Step 2: Add a Role Assignment

1. Select:
   - **+ Add**
   - then **Add role assignment**

![Lab-2.9](images/Lab-2.9.png)

2. Search for and select:
   - **Virtual Machine Contributor**

3. Select:
   - **Next**

> **Note:**  
> The Virtual Machine Contributor role allows management of virtual machines but does not allow access to the operating system.

![Lab-2.10](images/Lab-2.10.png)

---

## Step 3: Assign the Role to a Group

1. On the **Members** tab, select:
   - **Members**

2. Search for and select:
   - `IT Helpdesk`

3. Select:
   - **Select**

![Lab-2.11](images/Lab-2.11.png)

4. Select:
   - **Review + assign**
   - then again **Review + assign**

![Lab-2.12](images/Lab-2.12.png)

5. Confirm the `IT Helpdesk` group now has the:
   - **Virtual Machine Contributor** role

![Lab-2.13](images/Lab-2.13.png)

> **Best Practice:**  
> Assign roles to groups instead of individual users.

---

# Task 3: Create a Custom RBAC Role

## Step 1: Open Access Control

1. In the management group, open:
   - **Access control (IAM)**

2. Select:
   - **+ Add**
   - then **Add custom role**

![Lab-2.14](images/Lab-2.14.png)

---

## Step 2: Configure the Custom Role

On the **Basics** tab, configure:

| Setting | Value |
|---|---|
| Custom role name | `Custom Support Request61582618` |
| Description | `A custom contributor role for support requests.` |

### Baseline Permissions

1. Select:
   - **Clone a role**

2. From the drop-down, select:
   - **Support Request Contributor**

3. Select:
   - **Next**

![Lab-2.15](images/Lab-2.15.png)

---

## Step 3: Exclude Permissions

1. On the **Permissions** tab, select:
   - **+ Exclude permissions**

![Lab-2.16](images/Lab-2.16.png)

2. In the resource provider search field, enter:
   - `.Support`

3. Select:
   - **Microsoft.Support**

![Lab-2.17](images/Lab-2.17.png)

4. Enable the checkbox for:
   - **Other: Registers Support Resource Provider**
 
5. Select:
   - **Add**

![Lab-2.18](images/Lab-2.18.png)

> **Note:**  
> This removes the ability to register support resource providers from the custom role.

---

## Step 4: Configure Assignable Scope

1. On the **Assignable scopes** tab:
   - Confirm your management group is listed

![Lab-2.19](images/Lab-2.19.png)

2. Select:
   - **Next**

3. Review the JSON configuration for:
   - Actions
   - NotActions
   - AssignableScopes

4. Select:
   - **Review + Create**
   - then **Create**

![Lab-2.20](images/Lab-2.20.png)

---

# Task 4: Monitor Role Assignments with Activity Log

## Step 1: Open Activity Log

1. Locate the:
   - `az104-mg161582618` management group

2. Select:
   - **Activity log**

![Lab-2.21](images/Lab-2.21.png)

---

## Step 2: Review Role Assignment Activities

1. Review recent activities related to:
   - Role assignments

2. Apply filters if necessary to locate specific operations.

---

# Cleanup Resources

## Delete the Management Group Using Azure Portal

1. Open the management group.

2. Select:
   - **Delete**

3. Confirm by selecting:
   - **Yes**

---

## Delete Using Azure PowerShell

```powershell
Remove-AzManagementGroup -GroupName az104-mg161582618
```

---

## Delete Using Azure CLI

```bash
az account management-group delete --name az104-mg161582618
```

---

# Extend Your Learning with Copilot

Try the following prompts in Microsoft Copilot:

- Create tables of important Azure PowerShell and CLI commands for subscription management.
- What is the format of an Azure RBAC JSON file?
- What are the steps for creating a custom Azure RBAC role?
- What is the difference between Azure RBAC roles and Microsoft Entra ID roles?

---

# Key Takeaways

- Management groups logically organize Azure subscriptions.
- The root management group contains all subscriptions and management groups.
- Azure provides many built-in RBAC roles.
- Custom RBAC roles can be created using JSON permissions.
- Activity Logs help monitor role assignments and security-related activities.

---

# Lab Completion

Congratulations! You have successfully completed the lab.

Select **End** to mark the lab as complete.
