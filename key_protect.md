---

copyright:
  years: 2014, 2023
lastupdated: "2024-08-02"

keywords: db2, Db2 Warehouse on Cloud, bring your own key, byok, crypto-shredding

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

# Key Protect integration
{: #key-protect-v2}

The data that you store in {{site.data.keyword.dashdblong}} is encrypted by default using randomly generated keys. If you need to control the encryption keys, you can use [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/key-protect?topic=key-protect-integrate-services) to create, add, and manage encryption keys. Then, you can associate those keys with your Db2 Warehouse on Cloud deployment to encrypt your Db2 databases.

To get started, you need [{{site.data.keyword.keymanagementserviceshort}}](https://cloud.ibm.com/catalog/services/key-protect){: external} provisioned on your {{site.data.keyword.cloud_notm}} account.

## Creating or adding a key in {{site.data.keyword.keymanagementserviceshort}}
{: #kp-create-add}

Navigate to your instance of {{site.data.keyword.keymanagementserviceshort}} and [generate or enter a key](/docs/key-protect?topic=key-protect-getting-started-tutorial).

## Granting service authorization
{: #kp-grant}

Authorize {{site.data.keyword.keymanagementserviceshort}} for use with Db2 Warehouse SaaS deployments:

1. Open your {{site.data.keyword.cloud_notm}} dashboard.
1. From the menu bar, select **Manage > Access (IAM)**.
1. In the side navigation, select **Authorizations**. Click **Create**.
1. In the _Source service_ menu, select the service of the deployment. For example, **Db2 Warehouse**.
1. In the _Source service instance_ menu, select **All service instances**.
1. In the _Target service_ menu, select **Key Protect**.
1. In the _Target service instance_ menu, select the service instance to authorize.
1. Enable the `Reader` role. Click **Authorize**.

## Using the Key Protect key
{: #kp-use}

After you grant your Db2 Warehouse instance permission to use your keys, you supply the Key Protect information on the Console Administration -> Settings -> Manage Keys tab. You must provide the name of the Key Protect instance and the key that was created in the "Creating or adding a key in Key Protect" section. After the information is provided, you then migrate the instance to Key Protect managed keys. 




