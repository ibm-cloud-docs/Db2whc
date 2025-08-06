---

copyright:
  years: 2014, 2025
lastupdated: "2025-03-11"

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

# Disaster recovery
{: #dr}

Disaster recovery (DR) backups for {{site.data.keyword.dashdblong}} are enabled by default.

If a disaster event occurs at the data center where your {{site.data.keyword.dashdbshort_notm}} instance is deployed, IBM service operators will work with you to stand up a new data warehouse in a different data center, by using the most recent disaster recovery backup.

For more information about DR and replication on Db2 Warehouse SaaS, see [Replication](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.idrca.doc/overview/ovu-db2woc.html).
{: shortdesc}

## IBM Cloud
{: #ibm_cloud_br}

### Current Generation

When deployed on IBM Cloud, the daily snapshot backup described in https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-br is also used for disaster recovery purposes. This DR backup is encrypted and stored in IBM Cloud Object Storage (COS) across 3 availability zones (AZs) in each region. Regional DR backups allow you to restore your instance to another zone in the same region if needed. The RPO for DR backups on IBM Cloud is 24 hours. The RTO if a disaster occurs will be best effort. The actual time required to complete a DR restore is dependent on many variables, including but not limited to:

 * the number of vCPUs in the instance
 * the amount of data stored in Native Cloud Object Storage (https://www.ibm.com/docs/en/db2w-as-a-service?topic=native-cloud-object-storage-support)

With the current generation of plans, the console allows you to copy backups to a separate region, and restore a backup to an instance in another region if needed. The region must be a supported region for Db2 Warehouse SaaS on IBM Cloud. You are charged for the storage used for these copies, and for data transfer charges.

### Previous Generation

For instances deployed on IBM Cloud, disaster recovery (DR) backups supplement daily snapshot backups. They are used exclusively for system recovery purposes by IBM service operators if there is a disaster or system loss.

A full backup of the database is taken once a week for disaster recovery. This DR backup is encrypted and stored in {{site.data.keyword.Bluemix_notm}} Object Storage (COS). IBM COS replicates each DR backup across multiple {{site.data.keyword.Bluemix_notm}} regions to ensure availability if a single zone fails. You can open a support ticket to ask which regions your backups are being replicated to.

DR backups of the last 2 weeks are retained by default. The RPO for DR backups on {{site.data.keyword.Bluemix_notm}} is 1 week. The RTO if a disaster occurs is dependent upon the size of the database – 1.5 hours per terabyte of data.

It is essential for disaster recovery backups to be taken regularly as part of this managed service. If you have concerns about the time window in which backups run and want to schedule the backup for a less busy time on your system, open a support case.

## Amazon Web Services
{: #aws_br}

### Current Generation

When deployed on Amazon Web Services, the daily snapshot backup described in https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-br is also used for disaster recovery purposes. This DR backup is encrypted and stored in Amazon Web Services S3 across 3 availability zones (AZs) in each region. Regional DR backups allow you to restore your instance to another zone in the same region if needed. The RPO for DR backups on Amazon Web Services is 24 hours. The RTO if a disaster occurs will be best effort. The actual time required to complete a DR restore is dependent on many variables, including but not limited to:

 * the number of vCPUs in the instance
 * the amount of data stored in Native Cloud Object Storage (https://www.ibm.com/docs/en/db2w-as-a-service?topic=native-cloud-object-storage-support)

With the current generation of plans, the console allows you to copy backups to a separate region, and restore a backup to an instance in another region if needed. The region must be a supported region for Db2 Warehouse SaaS on Amazon Web Services. You are charged for the storage used for these copies, and for data transfer charges.

### Previous Generation

When deployed on AWS, the daily snapshot backup described in https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-br is also used for disaster recovery. This DR backup is encrypted and stored in Amazon Web Services S3 across 3 Availability Zones (AZs) in each region. Regional DR backups allow you to restore your instance to another zone in the same region if needed. The RPO for DR backups on Amazon Web Services is 24 hours. The RTO if a disaster occurs is approximately 4 hours.

## **Brazil: Supplementary Rule 14** (applies to systems provisioned for the Brazilian federal government)
{: #rule_14}

For the current generation of plans hosted on AWS, the disaster recovery (DR) option for {{site.data.keyword.dashdbshort_notm}} offerings is not available in Brazil for the federal government due to Supplementary Rule 14.

