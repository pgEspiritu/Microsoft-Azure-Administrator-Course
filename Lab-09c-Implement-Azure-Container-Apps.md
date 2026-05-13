# 🌐 Lab 09c - Implement Azure Container Apps

---

# 📘 Lab Introduction

In this lab, you learn how to implement and deploy Azure Container Apps.

This lab requires an Azure subscription. Your subscription type may affect the availability of features in this lab. You may change the region, but the steps are written using East US.

⏱️ Estimated timing: 15 minutes

---

# 🧩 Lab Scenario

Your organization has a web application that runs on a virtual machine in your on-premises data center. The organization wants to move all applications to the cloud but doesn't want to have a large number of servers to manage. You decide to evaluate Azure Container Apps.

---

# 🏗️ Architecture Diagram

Diagram of the tasks.

---

# 🎯 Job skills

Task 1: Create and configure an Azure Container App and environment.  
Task 2: Test and verify deployment of the Azure Container App.

---

# 🚀 Task 1: Create and configure an Azure Container App and environment

Azure Container Apps take the concept of a managed Kubernetes cluster a step further and manages the cluster environment as well as provides other managed services on top of the cluster. Unlike an Azure Kubernetes cluster, where you must still manage the cluster, an Azure Container Apps instance removes some of the complexity to setting up a Kubernetes cluster.

---

## 🪜 Step-by-step instructions

### 🔹 Step 1: Sign in to the Azure portal

Sign in to the Azure portal - https://portal.azure.com.

---

### 🔹 Step 2: Open Container Apps

In the Azure portal, search for and select **Container Apps** and then, on the Container Apps blade, click **+ Create**.

---

### 🔹 Step 3: Select Container App

Select **Container App**, from drop-down menu. Notice the other choices.

---

### 🔹 Step 4: Configure Basics tab

On the **Basics** tab, use the following settings (leave others with their default values):

| Setting | Value |
|---|---|
| Subscription | Select your Azure subscription |
| Resource group | az104-rg9 |
| Container app name | my-app |
| Region | East US |
| Container Apps Environment | Select Create new > Set Environment name to my-environment > Create |

---

### 🔹 Step 5: Create Container Apps Environment

Select **Create new** under Container Apps Environment.

Set:

| Setting | Value |
|---|---|
| Environment name | my-environment |

Select **Create**.

---

### 🔹 Step 6: Configure Container tab

Click **Next: Container tab** and ensure that **Use quickstart image** is checked. You may need to scroll up to view this setting.

Ensure **Quickstart image** is set to **Simple hello world container**. Notice the other choices.

---

### 🔹 Step 7: Review and create

Select **Review and create** and then **Create**.

---

### 🔹 Step 8: Wait for deployment

Note: Wait for the container app to deploy. This will take a couple of minutes.

---

# 🧪 Task 2: Test and verify deployment of the Azure Container App

By default, the Azure container app that you create will accept traffic on port 80 using the sample Hello World application.

Azure Container Apps will provide a DNS name for the application. Copy and navigate to this URL to ensure that the application is up and running.

---

## 🪜 Step-by-step instructions

### 🔹 Step 1: Open deployed resource

Select **Go to resource** to view your new container app.

---

### 🔹 Step 2: Open Application URL

Select the link next to **Application URL** to view your application.

---

### 🔹 Step 3: Verify application

Verify you receive the message:

**Your Azure Container Apps app is live**

---

# 🧹 Cleanup your resources

If you are working with your own subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized.

The easiest way to delete the lab resources is to delete the lab resource group.

---

## 🔹 Delete using Azure Portal

In the Azure portal:

1. Select the resource group  
2. Select Delete the resource group  
3. Enter resource group name  
4. Click Delete  

---

## 🔹 Delete using Azure PowerShell

```powershell
Remove-AzResourceGroup -Name resourceGroupName
```

---

## 🔹 Delete using Azure CLI

```bash
az group delete --name resourceGroupName
```

---

# 🤖 Extend your learning with Copilot

Copilot can assist you in learning how to use the Azure scripting tools. Copilot can also assist in areas not covered in the lab or where you need more information.

Open an Edge browser and choose Copilot (top right) or navigate to https://copilot.microsoft.com.

---

## 💡 Try these prompts

Summarize the steps to create and configure an Azure Container App.  
Compare and contrast Azure Container Apps to Azure Kubernetes Service.

---

# 📚 Learn more with self-paced training

## 🚀 Configure a container app in Azure Container Apps

Learn the features and capabilities of Azure Container Apps, and then focus on how to create, configure, scale, and manage container apps using Azure Container Apps.

---

## 🚀 Implement Azure Container Apps

Learn how Azure Container Apps can help you deploy and manage microservices and containerized apps on a serverless platform.

---

# 🧠 Key takeaways

Congratulations on completing the lab. Here are the main takeaways for this lab:

- Azure Container Apps (ACA) is a serverless platform that allows you to maintain less infrastructure and save costs while running containerized applications.
- Container Apps provides server configuration, container orchestration, and deployment details.
- Workloads on ACA are usually long-running processes like a Web App.

---

# 🎉 Congratulations

You have successfully completed this lab. Click End to mark the lab as Complete.
```
