# AZ-104 Reviewer
# Domain: Manage Azure Identities and Governance

---

# 📚 Exam Coverage

This domain covers:
- Microsoft Entra ID
- Users and Groups
- Role-Based Access Control (RBAC)
- Subscriptions and Management Groups
- Azure Policy
- Resource Locks
- Tags
- Cost Management
- Governance Features

Weight in Exam:
20–25%

---

# ☁️ Microsoft Entra ID (Formerly Azure Active Directory)

## Overview

Microsoft Entra ID is Azure's cloud-based identity and access management service.

Functions:
- Authentication
- Authorization
- Single Sign-On (SSO)
- Identity Management
- Conditional Access
- Multi-Factor Authentication

---

# 🏢 Tenant

A tenant is a dedicated instance of Microsoft Entra ID.

Example:
- company.onmicrosoft.com

A tenant contains:
- Users
- Groups
- Applications
- Devices
- Policies

---

# 👤 Users

## Types of Users

| User Type | Description |
|---|---|
| Member | Internal organization user |
| Guest | External/B2B user |

---

# 🔹 User Management

Common Tasks:
- Create users
- Reset passwords
- Assign licenses
- Delete users
- Configure authentication methods

---

# 🔹 Bulk User Creation

Can import users using:
- CSV
- PowerShell
- Azure CLI

---

# 🔐 Password Management

## Self-Service Password Reset (SSPR)

Allows users to reset passwords without administrator help.

Authentication Methods:
- Email
- SMS
- Authenticator App
- Security Questions

Important:
SSPR can be enabled for:
- All users
- Selected groups

---

# 👥 Groups

Used to simplify permission management.

---

# 🔹 Group Types

| Group Type | Description |
|---|---|
| Security Group | Permission management |
| Microsoft 365 Group | Collaboration tools |

---

# 🔹 Membership Types

| Membership | Description |
|---|---|
| Assigned | Manual |
| Dynamic User | Automatic based on rules |
| Dynamic Device | Device-based rules |

---

# 🔹 Dynamic Membership Example

```text
department -eq "IT"
```

Automatically adds IT users into group.

---

# 🌍 Administrative Units

Used to delegate administrative control to specific departments or regions.

Example:
- HR admins manage only HR users.

---

# 🔐 Multi-Factor Authentication (MFA)

Adds additional security layer.

---

# 🔹 MFA Methods

| Method | Description |
|---|---|
| SMS | Text code |
| Voice Call | Phone verification |
| Authenticator App | Push notification |
| FIDO2 Key | Hardware token |

---

# 🔹 MFA Concepts

| Feature | Description |
|---|---|
| Enabled | User prompted |
| Enforced | Mandatory |
| Disabled | Not used |

---

# 🔐 Conditional Access

Controls sign-in access based on conditions.

---

# 🔹 Common Conditions

| Condition | Example |
|---|---|
| Location | Outside company network |
| Device | Non-compliant device |
| Application | Office 365 |
| Risk | High-risk sign-in |

---

# 🔹 Common Actions

| Action | Description |
|---|---|
| Require MFA | Extra verification |
| Block Access | Deny sign-in |
| Require Compliant Device | Intune managed |

---

# 🔹 Conditional Access Example

```text
IF:
- User outside Philippines

THEN:
- Require MFA
```

---

# 🔐 Role-Based Access Control (RBAC)

Controls WHO can access Azure resources.

---

# 🔹 RBAC Components

| Component | Description |
|---|---|
| Security Principal | User, group, app |
| Role Definition | Permission set |
| Scope | Level of access |

---

# 🔹 RBAC Scope Hierarchy

```text
Management Group
 └── Subscription
      └── Resource Group
           └── Resource
```

Permissions inherit downward.

---

# 🔹 Built-in Roles

| Role | Permissions |
|---|---|
| Owner | Full access + assign access |
| Contributor | Manage resources only |
| Reader | View only |
| User Access Administrator | Manage RBAC |

---

# 🔹 Important RBAC Concepts

## Least Privilege
Give minimum permissions required.

---

## Inheritance
Permissions assigned at higher scope flow downward.

Example:
```text
Subscription Contributor
→ Applies to all resource groups/resources
```

---

## Deny Assignments
Blocks access even if RBAC allows it.

Used by:
- Azure Blueprints
- Managed Applications

---

# 🔹 Custom Roles

Can create custom permissions.

Example:
```json
{
  "Actions": [
    "Microsoft.Compute/*/read"
  ]
}
```

---

# 🔹 RBAC Assignment Requirements

To assign roles, user needs:
- Owner
OR
- User Access Administrator

---

# 💳 Azure Subscriptions

A subscription is:
- Billing boundary
- Access boundary
- Resource boundary

---

# 🔹 Subscription Uses

| Purpose | Description |
|---|---|
| Billing | Cost tracking |
| RBAC | Permission scope |
| Policy | Governance |

---

# 🏢 Management Groups

Used to organize multiple subscriptions.

---

# 🔹 Benefits

- Centralized governance
- Apply RBAC
- Apply Azure Policy
- Standardization

---

# 🔹 Hierarchy Example

```text
Tenant Root Group
 ├── Production MG
 │    ├── Subscription A
 │    └── Subscription B
 └── Development MG
```

---

# 📜 Azure Policy

Controls WHAT can be deployed.

---

# 🔹 Azure Policy vs RBAC

| Feature | RBAC | Policy |
|---|---|---|
| Purpose | Access control | Compliance |
| Focus | WHO | WHAT |

---

# 🔹 Common Policy Examples

| Policy | Purpose |
|---|---|
| Allowed Locations | Restrict regions |
| Allowed VM Sizes | Restrict SKUs |
| Require Tags | Enforce tagging |
| Enforce HTTPS | Secure traffic |

---

# 🔹 Policy Effects

| Effect | Description |
|---|---|
| Deny | Prevent deployment |
| Audit | Log non-compliance |
| Append | Add settings |
| DeployIfNotExists | Auto deploy resources |

---

# 🔹 Policy Scope

Can assign policy to:
- Management Group
- Subscription
- Resource Group
- Resource

---

# 🔹 Initiative Definition

Collection of policies grouped together.

Example:
- ISO compliance initiative
- Security baseline initiative

---

# 🔒 Resource Locks

Prevent accidental changes.

---

# 🔹 Lock Types

| Lock | Description |
|---|---|
| CanNotDelete | Cannot delete |
| ReadOnly | Cannot modify |

---

# 🔹 Lock Behavior

| Operation | ReadOnly | CanNotDelete |
|---|---|---|
| Read | ✅ | ✅ |
| Modify | ❌ | ✅ |
| Delete | ❌ | ❌ |

---

# 🏷️ Tags

Metadata for organizing resources.

Example:
```text
Environment = Production
Department = HR
CostCenter = 1001
```

---

# 🔹 Tag Uses

| Use Case | Description |
|---|---|
| Cost Tracking | Billing reports |
| Automation | Scripts |
| Organization | Resource grouping |

---

# 💰 Cost Management

Monitors Azure spending.

---

# 🔹 Features

| Feature | Description |
|---|---|
| Budgets | Spending limits |
| Alerts | Notifications |
| Reports | Cost analysis |

---

# 🔹 Budget Alerts

Can trigger:
- Email
- Action groups

Example:
```text
Alert when spending reaches 80%
```

---

# 💡 Azure Advisor

Provides optimization recommendations.

---

# 🔹 Recommendation Categories

| Category | Purpose |
|---|---|
| Cost | Save money |
| Security | Improve protection |
| Reliability | Improve uptime |
| Performance | Improve efficiency |

---

# 🔑 Privileged Identity Management (PIM)

Provides just-in-time privileged access.

---

# 🔹 PIM Features

| Feature | Description |
|---|---|
| Eligible Roles | Temporary activation |
| Approval Workflow | Admin approval |
| MFA Enforcement | Secure activation |
| Time-bound Access | Automatic expiration |

---

# 🔹 PIM Benefits

- Reduces standing privileges
- Improves security
- Tracks privileged actions

---

# 📱 Devices in Entra ID

Device identities registered in Azure.

---

# 🔹 Device States

| State | Description |
|---|---|
| Registered | BYOD devices |
| Joined | Organization-owned |
| Hybrid Joined | On-prem AD + Azure |

---

# 🔹 Device Management

Can integrate with:
- Microsoft Intune

Used for:
- Compliance
- Conditional Access

---

# 🧠 Important Exam Concepts

---

# 🔥 Frequently Asked Topics

| Topic | Importance |
|---|---|
| RBAC Inheritance | ⭐⭐⭐⭐⭐ |
| Conditional Access | ⭐⭐⭐⭐⭐ |
| Azure Policy | ⭐⭐⭐⭐⭐ |
| MFA | ⭐⭐⭐⭐ |
| Resource Locks | ⭐⭐⭐⭐ |
| Tags | ⭐⭐⭐⭐ |
| Management Groups | ⭐⭐⭐⭐ |
| PIM | ⭐⭐⭐ |

---

# ⚠️ Common Exam Confusions

---

# RBAC vs Azure Policy

| RBAC | Policy |
|---|---|
| WHO can access | WHAT can be deployed |

---

# ReadOnly Lock vs Contributor

Even Contributors CANNOT modify ReadOnly locked resources.

Locks override RBAC.

---

# Deny Assignment vs RBAC

Deny assignments take priority over allow permissions.

---

# Guest User vs Member User

| Guest | Member |
|---|---|
| External | Internal |

---

# 🧪 Common Exam Scenarios

---

# Scenario 1

Requirement:
```text
Prevent users from deploying VMs outside East US.
```

Answer:
```text
Azure Policy
```

---

# Scenario 2

Requirement:
```text
Allow helpdesk to reset passwords only for HR users.
```

Answer:
```text
Administrative Units
```

---

# Scenario 3

Requirement:
```text
Provide temporary Owner access for 2 hours.
```

Answer:
```text
Privileged Identity Management (PIM)
```

---

# Scenario 4

Requirement:
```text
Prevent accidental deletion of production resources.
```

Answer:
```text
Resource Locks
```

---

# 📚 Memorization Tips

---

# Remember:

## RBAC
WHO can access

## Azure Policy
WHAT can exist

## Locks
Protect existing resources

## Tags
Organize resources

## Management Groups
Organize subscriptions

---

# 🛠️ Recommended Hands-On Practice

Practice:
- Create users/groups
- Assign RBAC roles
- Configure Conditional Access
- Enable MFA
- Create Azure Policy
- Apply resource locks
- Configure tags
- Create management groups
- Configure budget alerts

---

# 📖 Official Microsoft Resources

AZ-104 Skills Measured:
https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104/

Microsoft Entra ID Documentation:
https://learn.microsoft.com/en-us/entra/

Azure RBAC Documentation:
https://learn.microsoft.com/en-us/azure/role-based-access-control/

Azure Policy Documentation:
https://learn.microsoft.com/en-us/azure/governance/policy/
