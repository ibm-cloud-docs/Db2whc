---

copyright:
  years: 2014, 2024
lastupdated: "2024-03-04"

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

# Loading data from on-premises systems with IBM Lift CLI
{: #onprem}

[IBM Lift CLI](https://www.ibm.com/products/lift){: external} is a free ground-to-cloud data migration tool that securely moves your data from on-premises systems to {{site.data.keyword.dashdblong}} plans hosted on IBM Cloud. IBM Lift CLI is available for the Flex One, Flex, and Flex Performance plans hosted on IBM Cloud.
{: shortdesc}

The CLI Lift application migrates your data to the {{site.data.keyword.Bluemix_notm}} from the various data sources listed in Table 1. 

| Target database on {{site.data.keyword.Bluemix_notm}} | Data source |
|------------------------------|-------------|
| IBM Db2 Warehouse SaaS       | IBM Db2 |
|                              | IBM Db2 Warehouse |
|                              | IBM Integrated Analytics System |
|                              | IBM PureData System for Analytics |
|                              | Oracle Database |
|                              | Microsoft SQL Server |
|                              | CSV file format |
{: caption="Table 1. Migration data sources" caption-side="top"}

When your data source is IBM Db2, IBM Db2 Warehouse, IBM Integrated Analytics System, or IBM PureData System for Analytics, migration of your data with Lift happens in two phases:
- Migrating the table structure of the source database
- Moving data into IBM Db2 Warehouse SaaS

## Migrating Table Structure

The Lift application may accept obsolete TLS protocol in SSL handshake if the server it is connecting to does not support TLS version 1.2. To ensure TLS 1.0 and TLS 1.1 will not be in use during communication, edit `liftMain` file adding in lines 115 and 118 `-Djdk.tls.client.protocols=TLSv1.2 -Dhttps.protocols=TLSv1.2` to Java™ invocation as specified [here](https://www.ibm.com/support/pages/how-do-i-change-default-ssltls-protocol-my-java™-application-will-use).
{: important}

Migrate your table structure by using the following lift ddl command example, which extracts the Data Definition Language (DDL) from the source database and applies it to the target database:

```
% lift ddl --migrate --source-schema <source-schema-name> --source-object <source-object-name> 
--source-database <source-database-name> --source-user <source-user-name> 
--source-password <source-password> --source-host <source-database-host-name> 
--source-database-port <source-database-port> --source-database-type <source-database-type> 
--target-user <target-user-name> --target-password <target-password> 
--target-host <target-database-host-name>

```
{: codeblock}

For more available command options, run the lift ddl --help command.

## Moving Data

The Lift application may accept obsolete TLS protocol in SSL handshake if the server it is connecting to does not support TLS version 1.2. To ensure TLS 1.0 and TLS 1.1 will not be in use during communication, edit `liftMain` file adding in lines 115 and 118 `-Djdk.tls.client.protocols=TLSv1.2 -Dhttps.protocols=TLSv1.2` to Java™ invocation as specified [here](https://www.ibm.com/support/pages/how-do-i-change-default-ssltls-protocol-my-java™-application-will-use).
{: important}

Extract the table data into a CSV file by running the following lift extract command example:

 ```
% lift extract --source-schema <source-schema-name> --source-table <source-table-name> 
--source-database <source-database-name> --source-host <source-host-name> 
--source-user <source-user-name> --source-password <source-password> 
--source-database-port <source-database-port> --source-database-type <ias/db2/db2w> 
--file <path-to-csv-file>
```
{: codeblock}

The ias, db2, and db2w settings for the –source-database-type command option are used to specify the particular source database type.

•  Move the CSV file and stage it in the landing zone of the target database by running the following lift put command example:

```
% lift put --file <path-to-csv-file> --target-user <target-user-name> 
--target-password <target-password> --target-host <target-database-host-name>
```
{: codeblock}

•  Load the data from the CSV file into the target database by running the following lift load command example:

```
% lift load --filename <csv-file-name> --target-schema <target-schema-name> 
```
{: codeblock}

```
--target-table <target-table-name> --file-origin <extract-ias/extract-db2/extract-db2w> 
```
{: codeblock}

```
--target-user <target-user-name> --target-password <target-password> 
```
{: codeblock}

```
--target-host <target-database-host-name>
```
{: codeblock}

The extract-ias, extract-db2, and extract-db2w settings for the --file-origin command option are used to specify that the CSV file was extracted from a particular database by using the lift extract command.

After completing these steps, you can run queries against your data.


After your table structure is in place, you can start moving your data. Lift CLI extracts the data from your table into a CSV file, moves that file over the network and stages it in the landing zone of the target database, and then loads the data into the database.


To download and install Lift, see the IBM Db2 Download Center: [Download Lift](https://epwt-www.mybluemix.net/software/support/trial/cst/programwebsite.wss?siteId=1120&tabId=5230&p=1&h=null){:external}.








