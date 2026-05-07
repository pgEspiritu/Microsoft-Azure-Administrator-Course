# Lab (Initial): Create a Microsoft Entra ID Tenant

## Step 1: Sign in to Azure Portal

1. Open the Azure Portal:
   https://portal.azure.com

2. Sign in using the following credentials:

| Field | Value |
|---|---|
| Username | `LabUser-61581520@LODSPRODMSLEARNMCA.onmicrosoft.com` |
| TAP Token | `EXuXApH6` |

---

## Step 2: Open Microsoft Entra ID

1. Search for and select **Microsoft Entra ID**.

---

## Step 3: Create a New Tenant

1. From the **Azure Active Directory Overview** blade, select:
   - **Manage Tenants**
   - then click **+ Create**

2. On the **Basics** tab:
   - Select **Microsoft Entra ID**
   - Click **Next: Configuration**

---

## Step 4: Configure Tenant Settings

Configure the following fields:

| Setting | Value |
|---|---|
| Organization Name | `First AAD` |
| Initial Domain Name | `firstaad61581520` |
| Country/Region | `United States` |

1. Click **Review + Create**
2. Click **Create**

---

## Step 5: Complete CAPTCHA

1. On the **Help us prove you're not a robot** pane:
   - Type the CAPTCHA letters
   - Click **Submit**

2. Wait for directory creation to complete.

> **Note:**  
> If the CAPTCHA form fails, the tenant may still be created.  
> Check the **Manage Tenant** section before attempting to create the tenant again.

---

## Step 6: Open the Newly Created Tenant

1. When tenant creation is successful, click:
   - **Click here to navigate to your new tenant**

2. Select the **First AAD** link.

---

## Step 7: Reauthenticate if Required

If prompted for authentication due to MFA requirements, sign in again using:

| Field | Value |
|---|---|
| Azure Portal | `https://portal.azure.com/` |
| Username | `LabUser-61581520@LODSPRODMSLEARNMCA.onmicrosoft.com` |
| Temporary Access Pass (TAP) Token | `EXuXApH6` |

---

## Step 8: Proceed to the 1st Lab

---

# Lab 01 - Manage Microsoft Entra ID Identities

## Lab Introduction

This lab introduces the management of Microsoft Entra ID users and groups.

Users and groups are the foundational components of an identity solution in Azure.

- **Estimated Time:** 30 minutes
- **Region Used:** East US

---

# Lab Scenario

Your organization is building a new lab environment for pre-production testing of applications and services.

You are tasked with:
- Provisioning users and groups in Microsoft Entra ID
- Allowing engineers to authenticate using Microsoft Entra ID
- Configuring groups with automated membership management based on job titles

---

# Job Skills

## Tasks Covered

- Task 1: Create and configure user accounts
- Task 2: Create groups and add members

---

# Task 1: Create and Configure User Accounts

## Step 1: Sign in to Azure Portal

1. Open the Azure Portal:
   https://portal.azure.com

2. If prompted with the **Welcome to Azure** splash screen:
   - Select **Cancel**

---

## Step 2: Open Microsoft Entra ID

1. Search for and select **Microsoft Entra ID**.

2. Review the available options in the left navigation pane.

3. Select:
   - **Overview**
   - then **Manage tenants**

> **Note:**  
> A tenant is a dedicated instance of Microsoft Entra ID that contains users, groups, and resources.

4. Return to the Microsoft Entra ID page.

---

## Step 3: Create a New User

1. In the **Manage** blade, select:
   - **Users**
   - then **New user**
   - select **Create new user**

2. Configure the following settings:

| Setting | Value |
|---|---|
| User principal name | `az104-user1` |
| Display name | `az104-user1` |
| Auto-generate password | Checked |
| Account enabled | Checked |
| Job title | `IT Lab Administrator` |
| Department | `IT` |
| Usage location | `United States` |

3. Select:
   - **Review + create**
   - then **Create**

4. Refresh the page and confirm the user was created.

---

## Step 4: Invite an External User

1. In the **New user** drop-down, select:
   - **Invite an external user**

2. Configure the following settings:

| Setting | Value |
|---|---|
| Email | Your email address |
| Display name | Your name |
| Send invite message | Checked |
| Message | `Welcome to Azure and our group project` |

3. Open the **Properties** tab and configure:

| Setting | Value |
|---|---|
| Job title | `IT Lab Administrator` |
| Department | `IT` |
| Usage location | `United States` |

4. Select:
   - **Review + invite**
   - then **Invite**

5. Refresh the page and confirm the guest user was created.

> **Note:**  
> The invitation email should arrive shortly.

---

# Task 2: Create Groups and Add Members

## Step 1: Open Groups

1. In the Azure portal, search for and select:
   - **Microsoft Entra ID**

2. In the **Manage** blade, select:
   - **Groups**

3. Review available group configuration settings.

---

## Step 2: Create a Security Group

1. In the **All groups** blade, select:
   - **+ New group**

2. Configure the following settings:

| Setting | Value |
|---|---|
| Group type | `Security` |
| Group name | `IT Lab Administrators` |
| Group description | `Administrators that manage the IT lab` |
| Membership type | `Assigned` |

> **Note:**  
> Dynamic membership requires Microsoft Entra ID Premium P1 or P2 licensing.

---

## Step 3: Assign Group Owners

1. Select:
   - **No owners selected**

2. Search for and select your account as the owner.

3. Confirm the selection.

---

## Step 4: Add Group Members

1. Select:
   - **No members selected**

2. Add the following users:
   - `az104-user1`
   - The invited guest user

3. Confirm the member selections.

---

## Step 5: Create the Group

1. Select:
   - **Create**

2. Refresh the page and verify the group was created successfully.

3. Open the newly created group and review:
   - Members
   - Owners

---

# Extend Your Learning with Copilot

Try the following prompts in Microsoft Copilot:

- What are the Azure PowerShell and CLI commands to create a security group called IT Admins?
- Provide a step-by-step strategy for managing users and groups in Microsoft Entra ID.
- What are the steps in the Azure portal to bulk create users and groups?
- Provide a comparison table of internal and external Microsoft Entra ID user accounts.

---

# Key Takeaways

- A tenant represents an organization within Microsoft cloud services.
- Microsoft Entra ID supports both internal and guest accounts.
- Groups help organize users and devices.
- Group membership can be assigned statically or dynamically.
