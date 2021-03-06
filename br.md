---

copyright:
  years: 2014, 2019
lastupdated: "2019-10-18"

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

# Snapshot backup and restore
{: #br}

A snapshot backup of the database is taken daily. Management and configuration of daily snapshot backups is built into the web console. 
{: shortdesc}

You can use the web console to restore from a snapshot backup if needed. Snapshot backups take approximately 3 minutes to complete. During this time, all writes in the system are queued, and all reads that don’t depend on the queued writes will continue. The RPO for snapshot backups is 24 hours. The RTO when restoring from a snapshot backup is 1 hour.

<!--| Plan              | Backup frequency | Number of retained backups | Backup retention period   | Self service |
|-------------------|------------------|----------------------------|---------------------------|--------------|
| MPP               | 1 / day          | 2                          | 2 days; FIFO* rollover   | No           |
| Flex              | 1 / day          | Up to 7                    | 7 days; FIFO* rollover   | Yes          |
| Flex Performance  | 1 / day          | Up to 7                    | 7 days; FIFO* rollover   | Yes          |
{: caption="Table 1. Backup frequency and retention" caption-side="top"} -->

## IBM Cloud
{: #ibm_cloud_br}

The last 7 daily snapshots are retained by default. Snapshot backups are encrypted and stored in block storage local to the {{site.data.keyword.dashdbshort_notm}} system. Snapshot backups are free of charge.

## Amazon Web Services
{: #aws_br}

The last 7 daily snapshots are retained by default. When deployed on Amazon Web Services, you can use the web console to configure a longer retention period for snapshot backups if desired. Potentially unlimited snapshots can be retained. Snapshot backups are encrypted and stored in Amazon Web services S3. S3 keeps copies of each snapshot backup across 3 availability zones (AZs) in each region by default, so there are 3 copies of each snapshot backup in total. The first 7 snapshot backups on Amazon Web Services are free of charge. You will be charged each month for the capacity required for any additional snapshot backups.

| Cloud provider      | Backup frequency | Number of retained backups | Retention period         |
|---------------------|------------------|----------------------------|--------------------------|
| IBM Cloud           | 1 / day          | Up to 7                    | 7 days; FIFO* rollover   |
| Amazon Web Services | 1 / day          | Up to 7 by default. Can be configured to retain potentially unlimited backups. | 7 days; FIFO* rollover by default. Can be configured to retain potentially unlimited backups.  |
{: caption="Table 1. Snapshot backup frequency and retention period" caption-side="top"}

*First in, first out

<!--## SMP and MPP plans
{: #smp_mpp}

The last 2 daily backups are retained.

The retained backups are used exclusively by IBM for only system recovery purposes if there is a disaster or system loss. A request to restore your database from a backup is not supported. You can export your data by using Db2 tools such as IBM Data Studio or by using the **db2 export** command. -->

<!--## Flex and Flex Performance plans
{: #flex}

Up to the last 7 daily backup snapshots are retained. The number of retained snapshots to a maximum of 7 depends on the size of each snapshot (equal to the amount of data that is changed between snapshots after the first) and the amount of storage space for retained backups.

From the {{site.data.keyword.dashdbshort_notm}} console, you can schedule your backups to run when it's most convenient and you can restore your database from any of your retained backup snapshots at any time that you choose. The system goes down during the restore period. An email is sent to notify you that the restore operation was completed.

![View of the web console backup and restore page](images/br.png)
-->
