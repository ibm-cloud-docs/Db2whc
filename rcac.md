---

copyright:
  years: 2014, 2024
lastupdated: "2023-06-14"

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

# Row and column access control (RCAC)
{: #rcac}

{{site.data.keyword.dashdblong}} comes equipped with powerful user security features that can help you manage security at the row and column level. This fine-grained access control that is known as row and column access control (RCAC) in {{site.data.keyword.dashdbshort_notm}}, works with [user roles](/docs/Db2whc?topic=Db2whc-user_roles). 
{: shortdesc}

RCAC can be used to ensure that your database users can access only the portions of database tables that are required for their work. For example, a hospital might have a policy that states a doctor can see the data of only their patients and not the patients of other doctors. In the following example of a patient data table,

| Patient name | Chart | Doctor name |
|--------------|-------|-------------|
| Alice | Aa BB cc | Smith |
| Bob | aA Bb CC | Chan |
| Charlie | AA BB CC | Morton |
{: caption="Table 1. Patient data table" caption-side="top"}

Dr. Smith is restricted to seeing only Alice's data, as depicted in the following table view:

| Patient name | Chart | Doctor name |
|--------------|-------|-------------|
| Alice | Aa BB cc | Smith |
{: caption="Table 2. Dr. Smith's view of the patient data table" caption-side="top"}

You can apply RCAC rules to your {{site.data.keyword.dashdbshort_notm}} instance to enforce the hospital's policy.

For more information about RCAC, see [RCAC overview](https://www.ibm.com/support/knowledgecenter/en/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/rcac_overview.html){: external}.








