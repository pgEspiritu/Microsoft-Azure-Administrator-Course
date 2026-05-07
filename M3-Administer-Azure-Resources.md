# ☁️ Module 3: Administer Azure Resources

## 📚 Overview

This module focuses on how to **deploy and manage Azure resources using Infrastructure as Code (IaC)**. It teaches how to create, modify, and manage Azure resources using:

- 🧾 Azure Resource Manager (ARM) Templates  
- 🧱 Bicep Files  

These tools allow you to automate deployments, ensure consistency, and reduce manual configuration errors.

---

# 🧠 Core Concept: Infrastructure as Code (IaC)

## 📖 What is IaC?

Infrastructure as Code is the practice of managing and provisioning cloud resources using code instead of manual processes.

---

## 🎯 Benefits of IaC

- ⚡ Faster deployments  
- 🔁 Repeatable and consistent environments  
- 🔐 Reduced human error  
- 📊 Version control support  
- 🧪 Easier testing and rollback  

---

# 🧾 Lesson 1: Deploy Resources by Using ARM Template or Bicep File

## 📖 Azure Resource Manager (ARM) Template

An ARM template is a **JSON-based file** that defines Azure resources and their configurations.

---

## 🧩 ARM Template Structure

```json
{
  "$schema": "https://schema.management.azure.com/...",
  "contentVersion": "1.0.0.0",
  "resources": [
    {
      "type": "Microsoft.Storage/storageAccounts",
      "name": "mystorageaccount",
      "apiVersion": "2023-01-01",
      "location": "eastus",
      "sku": {
        "name": "Standard_LRS"
      },
      "kind": "StorageV2"
    }
  ]
}
``` id="armtpl1"

---

## 🏗️ What ARM Templates Do

- 📦 Define infrastructure in JSON
- 🚀 Deploy Azure resources automatically
- 🔁 Ensure consistent environments

---

## 📖 Bicep File

Bicep is a **simplified, declarative language** for deploying Azure resources. It is designed to replace ARM JSON templates.

---

## 🧱 Example Bicep File

```bicep
resource storageAccount 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: 'mystorageaccount'
  location: 'eastus'
  sku: {
    name: 'Standard_LRS'
  }
  kind: 'StorageV2'
}
``` id="bicep1"

---

## 🎯 ARM vs Bicep

| Feature | ARM Template | Bicep |
|---|---|---|
| Format | JSON | Simple DSL |
| Readability | Complex | Easy |
| Maintenance | Hard | Easier |
| Learning Curve | High | Low |

---

## 🛠️ Deployment Methods

- Azure Portal 🌐  
- Azure CLI 💻  
- PowerShell ⚡  
- Azure DevOps / GitHub Actions 🔁  

---

# ✏️ Lesson 2: Modify an Existing Azure Resource Manager Template

## 📖 Why Modify ARM Templates?

You modify ARM templates to:
- Update resource configurations
- Add new resources
- Fix deployment issues
- Improve performance or security

---

## 🛠️ Common Modifications

### 🔄 Change Resource Properties
Example:
- Update VM size
- Change storage SKU
- Modify location

---

### ➕ Add New Resources
You can add:
- Virtual Machines
- Storage accounts
- Networks
- Databases

---

### ❌ Remove Resources
Remove unused or deprecated infrastructure components.

---

## 🧠 Best Practices for ARM Templates

- Use parameters for flexibility
- Use variables for reuse
- Validate templates before deployment
- Store templates in version control (Git)

---

## ⚙️ Deployment Validation

Before deploying:
- Use `az deployment group validate`
- Check for syntax errors
- Ensure required parameters are provided

---

# 🧱 Lesson 3: Modify an Existing Bicep File

## 📖 Why Modify Bicep Files?

Bicep files are modified to:
- Improve infrastructure design
- Add or remove resources
- Update configurations
- Scale environments

---

## 🛠️ Common Bicep Modifications

### 🔄 Update Resource Settings
Example:
- Change VM size
- Modify SKU
- Adjust network configuration

---

### ➕ Add New Modules or Resources

Bicep supports modular design.

Example:
- Add storage account module
- Add virtual network module

---

### 🧩 Use Parameters for Flexibility

```bicep
param location string = 'eastus'
param storageName string
``` id="bicep2"

---

## 🔁 Reusability in Bicep

You can reuse code using:
- Modules 📦
- Parameters 🔧
- Variables 📊

---

## 📦 Example: Adding a Resource in Bicep

```bicep
resource storageAccount 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: storageName
  location: location
  sku: {
    name: 'Standard_LRS'
  }
  kind: 'StorageV2'
}
``` id="bicep3"

---

## 🧠 Best Practices for Bicep

- Use modules for large deployments
- Use parameters instead of hardcoding values
- Use descriptive naming conventions
- Store in Git for version control
- Validate before deployment

---

# 🔗 Relationship Between ARM and Bicep

```
Bicep File
   ↓ (compiles)
ARM Template (JSON)
   ↓
Azure Resource Deployment
``` id="flow1"

---

# 🚀 Deployment Lifecycle

## 1️⃣ Define Infrastructure
- ARM template or Bicep file

## 2️⃣ Validate
- Check syntax and configuration

## 3️⃣ Deploy
- Use Azure CLI, PowerShell, or portal

## 4️⃣ Monitor
- Track resource status and performance

---

# 🎯 Summary of Module 3

| Lesson | Focus |
|---|---|
| Deploy Resources (ARM/Bicep) | Infrastructure as Code deployment |
| Modify ARM Template | Update JSON-based deployments |
| Modify Bicep File | Improve and update modern IaC scripts |

---

# 📝 Final Summary

Module 3 focuses on administering Azure resources using **Infrastructure as Code (IaC)**. It teaches how to deploy and manage infrastructure using ARM templates and Bicep files, and how to modify them to maintain scalable, consistent, and automated cloud environments.
```
