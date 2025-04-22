---

copyright:
  years: 2014, 2025
lastupdated: "2025-04-08"

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

# Loading data from Db2
{: #load_db2}

You can load data from a Db2 on-premises system into {{site.data.keyword.dashdblong}} with IBM Lift CLI, a free ground-to-cloud data migration tool. IBM Lift CLI is available for the Flex One, Flex, and Flex Performance plans hosted on IBM Cloud.
{: shortdesc}

Migration of your data with Lift happens in two phases: 
- Migrating the table structure of the source database
- Moving data into {{site.data.keyword.dashdbshort_notm}} 

## Migrating table structure
{: #mig_table_struct}

Migrate your table structure by using the following `lift ddl` command example, which extracts the Data Definition Language (DDL) from the source database and applies it to the target database:

```
% lift ddl --migrate --source-schema <source-schema-name> --source-object <source-object-name> 
--source-database <source-database-name> --source-user <source-user-name> 
--source-password <source-password> --source-host <source-database-host-name> 
--source-database-port <source-database-port> --source-database-type <source-database-type> 
--target-user <target-user-name> --target-password <target-password> 
--target-host <target-database-host-name>
```
{: codeblock}

For more available command options, run the `lift ddl --help` command.

## Moving data
{: #move_data}

After your table structure is in place, you can start moving your data. Lift CLI extracts the data from your table into a CSV file, moves that file over the network and stages it in the landing zone of the target database, and then loads the data into the database:

1. Extract the table data into a CSV file by running the following `lift extract` command example:

   ```
   % lift extract --source-schema <source-schema-name> --source-table <source-table-name> 
   --source-database <source-database-name> --source-host <source-host-name> 
   --source-user <source-user-name> --source-password <source-password> 
   --source-database-port <source-database-port> --source-database-type <ias/db2/db2w> 
   --file <path-to-csv-file>
   ```
   {: codeblock}

   The `ias`, `db2`, and `db2w` settings for the `–source-database-type` command option are used to specify the particular source database type.

2. Move the CSV file and stage it in the landing zone of the target database by running the following `lift put` command example:

   ```
   % lift put --file <path-to-csv-file> --target-user <target-user-name> 
   --target-password <target-password> --target-host <target-database-host-name>
   ```
   {: codeblock}

3. Load the data from the CSV file into the target database by running the following `lift load` command example:

   ```
   % lift load --filename <csv-file-name> --target-schema <target-schema-name> 
   --target-table <target-table-name> --file-origin <extract-ias/extract-db2/extract-db2w> 
   --target-user <target-user-name> --target-password <target-password> 
   --target-host <target-database-host-name>
   ```
   {: codeblock}

   The `extract-ias`, `extract-db2`, and `extract-db2w` settings for the `--file-origin` command option are used to specify that the CSV file was extracted from a particular database by using the `lift extract` command.

After completing these steps, you can run queries against your data.

