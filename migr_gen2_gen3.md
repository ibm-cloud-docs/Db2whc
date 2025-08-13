---

copyright:
  years: 2024, 2025
lastupdated: "2025-03-25"

keywords:

subcollection: Db2whc

---

<!-- Attribute definitions --> 
{:external: target="_blank" .external}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:video: .video}

# Upgrading your system to Db2 Warehouse SaaS Next Generation
{: #migr_gen2_gen3}

## IBM Driven Upgrade
{: #ibm_driven_upgrade}

Outdated instance versions may be automatically upgraded to the next generation (Gen 3) of {{site.data.keyword.dashdblong}} during the scheduled maintenance window. This implicit upgrade ensures all environments are moved to Gen 3 and benefit from the latest enhancements with minimal manual intervention.

## Customer Initiated Upgrade via Self-Service Upgrade Tool
{: #customer_initiated_upgrade}

In order to upgrade existing systems to the next generation (Gen 3) of {{site.data.keyword.dashdblong}}, a self-service upgrade tool has been provided and {{site.data.keyword.dashdbshort_notm}} users on {{site.data.keyword.Bluemix_notm}} Cloud will be invited individually to start using the tool. Upgrading to the next generation of {{site.data.keyword.dashdbshort_notm}}, unlocks opportunities to use {{site.data.keyword.Bluemix_notm}} Object Storage (COS) to store database data while increasing performance of your system and saving on storage costs. It also unlocks the use of open data formats such as DATALAKE tables, allowing for seamless access to other data within your enterprise for integrated workloads.

### Accessing the Upgrade Tool
{: #access_migr_tool}

1. Log in to IBM Cloud and navigate to the {{site.data.keyword.dashdbshort_notm}} instance you wish to upgrade by going to Resource List > Databases > Service Details > Manage.
2. Locate the “System upgrade available: Upgrade to the newest version of {{site.data.keyword.dashdbshort_notm}}”, then click Learn More to begin the upgrade process.


### Step 1: Create a New Instance
{: #migr_create_instance}

A duplicate of the current (Gen 2) IBM Cloud Classic {{site.data.keyword.dashdbshort_notm}} instance will be provisioned on the new Gen 3 infrastructure, with an estimated provisioning time displayed. All instance specifications, including compute and storage resources, will be seamlessly transitioned from the IBM Cloud Classic infrastructure to the Gen 3 environment. Once provisioning is complete, the new instance name will appear, and you can launch into the instance. At this stage, the instance will not contain any data until Step 2 is completed.

### Step 2: Restore and Test Your New System (optional step)
{: #migr_restore}

You can choose an existing backup or create a new backup from the prior instance to restore onto the newly provisioned instance, bringing in all data. During the restore process, the estimated restore time will be displayed. At this time, you can point your applications to the new server instance to verify that your existing applications and workloads are functioning as expected. This step allows you to perform validation checks before triggering the final upgrade (Step 3). All identity and access management configurations will also be transferred. This step can be repeated as needed to sync data from the old instance to the new one.

### Step 3: Final Upgrade
{: #migr_upgrade}

This step completes the upgrade process. A full backup of the database from the prior system will be taken and restored onto the new Gen 3 system. Both the hostname from the previous system and the new hostname for the Gen 3 instance will remain active, ensuring that applications, including those inserting and querying data, are routed to the upgraded Gen 3 environment. However, any private connections will need to be explicitly updated to point to the new instance, as described in the FAQ section.
The prior system will still exist but will no longer be accessible for connections, effectively rendering it offline. Billing for both systems will continue unless the old system is deleted. At this stage, billing for the new system will begin.

### Step 4: Delete Your Old System
{: #migr_delete}

Once the final upgrade in Step 3 is completed and the new instance is in use, you can delete the old {{site.data.keyword.dashdbshort_notm}} instance. To do this, go to the actions dropdown on the manage page. Deleting the old system ensures that you avoid unnecessary charges and maintenance of outdated resources.

### Step 5: Update Your Software
{: #migr_software}

After the previous self-service steps were performed, your system will be at the same level of software as your previous system. The final step is to update the software and that can be achieved by either opening an IBM Support Ticket or clicking the Update Now button in your console.

This step is crucial as it will unlock the new Cloud Object Storage native capabilities in Db2 Warehouse. You can save money and improve query performance by creating tables in object storage tablespaces. [Review the requirements and documentation](https://www.ibm.com/docs/en/db2w-as-a-service?topic=native-cloud-object-storage-support) for using object storage tables.

## Post-Upgrade Steps for Both Upgrade Paths
{: #post_upgrade_steps}

### Move Data from Block to Cloud Object Storage
{: #migr_move}

To start saving on storage costs, you will need to move eligble data from block storage to cloud object storage and then shrink the freed block storage. The limitations on what type of tables are eligible can be found within [this documentation](https://www.ibm.com/docs/en/db2w-as-a-service?topic=support-restrictions-limitations).
There are two ways to move tables:
- Via the service console, utilizing the Table Explorer, where a single table at a time can be moved to the pre-created cloud object storage tablespace.
- Via a command line tool, which can automate bulk table moves and more. Details on how to install and use the tool can be found [here](https://github.com/IBM/db2whmigratetocos).

### Shrink Block Storage
{: #migr_shrink}

After tables have been moved to cloud object storage, the block storage will need to be shrunk. The shrink operation can be performed as many times as required, however keep in mind that it is an offline operation and requires downtime. The shrink operation can be initiated via the service console as shown [here](https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-scaling).

For information about posting questions on a forum or opening a support ticket, see [Help & support](/docs/Db2whc?topic=Db2whc-help_support).

