---

copyright:
  years: 2014, 2020
lastupdated: "2020-04-15"

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

# Connecting overview
{: #connect_ov}

You can connect command-line interfaces, IBM® or third-party applications and tools, or apps that you create to your {{site.data.keyword.dashdbshort_notm}} database. 
{: shortdesc}

## Prerequisites
{: #prereqs}

Before attempting to connect to your {{site.data.keyword.dashdbshort_notm}} database, verify that you have the prerequisites. 

- Collect database details and credentials

   To connect to your database, you need database details (such as the host name) and credentials (such as a user ID and password.) You can collect this connection information from the {{site.data.keyword.dashdbshort_notm}} web console.

- Verify that a supported driver is installed

   - If your application or tool already contains an appropiate compatible version of IBM Data Server Driver Package, then your application or tool is able to connect to your {{site.data.keyword.dashdbshort_notm}} database by using that driver.
   - Otherwise, install the Db2 driver package, which you can download from the {{site.data.keyword.dashdbshort_notm}} web console.

- Configure your environment

  - Add entries to the driver configuration file, `db2dsdriver.cfg`, for your database.
  - Secure Sockets Layer (SSL)

    Connection details, such as which port to use and the connection string, depend on whether you use SSL connections. Using SSL is strongly recommended because of the stronger security it provides.

    <!-- You can choose to connect with or without SSL. Connection details, such as which port to use and the connection string, depend on whether you use SSL connections. -->

    To use SSL connections, you need a CA certificate:
    - If you use the most recent {{site.data.keyword.dashdbshort_notm}} driver package, the certificate file is bundled with the package and used for connections.
    - If you use the IBM Data Server Driver Package, you can download the SSL certificate from the {{site.data.keyword.dashdbshort_notm}} web console.

- Confirm that ports are available

   If your network is behind a firewall, confirm that communications are permitted on port number `50000` for standard protocols or port number `50001` for SSL connections.

   Port number `50000` is permitted only when a risk document is signed.
  {: note}

<!-- Before you can connect to your {{site.data.keyword.dashdbshort_notm}} database, verify that you completed downloading and installing the necessary components on the prerequisites checklist: 

- [Prerequisites checklist](prereqs.html) -->

### Collecting connection information
{: #collect_info}

- [Database details and connection credentials](/docs/Db2whc/connecting?topic=Db2whc-db_details_cxn_creds)

### Downloading and installing driver package
{: #dl_install}

- [Download driver package](/docs/Db2whc/connecting?topic=Db2whc-dr_pkg)
- [Installing on Linux or PowerLinux](/docs/Db2whc/connecting?topic=Db2whc-dr_pkg#install_dr_pkg_linux)
- [Installing on Mac OS X](/docs/Db2whc/connecting?topic=Db2whc-dr_pkg#install_dr_pkg_mac)
- [Installing on Windows](/docs/Db2whc/connecting?topic=Db2whc-dr_pkg#install_dr_pkg_windows)

### Configuring your environment
{: #cfg_env}

- [Configuring your local environment](/docs/Db2whc/connecting?topic=Db2whc-dr_pkg#cfg_loc_env)
- [SSL connectivity](/docs/Db2whc/connecting?topic=Db2whc-ssl_support)

## Connectivity options
{: #connect_opts}

{{site.data.keyword.dashdbshort_notm}} offers multiple secure connectivity options depending on your application connection requirements.  
{: shortdesc}

- See [Connectivity options on IBM Cloud](/docs/Db2whc/connecting?topic=Db2whc-connect_options).
- See [Connectivity options on Amazon Web Services](/docs/Db2whc/connecting?topic=Db2whc-connect_options_aws).

## Connecting programmatically
{: #conx_prgrm}

You can use common programming languages to create applications that connect to a {{site.data.keyword.dashdbshort_notm}} database.
{: shortdesc}

- [JDBC](/docs/Db2whc/connecting?topic=Db2whc-con_program#con_prog_jdbc)
- [Microsoft Windows ODBC or CLI](/docs/Db2whc/connecting?topic=Db2whc-con_program#con_prog_odbc_cli)
- [.NET](/docs/Db2whc/connecting?topic=Db2whc-con_program#con_prog_net)
- [ODBC Data Source Administrator](/docs/Db2whc/connecting?topic=Db2whc-con_program#con_prog_odbc_dsa)
- [PHP](/docs/Db2whc/connecting?topic=Db2whc-con_program#con_prog_php)
- [REST API](/docs/Db2whc/connecting?topic=Db2whc-con_rest_api)
<!-- - [C++]() -->
<!-- - [Java]() -->
<!-- - [Node.js]() -->
<!-- - [Perl]() -->
<!-- - [Python]() -->

## Integrating apps and tools
{: #conx_apps_tools}

You can also connect external applications and tools to {{site.data.keyword.dashdbshort_notm}} and use them to further manage or analyze your data. For example:

### Data integration
{: #di}

- Connect your {{site.data.keyword.Bluemix_short}} applications that need an analytics database.
- [DataStage](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#datastage)
- [Informatica](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#informatica)
- [Lift](https://www.ibm.com/products/lift){:external}
- [InfoSphere Data Replication](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#idr)
- [Segment](https://segment.com/docs/destinations/db2/){:external}
- [Data Studio](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#data_studio)
- [Data Server Manager](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#dsm)
- [CLPPLUS](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#clpplus)
- [Aginity Workbench to migrate Netezza® data models and data to {{site.data.keyword.dashdbshort_notm}}](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#aginity_wb)
- [InfoSphere Data Architect to design and deploy your database schema](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#ida)

### Data visualization/BI
{: #dvis_bi}

- [Cognos Analytics to run Business Intelligence reports against your data](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#cognos)
- [Looker](https://docs.looker.com/setup-and-management/connecting-to-db){:external}
- [Tableau](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#tableau)
- [Microsoft Excel](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#excel)
- [Esri ArcGIS for Desktop to perform geospatial analytics and map publishing with your data](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#esri_arcgis)

### Data science
{: #dsci}

- [Watson Studio (formerly IBM Data Science Experience)](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#watson_studio)
- [SPSS Statistics](/docs/Db2whc/connecting?topic=Db2whc-connect_ibm#spss_stats)
- [SAS](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#sas)
- [Local R development environment](/docs/Db2whc/connecting?topic=Db2whc-connect_3rd_party#r_dev_env)

## Connecting to another Db2 database
{: #fed}

Db2 data virtualization (also known as federation) is supported by {{site.data.keyword.dashdbshort_notm}}. Data virtualization gives you single-query access to all of your data that is on multiple distributed databases anywhere in your organization. You can access data that is on any of your Db2 or Informix data sources, both in the cloud and on premises. 

This function is supported on all versions of {{site.data.keyword.dashdbshort_notm}}.

- [Data virtualization (federation)](/docs/Db2whc?topic=Db2whc-data_virt_fed)


