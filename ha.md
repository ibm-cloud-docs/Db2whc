---

copyright:
  years: 2014, 2024
lastupdated: "2024-11-08"

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

# High availability (HA) 
{: #ha}

The measure of a successful database solution is its availability. The architecture of {{site.data.keyword.dashdblong}} features multiple tiers of reliability, which allows for fast, automated recovery from any issues that the data warehouse might encounter.
{: shortdesc}

<!--
## MPP plan
{: #ha_mpp}

The {{site.data.keyword.dashdbshort_notm}} MPP plan cluster is provisioned with high availability.  

When a node goes down for an MPP plan, the HA component restarts your database partitions in the remaining healthy nodes. A short downtime occurs during this phase. 

After the node is added back to the cluster, the database engine must be restarted to run at full capacity. 
-->
<!--
## Flex Performance plan
{: #ha_flex}

If an unexpected node failure does occur, your Flex Performance MPP cluster is brought back to full capacity after a short downtime due to using the IBM Container Service (based on Kubernetes). Nodes from a pool are used to move the failed node entities. 
-->

### Compute HA
{: #compute_ha}

Any node failure is immediately detected by the cloud provider's container service. The containers and pods that were running in the failed node are scheduled to a new node automatically by the HA process. The system is back to 100% normal operation after a short downtime.

### Storage HA
{: #storage_ha}

{{site.data.keyword.dashdbshort_notm}} uses highly-reliable block storage, designed to provide consistent performance and protect data integrity and availability through maintenance events and unplanned failures. Storage is provisioned and managed independently of compute.

### Network HA
{: #net_ha}

Network connections are made highly available by provisioning your service with a redundant network interface card (NIC). 

If the container service detects a network issue, pods and containers can automatically restart after a short downtime.

