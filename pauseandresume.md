---

copyright:
  years: 2014, 2025
lastupdated: "2023-04-30"

keywords:

subcollection: Db2whc

---

# Pause and resume

{: #scale}

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

{{site.data.keyword.dashdblong}} provides you with the ability pause and resume your service.
{: shortdesc}

For information about using the REST API to pause and resume, see [REST API](https://cloud.ibm.com/apidocs/db2-warehouse-on-cloud){: external}.

When your system is paused the system's compute is scaled down which disables data access. It will also pause compute billing for the system.

When your system is resumed, compute billing will be resumed. Compute will scale back up. It will take a similar amount of time to a compute scaling operation for the system to become available again.

If your system is paused during a scheduled update, it will automatically be resumed during the scheduled update time period and will billed accordingly.
