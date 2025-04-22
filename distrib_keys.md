---

copyright:
  years: 2014, 2025
lastupdated: "2025-01-18"

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

# Distribution keys for multi-partitioned plans
{: #distribution_keys}

When creating a table in one of the {{site.data.keyword.dashdblong}} [multi-partitioned plans](/docs/Db2whc?topic=Db2whc-about#plans_cfgs){: external}, you can decide how you want to distribute data among data partitions. 
{: shortdesc}

You can use either [hash distribution](#hash_distrib) or [random distribution](#random_distrib).

## Hash distribution
{: #hash_distrib}

With hash distribution, data is distributed by applying a hashing algorithm to the values in the columns that are listed in a _distribution key_. A well-chosen distribution key can balance two objectives:

- Maximizing parallel processing of queries and maximizing the use of available storage space by distributing table data evenly across the system, and
- Minimizing the time that it takes to fetch data by collocating data that is likely to be fetched together.

In general, a well-chosen hash distribution key produces the best performance. You can specify the distribution key by including the `DISTRIBUTE BY HASH` clause in the **CREATE TABLE** statement:

```
    CREATE TABLE MYTABLE
    (
      COL1 INT,
      COL2 VARCHAR(5)
    )
    DISTRIBUTE BY HASH( COL1 )
```
{: codeblock}

For more information about choosing hash distribution keys, see [Choosing a hash distribution key for a table in an MPP database](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.doc/learn_how/choosing_dist_key_mpp.html){: external}.

## Random distribution
{: #random_distrib}

With random distribution, data is distributed evenly across the system. Random distribution maximizes parallel processing of queries and maximizes the use of available storage space.

Consider using random distribution as a simpler alternative to hash distribution, for the following reasons:

1. If you don't have enough information to choose an effective hash distribution key,
1. If you know that collocation isn't needed for the queries that are entered against the table, or
1. If the table is small enough that performance is not affected by the distribution.

You can use random distribution by including the `DISTRIBUTE BY RANDOM` clause in the **CREATE TABLE** statement.

If you specify `DISTRIBUTE BY RANDOM` when creating a table with a primary or unique key, the database manager implements the random distribution by creating a hash key on the unique or primary key. In this case, when you view the table definition in the web console or the catalog tables, you'll see this hash distribution key despite the fact that you specified `DISTRIBUTE BY RANDOM` when you created the table.

```
    CREATE TABLE MYTABLE
    (
      COL1 INT,
      COL2 VARCHAR(5)
    )
    DISTRIBUTE BY RANDOM
```
{: codeblock}

## Default behavior
{: #default_behav}

If you do not specify a distribution clause when creating a table in a multi-partitioned plan, a default hash distribution key is used.




