---

copyright:
  years: 2014, 2020
lastupdated: "2020-09-21"

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

# Diagnosing and resolving high storage usage
{: #stor_intro}

This document describes ways to diagnose and, if necessary, reduce the storage usage on your {{site.data.keyword.dashdbshort_notm}} system. 
{: shortdesc}

## Check storage usage
{: #stor_chk}

Run the following SQL query as an `admin` user to check the current storage usage on every Db2 partition in your {{site.data.keyword.dashdbshort_notm}} instance:

```
db2 "SELECT DBPARTITIONNUM , ROUND((SUM(FS_USED_SIZE) / SUM(FS_TOTAL_SIZE)::DECFLOAT) * 100,2)  AS UTILIZATION_PERCENT, ROUND(( SUM(FS_TOTAL_SIZE) - SUM(FS_USED_SIZE)::DECFLOAT) / 1073741824,2) AS FREE_GB FROM TABLE(ADMIN_GET_STORAGE_PATHS(NULL,-2)) AS T WHERE STORAGE_GROUP_NAME NOT LIKE '%TEMP%' GROUP BY DBPARTITIONNUM ,CASE WHEN DBPARTITIONNUM = 0 THEN 'NP' ELSE 'P' END"
```
{: codeblock}

There are two possible causes for high storage usage:
- The storage attached to your system is reaching maximum capacity.
- There is empty space on the disks that must be reclaimed.

## Diagnosing and resolving
{: #stor_diag}

If the output from the previous SQL query indicates that storage usage on your instance is high, the following steps will help to diagnose and resolve this scenario:
1. Check if the instance has reclaimable space by running the following SQL query as an `admin` user:
   ```
   db2 "SELECT SUBSTR(TBSP_NAME, 1,30) AS TBSP_NAME, SUM(TBSP_USED_PAGES * TBSP_PAGE_SIZE)/ 1073741824 AS TBSP_USED_SIZE_GB, SUM((TBSP_PENDING_FREE_PAGES+ tbsp_free_pages) * TBSP_PAGE_SIZE)/ 1073741824 AS FREE_OR_PENDING_GB FROM TABLE(MON_GET_TABLESPACE('',-2)) where TBSP_NAME not like '%SYS%' and TBSP_NAME not like '%TEMP%' and RECLAIMABLE_SPACE_ENABLED = 1 and (TBSP_PENDING_FREE_PAGES+ tbsp_free_pages) >= 1 GROUP BY TBSP_NAME ORDER BY 3 DESC"
   ```
   {: codeblock}
1. If the data is very skewed across Db2 partitions, meaning that one or more Db2 partitions is almost full while other Db2 partitions still have significant capacity remaining, then see [Choosing a hash distribution key for a table in an MPP database](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/choosing_dist_key_mpp.html){: external}.
1. If one or more table spaces have reclaimable space, complete the following steps to reclaim that space: 

   Do not reclaim space during an online backup. The reclaim operation can also impact the performance of ongoing workloads, so it is best to run the following steps during off-peak hours.
   {: important}

   a. Verify that an online backup is not running:
      ```
      db2 "SELECT MEMBER,SUBSTR(UTILITY_DETAIL, 1, 150) AS CMD FROM TABLE(MON_GET_UTILITY(-2)) AS T"
      ```
      {: codeblock}
   b. For every table space in the list generated by the previous step, reclaim the unused space by running the following command:
      ```
      db2 alter tablespace <tablespace_name> reduce max
      ```
      {: codeblock}

1. If there is no disk space that can be reclaimed, you must either purge unwanted data or scale up the storage on your {{site.data.keyword.dashdbshort_notm}} instance to ensure database stability.

## Additional information
{: #stor_add_info}

[Reclaimable storage](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.5.0/com.ibm.db2.luw.admin.dbobj.doc/doc/c0055392.html){: external}

[Reclaiming unused storage in DMS table spaces](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.5.0/com.ibm.db2.luw.admin.dbobj.doc/doc/t0055397.html){: external}

[ALTER TABLESPACE statement](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.5.0/com.ibm.db2.luw.sql.ref.doc/doc/r0000890.html){: external}

[Distribution keys for multi-partitioned plans](/docs/Db2whc?topic=Db2whc-distribution_keys){: external}




