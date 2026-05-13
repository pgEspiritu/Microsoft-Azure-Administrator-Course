# 🛡️ Lab 10 - Implement Data Protection

---

# 📘 Lab introduction

In this lab, you learn about backup and recovery of Azure virtual machines. You learn to create a Recovery Services vault and a backup policy for Azure virtual machines. You learn about disaster recovery with Azure Site Recovery.

This lab requires an Azure subscription. Your subscription type may affect the availability of features in this lab. You may change the regions, but the steps are written using East US and West US.

Estimated timing: 50 minutes

---

# 🧩 Lab scenario

Your organization is evaluating how to backup and restore Azure virtual machines from accidental or malicious data loss. Additionally, the organization wants to explore using Azure Site Recovery for disaster recovery scenarios.

---

# 🎯 Job skills

Task 1: Use a template to provision an infrastructure.  
Task 2: Create and configure a Recovery Services vault.  
Task 3: Configure Azure virtual machine-level backup.  
Task 4: Monitor Azure Backup.  
Task 5: Enable virtual machine replication.

---

# 🏗️ Architecture diagram

Diagram of the architecture tasks.

---

# 🚀 Task 1: Use a template to provision an infrastructure

In this task, you will use a template to deploy a virtual machine. The virtual machine will be used to test different backup scenarios.

Download the F:\Allfiles\Labs\Lab10\ lab files.

Sign in to the Azure portal - https://portal.azure.com.

Search for and select Deploy a custom template.

On the custom deployment page, select Build your own template in the editor.

![Lab-13.1](images/Lab-13.1.png)

On the edit template page, select Load file.

![Lab-13.2](images/Lab-13.2.png)

Locate and select the F:\Allfiles\Labs\Lab10\az104-10-vms-edge-template.json file and select Open.

![Lab-13.3](images/Lab-13.3.png)

Note: Take a moment to review the template. We are deploying a virtual network and virtual machine so we can demonstrate backup and recovery.

![Lab-13.4](images/Lab-13.4.png)

Save your changes.

Select Edit parameters and then Load file.

![Lab-13.5](images/Lab-13.5.png)

Load and select the F:\Allfiles\Labs\Lab10\az104-10-vms-edge-parameters.json file.

![Lab-13.6](images/Lab-13.6.png)
![Lab-13.7](images/Lab-13.7.png)

Save your changes.

![Lab-13.8](images/Lab-13.8.png)

Use the following information to complete the custom deployment fields, leaving all other fields with their default values:

| Setting | Value |
|---|---|
| Subscription | Your Azure subscription |
| Resource group | az104-rg-region1 (If necessary, select Create new) |
| Region | East US |
| Username | localadmin |
| Password | Provide a complex password |

![Lab-13.9](images/Lab-13.9.png)

Select Review + Create, then select Create.

![Lab-13.10](images/Lab-13.10.png)

Note: Wait for the template to deploy, then select Go to resource. You should have one virtual machine in one virtual network.

---

# 🛡️ Task 2: Create and configure a Recovery Services vault

In this task, you will create a Recovery Services vault. A Recovery Services vault provides storage for the virtual machine data.

In the Azure portal, search for and select Recovery Services vaults and, on the Recovery Services vaults blade, click + Create.

![Lab-13.11](images/Lab-13.11.png)

On the Create Recovery Services vault blade, specify the following settings:

| Settings | Value |
|---|---|
| Subscription | the name of your Azure subscription |
| Resource group | az104-rg-region1 |
| Vault Name | az104-rsv-region1 |
| Region | East US |

![Lab-13.12](images/Lab-13.12.png)

Note: Make sure that you specify the same region into which you deployed virtual machines in the previous task.

Screenshot of the recovery services vault.

Click Review + Create, ensure that the validation passes and then click Create.

![Lab-13.13](images/Lab-13.13.png)

Note: Wait for the deployment to complete. The deployment should take a couple of minutes.

When the deployment is completed, click Go to Resource.

In the Settings section, click Properties.

Select the Update link under Backup Configuration label.

![Lab-13.14](images/Lab-13.14.png)

On the Backup Configuration blade, review the choices for Storage replication type. Leave the default setting of Geo-redundant in place and close the blade.

![Lab-13.15](images/Lab-13.15.png)

Note: This setting can be configured only if there are no existing backup items.

Did you know? The Cross Region Restore option allows you to restore data in a secondary, Azure paired region.

Select the Update link under Security Settings > Soft Delete Settings label.

![Lab-13.16](images/Lab-13.16.png)

On the Soft delete Settings blade, verify that the Soft delete retention period is 14 days and close the blade.

![Lab-13.17](images/Lab-13.17.png)

Did you know? Azure has two types of vaults: Recovery Services vaults and Backup vaults. The main difference is the datasources that can be backed up. Learn more about the differences.

---

# 💾 Task 3: Configure Azure virtual machine-level backup

Note: Before you start this task, make sure that the deployment you initiated in the first task of this lab has successfully completed.

On the Recovery Services vault blade, click Overview, then click + Backup.

![Lab-13.18](images/Lab-13.18.png)

On the Backup Goal blade, specify the following settings:

| Settings | Value |
|---|---|
| Where is your workload running? | Azure (notice your other options) |

![Lab-13.19](images/Lab-13.19.png)

| What do you want to backup? | Virtual machine (notice your other options) |

![Lab-13.20](images/Lab-13.20.png)

Select Backup.

![Lab-13.21](images/Lab-13.21.png)

Notice there a two Policy sub types: Enhanced and Standard. Review the choices and select Standard.

In Backup policy, select Create a new policy.

![Lab-13.22](images/Lab-13.22.png)

Define a new backup policy with the following settings (leave others with their default values):

| Setting | Value |
|---|---|
| Policy name | az104-backup |
| Frequency | Daily |
| Time | 12:00 AM |
| Timezone | the name of your local time zone |
| Retain instant recovery snapshot(s) for | 2 Days(s) |

![Lab-13.23](images/Lab-13.23.png)

Click OK to create the policy and then, in the Virtual Machines section, select Add (scroll down).

![Lab-13.24](images/Lab-13.24.png)

On the Select virtual machines blade, select az-104-10-vm0, click OK, and then back on the Backup blade, click Enable backup.

![Lab-13.25](images/Lab-13.25.png)
![Lab-13.26](images/Lab-13.26.png)

Note: Wait for the backup to be enabled. This should take approximately 2 minutes.

After the deployment, select Go to resource.

In the Protected items section, click Backup items, and then click the Azure virtual machine entry.

![Lab-13.27](images/Lab-13.27.png)

Select the View details link for az104-10-vm0, and review the values of the Backup Pre-Check and Last Backup Status entries.

![Lab-13.28](images/Lab-13.28.png)
![Lab-13.29](images/Lab-13.29.png)

Note: Notice the backup is pending.

Select Backup now, accept the default value in the Retain Backup Till drop-down list, and click OK.

![Lab-13.30](images/Lab-13.30.png)
![Lab-13.31](images/Lab-13.31.png)

Note: Do not wait for the backup to complete but instead proceed to the next task.

---

# 📊 Task 4: Monitor Azure Backup

From the Azure portal, search for and select Storage accounts.

On the Storage accounts page, select Create.

![Lab-13.32](images/Lab-13.32.png)

Use the following information to define the storage account, then select Review + create.

| Settings | Value |
|---|---|
| Subscription | Your subscription |
| Resource group | az104-rg-region1 |
| Storage account name | Provide a globally unique name |
| Region | East US |

![Lab-13.33](images/Lab-13.33.png)

Select Create.

![Lab-13.34](images/Lab-13.34.png)

Note: Wait for the deployment to complete. It should take about a minute.

Search and select your Recovery Services vault.

In the Monitoring blade, select Diagnostic Settings and then select Add diagnostic setting.

![Lab-13.35](images/Lab-13.35.png)

Name the setting Logs and Metrics to storage.

Place a checkmark next to the following log and metric categories:

Azure Backup Reporting Data  
Addon Azure Backup Job Data  
Addon Azure Backup Alert Data  
Azure Site Recovery Jobs  
Azure Site Recovery Events  

![Lab-13.36](images/Lab-13.36.png)
![Lab-13.37](images/Lab-13.37.png)

In the Destination details, place a checkmark next to Archive to a storage account.

In the Storage account drop-down field, select the storage account that you deployed earlier in this task.

![Lab-13.38](images/Lab-13.38.png)

Select Save.

Return to your Recovery Services vault, in the Monitoring blade select Backup jobs.

Locate the backup operation for the az104-10-vm0 virtual machine.

![Lab-13.39](images/Lab-13.39.png)

View details (scroll to the right for the link) of the backup job.

![Lab-13.40](images/Lab-13.40.png)

![Lab-13.41](images/Lab-13.41.png)

---

# 🔁 Task 5: Enable virtual machine replication

In the Azure portal, search for and select Recovery Services vaults and, on the Recovery Services vaults blade, click + Create.

![Lab-13.42](images/Lab-13.42.png)

On the Create Recovery Services vault blade, specify the following settings:

| Settings | Value |
|---|---|
| Subscription | the name of your Azure subscription |
| Resource group | az104-rg-region2 (If necessary, select Create new) |
| Vault Name | az104-rsv-region2 |
| Region | West US |

![Lab-13.43](images/Lab-13.43.png)

Note: Make sure that you specify a different region than the virtual machine.

Click Review + Create, ensure that the validation passes and then click Create.

![Lab-13.44](images/Lab-13.44.png)

Note: Wait for the deployment to complete. The deployment should take a couple of minutes.

Search for and select the az104-10-vm0 virtual machine.

In the Backup + Disaster recovery blade, select Disaster recovery.

On the Basics tab, notice the Target region.

![Lab-13.45](images/Lab-13.45.png)

Select Next: Advanced settings. Resource selections have been made for you.

![Lab-13.46](images/Lab-13.46.png)

Scroll down and Create the automation account.

![Lab-13.47](images/Lab-13.47.png)

Note: It is important the settings be populated, or the validation will fail.

Select Review + Start replication and then Start replication.

![Lab-13.48](images/Lab-13.48.png)

Note: Enabling replication will take a 10-15 minutes. Watch the notification messages in the upper right of the portal. While you wait, consider reviewing the self-paced training links at the end of this page.

Once the replication is complete, search for and locate your Recovery Services Vault, az104-rsv-region2. You may need to Refresh the page.

In the Protected items section, select Replicated items.

Check that the virtual machine is showing as healthy for the replication health. Note that the status will show the synchronization (starting at 0%) status and ultimately show Protected after the initial synchronization completes.

![Lab-13.49](images/Lab-13.49.png)
![Lab-13.50](images/Lab-13.50.png)

Select the virtual machine to view more details.

Did you know? It is a good practice to test the failover of a protected VM.

---

# 🧹 Cleanup your resources

If you are working with your own subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized. The easiest way to delete the lab resources is to delete the lab resource group.

In the Azure portal, select the resource group, select Delete the resource group, Enter resource group name, and then click Delete.

Using Azure PowerShell, Remove-AzResourceGroup -Name resourceGroupName.

Using the CLI, az group delete --name resourceGroupName.

Note: To delete an Azure Recovery Services vault, you must first remove all dependencies like protected items, backup servers, and storage accounts, disable security features like soft delete, and then delete the vault itself. An example PowerShell script is available.

---

# 🤖 Extend your learning with Copilot

Copilot can assist you in learning how to use the Azure scripting tools. Copilot can also assist in areas not covered in the lab or where you need more information. Open an Edge browser and choose Copilot (top right) or navigate to copilot.microsoft.com.

Take a few minutes to try these prompts:

What products does Azure Backup support?  
Summarize the steps for backing up and restoring an Azure virtual machine with Azure Backup.  
How can I use Azure PowerShell or the CLI to check the status of an Azure Backup job.  
Provide at least five best practices for configuring Azure virtual machine backups.  

---

# 📚 Learn more with self-paced training

Introduction to Azure Backup. Describe how the features of Azure Backup work to provide backup solutions for your needs.  
Protect your virtual machines by using Azure Backup. Use Azure Backup to help protect on-premises servers, virtual machines, SQL Server, Azure file shares, and other workloads.  

---

# 🧠 Key takeaways

- Azure Backup service provides simple, secure, and cost-effective solutions to back up and recover your data.  
- Azure Backup can protect on-premises and cloud resources including virtual machines and file shares.  
- Azure Backup policies configure the frequency of backups and the retention period for recovery points.  
- Azure Site Recovery is a disaster recovery solution that provides protection for your virtual machines and applications.  
- Azure Site Recovery replicates your workloads to a secondary site, and in the event of an outage or disaster, you can failover to the secondary site and resume operations with minimal downtime.  
- A Recovery Services vault stores your backup data and minimizes management overhead.  

---

# 🎉 Congratulations

You have successfully completed this lab. Click End to mark the lab as Complete.
