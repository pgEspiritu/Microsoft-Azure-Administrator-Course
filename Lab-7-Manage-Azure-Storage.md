# 📘 Lab 07 - Manage Azure Storage

---

# 🧪 Lab Introduction

In this lab you learn to create storage accounts for Azure blobs and Azure files. You learn to configure and secure blob containers. You also learn to use Storage Browser to configure and secure Azure file shares.

> ⚠️ This lab requires an Azure subscription. Your subscription type may affect the availability of features in this lab. You may change the region, but the steps are written using East US.

⏱️ Estimated timing: 50 minutes

---

# 🎯 Lab Scenario

Your organization is currently storing data in on-premises data stores. Most of these files are not accessed frequently. You would like to minimize the cost of storage by placing infrequently accessed files in lower-priced storage tiers.

You also plan to explore different protection mechanisms that Azure Storage offers, including:

- 🔒 Network access
- 🔑 Authentication
- 🛡️ Authorization
- ♻️ Replication

Finally, you want to determine to what extent Azure Files is suitable for hosting your on-premises file shares.

---

# 🏗️ Architecture Diagram

📌 Diagram of the tasks.

---

# 💼 Job Skills

- ✅ Task 1: Create and configure a storage account.
- ✅ Task 2: Create and configure secure blob storage.
- ✅ Task 3: Create and configure secure Azure file storage.

---

# 🛠️ Task 1: Create and Configure a Storage Account

In this task, you will create and configure a storage account. The storage account will use geo-redundant storage and will not have public access.

---

## 🔹 Create the Storage Account

1. Sign in to the Azure portal:
   - 🌐 https://portal.azure.com

2. Search for and select **Storage accounts**, and then click **+ Create**.

3. On the **Basics** tab of the **Create a storage account** blade, specify the following settings (leave others with their default values):

| Setting | Value |
|---|---|
| Subscription | The name of your Azure subscription |
| Resource group | `az104-rg7-lod61663697` |
| Storage account name | Any globally unique name between 3 and 24 in length consisting of letters and digits |
| Region | `(US) East US` |
| Performance | `Standard (notice the Premium option)` |
| Redundancy | `Geo-redundant storage` |
| Make read access to data available in the event of regional unavailability | ✅ Check the box |

> 💡 Did you know?  
> You should use the Standard performance tier for most applications. Use the Premium performance tier for enterprise or high-performance applications.

---

## 🔹 Review Additional Configuration Tabs

### ⚙️ Advanced Tab

1. On the **Advanced** tab, use the informational icons to learn more about the choices.
2. Take the defaults.

---

### 🌐 Networking Tab

1. On the **Networking** tab, in the **Public network access** section, select:
   - ❌ Disable

This will restrict inbound access while allowing outbound access.

---

### 🛡️ Data Protection Tab

1. Review the **Data protection** tab.
2. Notice:
   - 7 days is the default soft delete retention policy.
3. Note:
   - You can enable versioning for blobs.
4. Accept the defaults.

---

### 🔐 Encryption Tab

1. Review the **Encryption** tab.
2. Notice the additional security options.
3. Accept the defaults.

---

## 🔹 Deploy the Storage Account

1. Select **Review + create**.
2. Wait for the validation process to complete.
3. Click **Create**.

Once the storage account is deployed:

4. Select **Go to resource**.

---

## 🔹 Review Storage Account Configuration

1. Review the **Overview** blade and the additional configurations that can be changed.

These are global settings for the storage account.

2. Notice the storage account can be used for:
   - 📦 Blob containers
   - 📁 File shares
   - 📬 Queues
   - 🗃️ Tables

---

## 🔹 Configure Public Network Access

1. In the **Security + networking** blade, select **Networking**.
2. Notice:
   - Public network access is disabled.

3. Select **Manage** and change the **Public network access** setting to:
   - ✅ Enabled

4. Change the **Public network access scope** to:
   - ✅ Enable from selected networks

5. In the **IPv4 Addresses** section:
   - Select **Add your client IPv4 address**

6. Save your changes.

---

## 🔹 Review Redundancy Configuration

1. In the **Data management** blade, select **Redundancy**.
2. Notice the information about your:
   - 🌎 Primary data center location
   - 🌎 Secondary data center location

---

## 🔹 Configure Lifecycle Management

1. In the **Data management** blade, select **Lifecycle management**.
2. Select **Add a rule**.

3. Name the rule:
   - `Movetocool`

4. Notice your options for limiting the scope of the rule.

5. Click **Next**.

---

## 🔹 Configure Lifecycle Rule Conditions

1. On the **Add rule** page, configure the following condition:

| Condition | Value |
|---|---|
| If base blobs were last modified more than | `30 days ago` |
| Action | `Move to cool storage` |

2. Notice your other choices.

3. Notice you can configure other conditions.

4. Select **Add** when you are done exploring.

📸 Screenshot move to cool rule conditions.

---

# 🛠️ Task 2: Create and Configure Secure Blob Storage

In this task, you will create a blob container and upload an image. Blob containers are directory-like structures that store unstructured data.

---

# 📦 Create a Blob Container and a Time-Based Retention Policy

1. Continue in the Azure portal, working with your storage account.

2. In the **Data storage** blade, select **Containers**.

3. Click **+ Add container** and create a container with the following settings:

| Setting | Value |
|---|---|
| Name | `data` |
| Public access level | Notice the access level is set to private |

📸 Screenshot of create a container.

---

## 🔹 Configure Immutable Blob Storage

1. On your container, scroll to the ellipsis (**…**) on the far right.
2. Select **Access policy**.

3. In the **Immutable blob storage** area, select **Add policy**.

4. Configure the following settings:

| Setting | Value |
|---|---|
| Policy type | `Time-based retention` |
| Set retention period for | `180 days` |

5. Select **Save**.

---

# 📤 Manage Blob Uploads

---

## 🔹 Upload a Blob

1. Return to the containers page.
2. Select your `data` container and then click **Upload**.

3. On the **Upload blob** blade, expand the **Advanced** section.

> 📌 Note: Locate a file to upload. This can be any type of file, but a small file is best. A sample file can be downloaded from the AllFiles directory.

4. Configure the following settings:

| Setting | Value |
|---|---|
| Browse for files | Add the file you have selected to upload |
| Blob type | `Block blob` |
| Block size | `4 MiB` |
| Access tier | `Hot (notice the other options)` |
| Upload to folder | `securitytest` |
| Encryption scope | `Use existing default container scope` |

5. Click **Upload**.

---

## 🔹 Verify the Blob Upload

1. Confirm you have:
   - ✅ A new folder
   - ✅ Your file uploaded

2. Select your uploaded file and review the ellipsis (**…**) options including:
   - ⬇️ Download
   - 🗑️ Delete
   - 🔄 Change tier
   - 🔒 Acquire lease

---

## 🔹 Test Public Access Restrictions

1. Copy the file URL:
   - Settings → Properties blade

2. Paste the URL into a new **InPrivate** browsing window.

3. You should be presented with an XML-formatted message stating:
   - ❌ `ResourceNotFound`
   - OR
   - ❌ `PublicAccessNotPermitted`

> 💡 Note: This is expected, since the container you created has the public access level set to Private (no anonymous access).

---

# 🔐 Configure Limited Access to the Blob Storage

1. Browse back to the file that you uploaded.

2. Select the ellipsis (**…**) to the far right, then select:
   - **Generate SAS**

3. Specify the following settings (leave others with their default values):

| Setting | Value |
|---|---|
| Signing key | `Key 1` |
| Permissions | `Read (notice your other choices)` |
| Start date | Yesterday's date |
| Start time | Current time |
| Expiry date | Tomorrow's date |
| Expiry time | Current time |
| Allowed IP addresses | Leave blank |

4. Click **Generate SAS token and URL**.

5. Copy the **Blob SAS URL** entry to the clipboard.

6. Open another **InPrivate** browser window and navigate to the Blob SAS URL you copied in the previous step.

> 💡 Note: You should be able to view the content of the file.

---

# 🛠️ Task 3: Create and Configure an Azure File Storage

In this task, you will create and configure Azure File shares. You will use Storage Browser to manage the file share.

---

# 📁 Create the File Share and Upload a File

1. In the Azure portal, navigate back to your storage account.

2. In the **Data storage** blade, click **File shares**.

3. Click **+ File share** and on the **Basics** tab give the file share a name:
   - `share1`

4. Notice the **Access tier** options.
5. Keep the default:
   - `Transaction optimized`

---

## 🔹 Configure Backup Settings

1. Move to the **Backup** tab.
2. Ensure:
   - ❌ Enable backup is NOT checked

> 💡 Note: We are disabling backup to simplify the lab configuration.

3. Click **Review + create**, and then **Create**.

4. Wait for the file share to deploy.

📸 Screenshot of the create file share page.

---

# 🖥️ Explore Storage Browser and Upload a File

1. Return to your storage account and select **Storage browser**.

> 💡 The Azure Storage Browser is a portal tool that lets you quickly view all the storage services under your account.

2. Select **File shares** and verify your `share1` directory is present.

3. Select your `share1` directory and notice you can:
   - ➕ Add directory

This lets you create a folder structure.

---

## 🔹 Upload a File to the File Share

1. Select **Upload**.
2. Browse to a file of your choice.
3. Click **Upload**.

> 📌 Note: You can view file shares and manage those shares in the Storage Browser. There are currently no restrictions.

---

# 🌐 Restrict Network Access to the Storage Account

---

## 🔹 Create a Virtual Network

1. In the portal, search for and select **Virtual networks**.

2. Select **+ Create**.

3. Select your resource group and give the virtual network a name:
   - `vnet1`

4. Take the defaults for other parameters.

5. Select **Review + create**, and then **Create**.

6. Wait for the virtual network to deploy, and then select:
   - **Go to resource**

---

## 🔹 Configure Service Endpoints

1. In the **Settings** section, select the **Service endpoints** blade.

2. Select **Add**.

3. Configure the following settings:

| Setting | Value |
|---|---|
| Service | `Microsoft.Storage` |
| Subnets | Check the `Default` subnet |

4. Click **Add** to save your changes.

---

## 🔹 Restrict Storage Account Access to the Virtual Network

1. Return to your storage account.

2. In the **Security + networking** blade, select **Networking**.

3. Under **Public network access** select:
   - **Manage**

4. Select:
   - **Add a virtual network**

5. Then select:
   - **Add existing network**

6. Select:
   - `vnet1`
   - `default subnet`

7. Select **Add**.

---

## 🔹 Remove Client IP Access

1. In the **IPv4 Addresses** section:
   - Delete your machine IP address.

> 💡 Allowed traffic should only come from the virtual network.

2. Be sure to **Save** your changes.

> 📌 Note: The storage account should now only be accessed from the virtual network you just created.

---

## 🔹 Verify Restricted Access

1. Select the **Storage browser** and refresh the page.

2. Navigate to your file share or blob content.

> 💡 Note: You should receive a message:
> ❌ Not authorized to perform this operation.

You are not connecting from the virtual network.

It may take a couple of minutes for this to take effect.

You may still be able to view the file share, but not the files or blobs in the storage account.

📸 Screenshot unauthorized access.

---

# 🧹 Cleanup Your Resources

If you are working with your own subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized. The easiest way to delete the lab resources is to delete the lab resource group.

---

## 🔹 Delete Using Azure Portal

1. In the Azure portal, select the resource group.
2. Select:
   - 🗑️ Delete the resource group
3. Enter the resource group name.
4. Click:
   - Delete

---

## 🔹 Delete Using Azure PowerShell

```powershell
Remove-AzResourceGroup -Name resourceGroupName
```

---

## 🔹 Delete Using Azure CLI

```bash
az group delete --name resourceGroupName
```

---

# 🤖 Extend Your Learning with Copilot

Copilot can assist you in learning how to use the Azure scripting tools.

Open Microsoft Copilot:
- 🌐 https://copilot.microsoft.com

Try these prompts:

- 💬 Provide an Azure PowerShell script to create a storage account with a blob container.
- 💬 Provide a checklist I can use to ensure my Azure storage account is secure.
- 💬 Create a table to compare Azure storage redundancy models.

---

# 📚 Learn More with Self-Paced Training

## 📘 Guided Project - Azure Files and Azure Blobs

Practice storing business data securely by using Azure Blob Storage and Azure Files.

---

## 📘 Create an Azure Storage Account

Create an Azure Storage account with the correct options for your business needs.

---

## 📘 Manage the Azure Blob Storage Lifecycle

Learn how to manage data availability throughout the Azure Blob storage lifecycle.

---

# 🔑 Key Takeaways

🎉 Congratulations on completing the lab.

Here are the main takeaways for this lab:

- ✅ An Azure storage account contains all your Azure Storage data objects: blobs, files, queues, and tables.
- ✅ The storage account provides a unique namespace for your Azure Storage data that is accessible from anywhere in the world over HTTP or HTTPS.
- ✅ Azure storage provides several redundancy models including:
  - Locally redundant storage (LRS)
  - Zone-redundant storage (ZRS)
  - Geo-redundant storage (GRS)
- ✅ Azure blob storage allows you to store large amounts of unstructured data on Microsoft's data storage platform.
- ✅ Blob stands for Binary Large Object, which includes objects such as images and multimedia files.
- ✅ Azure file Storage provides shared storage for structured data.
- ✅ The data can be organized in folders.
- ✅ Immutable storage provides the capability to store data in a write once, read many (WORM) state.
- ✅ Immutable storage policies can be time-based or legal-hold.

---

# 🎉 Congratulations

You have successfully completed this lab.

✅ Click **End** to mark the lab as Complete.
