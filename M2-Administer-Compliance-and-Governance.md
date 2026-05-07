# 🛡️ Module 2: Administer Governance and Compliance

## 📚 Overview

This module focuses on **governance and compliance in Azure**, which ensures that cloud resources are organized, secured, and controlled according to organizational policies.

It covers how to structure resources, control access, and enforce rules using Azure governance tools.

---

# 🧠 Core Concept of Azure Governance

Azure governance is the framework used to:
- 🏗️ Organize resources
- 🔐 Control access
- 📊 Monitor compliance
- ⚙️ Enforce policies
- 💰 Manage costs

It ensures that cloud environments remain secure, consistent, and well-managed.

---

# 🏢 Lesson 1: Configure Management Groups

## 📖 What are Management Groups?

Management Groups provide a **hierarchical structure** above subscriptions in Azure.

They are used to apply governance rules across multiple subscriptions.

---

## 🧩 Hierarchy Structure

```
Tenant (Microsoft Entra ID)
   └── Management Groups
        └── Subscriptions
             └── Resource Groups
                  └── Resources
```

---

## 🎯 Purpose of Management Groups

- 🌐 Organize multiple subscriptions
- 🔐 Apply policies at scale
- 👥 Manage access control centrally
- 📊 Improve governance consistency

---

## 📌 Key Features

- Can contain multiple subscriptions
- Can be nested (parent-child structure)
- Policies and roles apply downward

---

## 🛠️ Example Use Case

A company uses:
- Management Group for "Production"
- Management Group for "Development"

Each group has different policies and access rules.

---

# 💳 Lesson 2: Manage Subscriptions

## 📖 What is an Azure Subscription?

An Azure Subscription is a billing and resource container for Azure services.

---

## 🎯 Purpose of Subscriptions

- 💰 Billing management
- 🧾 Resource isolation
- 🔐 Access control boundary
- 📊 Usage tracking

---

## 📌 Types of Subscriptions

- Pay-As-You-Go
- Enterprise Agreement
- Free Trial
- Student Subscription

---

## ⚙️ Subscription Management Tasks

- Create subscriptions
- Assign owners
- Set spending limits
- Monitor usage
- Apply policies

---

## 🧠 Best Practice

Use separate subscriptions for:
- Production environments
- Development environments
- Testing environments

---

# 📁 Lesson 3: Manage Resource Groups

## 📖 What is a Resource Group?

A Resource Group is a logical container that holds related Azure resources.

---

## 📦 Example Resources in a Resource Group

- Virtual Machines
- Storage Accounts
- Databases
- Web Apps

---

## 🎯 Purpose of Resource Groups

- 🧹 Organize resources logically
- 🔐 Apply access control
- 📊 Manage lifecycle together
- 🗑️ Delete resources as a group

---

## 🛠️ Resource Group Operations

- Create resource group
- Move resources
- Delete resource group
- Assign permissions

---

## 🧠 Best Practice

Group resources by:
- Application
- Environment (Dev/Test/Prod)
- Department

---

# 🔒 Lesson 4: Configure Resource Locks

## 📖 What are Resource Locks?

Resource Locks prevent accidental deletion or modification of Azure resources.

---

## 🔐 Types of Locks

| Lock Type | Description |
|---|---|
| Read-Only 🔒 | Users can read but cannot modify |
| Delete Lock 🗑️ | Prevents deletion of resources |

---

## 🎯 Purpose of Resource Locks

- Prevent accidental deletion
- Protect critical resources
- Maintain system stability

---

## 🛠️ Example

Lock a production database to prevent accidental deletion.

---

# 👤 Lesson 5: Manage Built-In Azure Roles

## 📖 What are Azure Roles?

Azure Roles define permissions for users and services.

They are part of **Role-Based Access Control (RBAC)**.

---

## 🔐 Common Built-In Roles

| Role | Description |
|---|---|
| Owner 👑 | Full control of resources |
| Contributor ✏️ | Can manage resources but not assign access |
| Reader 👁️ | Can view resources only |
| User Access Administrator 🔑 | Manages access permissions |

---

## 🧠 Key Concept

Roles determine:
- What you can do
- What resources you can access
- What permissions you have

---

# 🎯 Lesson 6: Assign Roles at Different Scopes

## 📖 What is Scope?

Scope defines **where a role assignment applies**.

---

## 📌 Azure Scope Levels

| Scope Level | Description |
|---|---|
| Management Group 🌐 | Applies to all subscriptions under it |
| Subscription 💳 | Applies to all resources in subscription |
| Resource Group 📁 | Applies to all resources in group |
| Resource 🧩 | Applies to a single resource |

---

## 🛠️ Role Assignment Example

- Assign **Reader role** at Subscription level → applies to all resources
- Assign **Contributor role** at Resource Group level → applies only within that group

---

## 🎯 Best Practice

- Use higher scope for general access
- Use lower scope for strict control

---

# 📜 Lesson 7: Implement and Manage Azure Policy

## 📖 What is Azure Policy?

Azure Policy is a service that enforces rules and standards across Azure resources.

---

## 🎯 Purpose of Azure Policy

- Enforce compliance rules
- Prevent non-compliant resources
- Automate governance
- Standardize configurations

---

## 📌 Examples of Policies

- Allow only specific VM sizes
- Restrict regions (e.g., only Southeast Asia)
- Require tags on resources
- Enforce encryption

---

## ⚙️ Policy Components

### 1️⃣ Policy Definition
Defines the rule.

### 2️⃣ Policy Assignment
Applies the rule to scope (management group, subscription, etc.).

### 3️⃣ Policy Initiative
A group of multiple policies.

---

## 🚦 Policy Effects

| Effect | Description |
|---|---|
| Deny 🚫 | Blocks non-compliant resources |
| Audit 📊 | Logs non-compliance |
| Append ➕ | Adds missing configuration |
| Modify ✏️ | Changes resource settings |

---

## 🧠 Example Policy

> Only allow resources in "Southeast Asia" region.

If a user tries to deploy in another region:
- Deployment is blocked

---

# 🔗 Relationship of Governance Components

```
Management Groups
   ↓
Subscriptions
   ↓
Resource Groups
   ↓
Resources
   ↓
Policies + Roles + Locks
```

---

# 🎯 Summary of Module 2

| Lesson | Focus |
|---|---|
| Management Groups | Organize subscriptions |
| Subscriptions | Billing and resource boundaries |
| Resource Groups | Logical grouping of resources |
| Resource Locks | Prevent accidental changes |
| Built-In Roles | Define permissions |
| Role Scopes | Control where roles apply |
| Azure Policy | Enforce rules and compliance |

---

# 📝 Final Summary

Module 2 focuses on **Azure governance and compliance**, ensuring that cloud resources are properly organized, secured, and controlled. It combines structure (management groups, subscriptions), security (roles, locks), and enforcement (Azure Policy) to maintain a well-governed Azure environment.
```
