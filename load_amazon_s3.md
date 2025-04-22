---

copyright:
  years: 2014, 2024
lastupdated: "2025-03-09"

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
{:video: .video}

# Loading data from Amazon S3
{: #load_s3}

## External Tables
{: #aws_s3_et}

You can load data from Amazon S3 into {{site.data.keyword.dashdblong}} by using the built-in External Tables functionality. 
{: shortdesc}

Here’s an example SQL statement that inserts Amazon S3 data into a {{site.data.keyword.dashdbshort_notm}} table by using External Tables:

```
INSERT INTO <table-name> SELECT * FROM EXTERNAL '<mys3file.txt>' USING
  (CCSID 1208 s3('s3.amazonaws.com', 
  '<S3-access-key-ID>',
  '<S3-secret-access-key>', 
  '<my_bucket>'
     )
  )
```
{: codeblock}


<!-- <iframe class="embed-responsive-item" id="youtubeplayer1" title="Loading data from COS into IBM Db2 Warehouse on Cloud" type="text/html" width="640" height="390" src="//www.youtube.com/embed/RMMExarvBVk?rel=0" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen> </iframe> -->

## Db2 LOAD utility
{: #aws_s3_load}

You can also load data from Amazon S3 into {{site.data.keyword.dashdbshort_notm}} by using the built-in Db2 **LOAD** utility. 

Here’s an example SQL statement that uses the Db2 LOAD utility to load Amazon S3 data into {{site.data.keyword.dashdbshort_notm}}:

```
CALL SYSPROC.ADMIN_CMD('LOAD FROM "S3::<s3-endpoint-url>::<s3-access-key-ID>::<s3-secret-access-key>:
:<s3-bucket-name>::<path-to-data-file>" OF <filetype> <additional-load-options> INTO <table-name>)
```
{: codeblock}

For more information about the Db2 LOAD utility, see: [LOAD command](https://test.cloud.ibm.com/docs/Db2whc?topic=Db2whc-load_cos){: external}.


<!--
The following is an example usage of the Db2 **LOAD** command:

```
CALL SYSPROC.ADMIN_CMD('load from "S3::s3-us-west-2.amazonaws.com::<s3-access-key-id>:
:<s3-secret-access-key>::ibm-state-store::bdidata2TB/web_site.dat" of DEL modified by codepage=1208 
coldel0x7c WARNINGCOUNT 1000 MESSAGES ON SERVER INSERT into BDINSIGHTS2.web_site ');
```
{: codeblock}

For supported command options. see: [LOAD command](https://www.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.admin.cmd.doc/doc/r0008305.html){: external}.
-->

