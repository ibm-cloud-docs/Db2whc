---

copyright:
  years: 2014, 2024
lastupdated: "2024-08-03"

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

# Inter-node encryption
{: #Inter-node encryption}

For the current generation of plans hosted on AWS, inter-node encryption is always enabled, where available. As of September 2023, inter-node encryption is available in all AWS regions except sa-east-1 (Sao Paulo). For the Flex and Flex Performance plans hosted on IBM Cloud, you can optionally choose to enable this form of encryption.
{: shortdesc}

Inter-node encryption is an additional layer of security that protects inter-node traffic between internal Db2 nodes in a massively parallel processing (MPP) cluster. It supplements the SSL encryption that is already in use between the server and your applications.

Inter-node encryption ensures that your data is processed with encryption at all points from your application to physical storage and back, which protects your information from physical and software-based attacks. Leaving inter-node traffic unencrypted means that your data is transferred in plain text between the physical hardware nodes that make up your Db2 MPP instance.  IBM already employs a variety of security protocols to protect such traffic to ensure the security and integrity of the unencrypted internal data flows. With this new feature, IBM provides an additional security layer to protect the data.

Due to the additional processing required to encrypt data on send and decrypt on receive, workloads with significant data movement may see a performance impact as little as 5% or as much as 20%.  If your instance is hosted on IBM Cloud, your solution architect must evaluate this performance impact against your need to encrypt internal traffic flows. In some cases, it might be warranted (for instance in heavily regulated industries or where end users demand such encryption). In other cases, the existing in-depth security protocols may be sufficient. 

IBM Cloud plans only: To enable inter-node encryption, open the web console, select **Administration**, and navigate to the **Settings** -> **Encryption** tab. Enabling or disabling inter-node encryption can be done online, and takes effect immediately. Choosing to enable inter-node encryption does not impact the Service Level Agreement (SLA), self-service backups, database replication, or scaling.
