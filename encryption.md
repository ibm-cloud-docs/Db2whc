---

copyright:
  years: 2014, 2025
lastupdated: "2024-09-14"

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

# Data security & encryption
{: #encryption}

The {{site.data.keyword.dashdbshort_notm}} service has security built into all levels of its architecture.
{: shortdesc}

The following methods are used to secure your data:
- Data at rest and database backups are encrypted using NIST SP 800-131A compliant cryptographic algorithms
- Data in motion is encrypted through SSL/TLS
- When deployed to IBM Cloud, backplane network connectivity is supported through IBM Cloud Service Endpoints
- When deployed to Amazon Web Services, backplane network connectivity is supported through Amazon Web Services PrivateLink
- Database-level security is supported through Role-Based Access Control (RBAC) and Row and Column Access Control (RCAC)
- Inter-node encryption is always enabled for the current generation of plans hosted on AWS, where available. It can optionally be enabled for your Flex or Flex Performance instance hosted on IBM Cloud. For more information, see [Inter-node encryption](/docs/Db2whc?topic=Db2whc-Inter-node)

Encrypted connections are enforced by default. For more information, see [SSL connectivity](/docs/Db2whc?topic=Db2whc-ssl_support).





