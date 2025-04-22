---

copyright:
  years: 2014, 2025
lastupdated: "2025-04-01"

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
{:attention: .attention}

# About 
{: #about}

{{site.data.keyword.dashdblong}} is a fully-managed, elastic cloud data warehouse that delivers independent scaling of storage and compute. It delivers a highly optimized columnar data store, actionable compression, and in-memory processing to supercharge your analytics and machine learning workloads.
{: shortdesc}

## Key features 
{: #key_features}

### Blazingly-fast engine

{{site.data.keyword.dashdbshort_notm}} is a column-organized, in-memory data warehouse designed for complex analytics and extreme concurrency. {{site.data.keyword.dashdbshort_notm}} delivers high performance on complex analytics workloads by using IBM BLU Acceleration, a collection of technologies pioneered by IBM Research that features the following key optimizations: 
- A columnar organized storage model 
- In-memory processing 
- Querying of compressed data sets
- Data skipping

### Scalable and elastic cloud service

{{site.data.keyword.dashdbshort_notm}} is an elastic service, and allows you to independently scale compute and storage through an intuitive UI or REST API.

### Native object storage support 

{{site.data.keyword.dashdbshort_notm}} on Amazon Web Services (AWS) introduces native object storage support to Db2. This functionality allows you to store traditional Db2 column-organized tables in Db2's native format on object storage while maintaining the existing SQL support and performance using a tiered storage architecture. Moving data from higher cost block storage to lower cost object storage can significantly reduce your costs and does not require changes to your workload. This feature is available on the current generation of AWS plans. For more information, see [Native Cloud Object Storage support](https://www.ibm.com/docs/en/db2woc?topic=native-cloud-object-storage-support){: external}

### Open data format table support 

{{site.data.keyword.dashdbshort_notm}} on AWS introduces new DATALAKE table support. This functionality provides Db2 users with the ability to access data that is stored on inexpensive, scalable, and reliable object storage in open data formats such as PARQUET and ORC from within the Db2 Warehouse. This feature is available on the current generation of AWS plans. For more information, see [Open data format table support](https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-open-data-format-table-support) {: external}

### Replication Support

{{site.data.keyword.dashdbshort_notm}} with Q Replication enables high-speed data replication for business continuity. This feature allows you to manage downtime with continuous availability (99.999%) and in-place recovery within a cluster. The cloud-native architecture of Db2 features multiple layers of resiliency with managed computation, highly available storage, and cross-cloud replication.  

### Expertly managed and highly secure

Day-to-day operations for {{site.data.keyword.dashdbshort_notm}}, including database monitoring, uptime checks and failovers, are fully automated. Operations are supplemented by a DevOps team that are on call to handle unexpected system failures. Data is encrypted at rest and in motion by default. Administrators can also restrict access to sensitive data through data masking, row permissions, and role-based security, and can utilize database audit utilities to maintain audit trails for their data warehouse.

### Highly resilient and reliable

{{site.data.keyword.dashdbshort_notm}} provides double protection for your data with built-in snapshot backups and geo-replicated disaster recovery backups.

### Compatible with on-premises data warehouses​

{{site.data.keyword.dashdbshort_notm}} can be configured with Oracle compatibility, so applications that were written for an Oracle database can run against {{site.data.keyword.dashdbshort_notm}} without having to be rewritten. {{site.data.keyword.dashdbshort_notm}} also comes with nearly 100% DDL, DML, and stored procedure compatibility with IBM Netezza®.

### Built-in machine learning and geospatial capabilities​

Train and run machine learning models directly in the {{site.data.keyword.dashdbshort_notm}} engine, using SQL, Python, or R. {{site.data.keyword.dashdbshort_notm}} also supports spatial analytics with Esri compatibility, including Esri data types such as GML, and integration with Jupyter Notebooks.

## Plans and configurations 
{: #plans_cfgs}

For information about the plans and configurations supported on IBM Cloud and Amazon Web Services (AWS), see [here](https://cloud.ibm.com/db2-wh).

This set of documentation covers the detailed commands and reference topics for the Db2 engine that powers {{site.data.keyword.dashdbshort_notm}}. To find the IBM Cloud documentation for the offering, see [here](https://cloud.ibm.com/docs/Db2whc?topic=Db2whc-about). The IBM Cloud documentation covers the high-level functionality for the cloud offering, and refers back to this set of documentation where appropriate. {: attention}
## Supported cloud providers and data centers
{: #sup_cp_dc}

{{site.data.keyword.dashdbshort_notm}} can be deployed on both {{site.data.keyword.cloud_notm}} and Amazon Web Services.

### Availability of plans in IBM Cloud data centers
{: #availability}

The following table provides information about the availability of the various {{site.data.keyword.dashdbshort_notm}} plans by {{site.data.keyword.cloud_notm}} data centers that are located in geographical regions:

| {{site.data.keyword.dashdbshort_notm}} plans | Asia/Pacific | Europe    | North/Central America     | South America |
|------------------------------|--------------|-----------|---------------------------|---------------|
| Flex                         | Tokyo        | Frankfurt | Dallas (us-south)         | *NA           |
|                              |              |           | Washington D.C. (us-east) |               |  
|      |||||
| Flex Performance             | Tokyo        | Frankfurt | Dallas (us-south)         | *NA           |
|                              |              |           | Washington D.C. (us-east) |               |  
|      |||||
| Flex One                     | Tokyo    | Frankfurt | Dallas (us-south)         | *NA           |
|                              |       | London    | Toronto                   |               | 
|                              |        |           | Washington D.C. (us-east) |               |
{: caption="Table 1. IBM Cloud data centers supporting {{site.data.keyword.dashdbshort_notm}} service plans" caption-side="top"}

*NA = Not available at this time

For information on deploying your {{site.data.keyword.dashdbshort_notm}} service in a network-isolated environment on the IBM Cloud, open a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter). {: external}

### Availability of plans in Amazon Web Services data centers
{: #availability_aws}

The current generation of plans on AWS is available in the following data centers:

| {{site.data.keyword.dashdbshort_notm}} plans | Asia/Pacific | Europe    | North/Central America     | South America    |
|----------------------------------------------|--------------|-----------|---------------------------|------------------|
| All current generation                       | Tokyo        | Frankfurt | N. Virginia               | Sao Paulo        |
|                                              | Sydney       |           |                           |                  | 
{: caption="Table 2. Amazon Web Services data centers supporting {{site.data.keyword.dashdbshort_notm}} service plans" caption-side="top"}

Support for additional AWS regions is coming soon.

The previous generation of plans on AWS is available in N. Virginia, Oregon, Frankfurt, London, Tokyo, Seoul, Singapore, and Sydney.

If you wish to provision a service instance in an AWS region not listed above, contact your local sales representative or open a [support case](https://cloud.ibm.com/unifiedsupport/supportcenter). You can also open a support case for information on deploying your {{site.data.keyword.dashdbshort_notm}} service in a network-isolated environment on AWS. 



<!--

{{site.data.keyword.dashdblong}} is a fully managed, high performance, petabyte-scale cloud data warehouse.

It delivers true elasticity with independent scaling of storage and compute, a highly optimized columnar data store, actionable compression and in-memory processing, all working together to supercharge your analytics workloads.
{: shortdesc}

## Db2 Warehouse on Cloud managed service
{: #managed_service}

The fully managed service of {{site.data.keyword.dashdbshort_notm}} handles all of the software upgrades, operating system updates, and hardware maintenance. The service includes 24x7 health monitoring of the database and infrastructure. If there is a hardware or software failure, the service is automatically restarted.
{: shortdesc} -->

<!-- ## Provisioning of Db2 Warehouse on Cloud
{: #whse_provision}

The {{site.data.keyword.dashdbshort_notm}} database can be provisioned on {{site.data.keyword.BluSoftlayer_full}} and for AWS.
{: shortdesc}

If you want to have the data warehouse provisioned for AWS, select the **MPP Small for AWS** plan. -->

<!--
## Data visualization
{: #visualize}

You can analyze and visualize your analysis by connecting to the following applications:

- [Watson Studio (formerly Data Science Experience)](/docs/Db2whc/connecting?topic=Db2whc-ds#watson_studio)
- [Cognos Analytics](/docs/Db2whc/connecting?topic=Db2whc-data_vis_bi#cognos)
- [Looker](https://docs.looker.com/setup-and-management/connecting-to-db){:external}
- [Tableau](/docs/Db2whc/connecting?topic=Db2whc-data_vis_bi#tableau)
- [SPSS Statistics](/docs/Db2whc/connecting?topic=Db2whc-ds#spss_stats)
- [SAS](/docs/Db2whc/connecting?topic=Db2whc-ds#sas)
- [Microsoft Excel](/docs/Db2whc/connecting?topic=Db2whc-data_vis_bi#excel)
- [Esri ArcGIS for Desktop](/docs/Db2whc/connecting?topic=Db2whc-data_vis_bi#esri_arcgis)

The following table provides information about the availability of the various {{site.data.keyword.dashdbshort_notm}} plans by Amazon Web Services data centers that are located in geographical regions:

| {{site.data.keyword.dashdbshort_notm}} plans | Asia/Pacific | Europe    | North/Central America     | South America |
|------------------------------|--------------|-----------|---------------------------|---------------|
| Flex                         | Seoul        | Frankfurt | N. Virginia | *NA           |
|                              | Singapore    | London    | Oregon          |               |
|                              | Sydney       |           |             |               |
|                              | Tokyo        |           |             |               | 
|      |||||
| Flex Performance             | Seoul        | Frankfurt | N. Virginia | *NA           |
|                              | Singapore    | London    | Oregon     |               | 
|                              | Sydney       |           |             |               |
|                              | Tokyo        |           |             |               |  

{: caption="Table 2. Amazon Web Services data centers supporting Db2 Warehouse on Cloud service plans" caption-side="top"}

*NA = Not available at this time

-->
