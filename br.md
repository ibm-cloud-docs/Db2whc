---

copyright:
  years: 2014, 2025
lastupdated: "2025-04-18"

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

# Backup and restore
{: #br}

A snapshot backup of the database is taken daily. Management and configuration of daily snapshot backups are built into the web console. While the backup is in progress, all writes in the system are queued, and all reads that do not depend on the queued writes continue to run.

You can use the web console to restore from a snapshot backup.

A snapshot restore restores the entire database to the state it was in when the backup was created. To restore only one object or a subset of objects, use the [logical schema backup and restore](https://www.ibm.com/docs/en/db2w-as-a-service?topic=database-schema-level-table-level-backup-restore) functionality.

<!--| Plan              | Backup frequency | Number of retained backups | Backup retention period   | Self service |
|-------------------|------------------|----------------------------|---------------------------|--------------|
| MPP               | 1 / day          | 2                          | 2 days; FIFO* rollover   | No           |
| Flex              | 1 / day          | Up to 7                    | 7 days; FIFO* rollover   | Yes          |
| Flex Performance  | 1 / day          | Up to 7                    | 7 days; FIFO* rollover   | Yes          |
{: caption="Table 1. Backup frequency and retention" caption-side="top"} -->

## IBM Cloud
{: #ibm_cloud_br}

### Current Generation
By default, daily snapshots are retained for the last seven days. When deployed on IBM Cloud, you can use the web console to configure a longer retention period for snapshot backups. While almost unlimited snapshots can be retained, the number can also be lowered to save on cost. At least one backup must be retained to maintain compliance with various standards.

Snapshot backups are encrypted and stored in IBM Cloud Could Object Storage (COS). COS keeps copies of each snapshot backup across three availability zones (AZs) in each region by default, so there are three copies of each snapshot backup in total.

With the current generation of plans, you are charged for all backups. The backup process backs up data on both block and in [native cloud object storage](https://www.ibm.com/docs/en/db2w-as-a-service?topic=native-cloud-object-storage-support). The backups are comprised of snapshots of block storage, all data in Native COS, and various required metadata stored in IBM Cloud Object Storage.

The recovery point objective (RPO) for snapshot backups is 24 hours. The recovery time objective (RTO) when restoring from a snapshot backup for the current generation is dependent upon the amount of data stored in object storage. The RTO is approximately 1.5 TB/hour.

### Previous Generation
By default, daily snapshots are retained up to the last seven days. Snapshot backups are encrypted and stored in block storage that is local to the {{site.data.keyword.dashdbshort_notm}} system. Snapshot backups are free of charge.

The recovery point objective (RPO) for snapshot backups is 24 hours. The recovery time objective (RTO) when restoring from a snapshot backup is approximately one hour.

## Amazon Web Services
{: #aws_br}

### Current Generation
By default, daily snapshots are retained for the last seven days. When deployed on Amazon Web Services, you can use the web console to configure a longer retention period for snapshot backups. While almost unlimited snapshots can be retained, the number can also be lowered to save on cost. At least one backup must be retained to maintain compliance with various standards.

Snapshot backups are encrypted and stored in AWS Simple Storage Service (S3). AWS S3 keeps copies of each snapshot backup across three availability zones (AZs) in each region by default, so there are three copies of each snapshot backup in total.

With the current generation of plans, you are charged for all backups. The backup process backs up data on both block and in [native cloud object storage](https://www.ibm.com/docs/en/db2w-as-a-service?topic=native-cloud-object-storage-support). The backups are comprised of snapshots of block storage, all data in Native COS, and various required metadata stored in AWS S3 backup.

The recovery point objective (RPO) for snapshot backups is 24 hours. The recovery time objective (RTO) when restoring from a snapshot backup for the current generation is dependent upon the amount of data stored in object storage. The RTO is approximately 1.5 TB/hour.

### Previous Generation
With the previous generation of plans, the first seven snapshot backups on Amazon Web Services are free of charge. You are charged each month for the capacity required for any additional snapshot backups.

The recovery point objective (RPO) for snapshot backups is 24 hours. The recovery time objective (RTO) when restoring from a snapshot backup is approximately one hour.

| Cloud provider                            | Backup frequency | Number of retained backups              | Retention period         |
|-------------------------------------------|------------------|-----------------------------------------|--------------------------|
| IBM Cloud (previous generation)                                | 1 / day          | Up to 7                                 | 7 days; FIFO* rollover   |
| IBM Cloud (current generation)  | 1 / day          | 7 by default; can be increased or decreased by configuring retention period | 7 days default; can be increased or decreased; FIFO rollover 
| Amazon Web Services (previous generation) | 1 / day          | Up to 7 by default; Can be increased    | 7 days; FIFO* rollover   |
| Amazon Web Services (current generation)  | 1 / day          | 7 by default; can be increased or decreased by configuring retention period | 7 days default; can be increased or decreased; FIFO rollover 
{: caption="Snapshot backup frequency and retention period" caption-side="top"}

*First in, first out

## Logical schema backup and restore

This feature provides the ability to do full, cumulative incremental, or delta incremental backup of a Db2 schema followed by full restore of the schema or table(s) within the schema. [Logical schema backup](https://www.ibm.com/docs/en/db2w-as-a-service?topic=database-schema-level-table-level-backup-restore) is a flexible and lightweight way to backup and restore table level data. 

<!--## SMP and MPP plans
{: #smp_mpp}

The last 2 daily backups are retained.

The retained backups are used exclusively by IBM for only system recovery purposes if there is a disaster or system loss. A request to restore your database from a backup is not supported. You can export your data by using Db2 tools such as IBM Data Studio or by using the **db2 export** command. -->

<!-- ## Flex and Flex Performance plans
{: #flex}

Up to the last 7 daily backup snapshots are retained. The number of retained snapshots to a maximum of 7 depends on the size of each snapshot (equal to the amount of data that is changed between snapshots after the first) and the amount of storage space for retained backups.

From the {{site.data.keyword.dashdbshort_notm}} console, you can schedule your backups to run when it's most convenient and you can restore your database from any of your retained backup snapshots at any time that you choose. The system goes down during the restore period. An email is sent to notify you that the restore operation was completed.

![View of the web console backup and restore page](images/br.png)
-->
