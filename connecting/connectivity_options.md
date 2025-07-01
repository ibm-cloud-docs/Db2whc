---

copyright:
  years: 2014, 2020
lastupdated: "2025-03-19"

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

# Connectivity options on IBM Cloud
{: #connect_options}

{{site.data.keyword.dashdblong}} offers multiple secure connectivity options for your application connection requirements.  
{: shortdesc} 


## Connecting to a public endpoint (default option)
{: #pub_endpt}

As with any public cloud service, you can connect your application by way of a public host name that is provided to you at the time that your service is provisioned. Access to your data is protected by strong authentication, vast Db2 authorization options and access controls, encryption over the wire and at rest, and IBM security and compliance practices for development and operations. Optional IP allowlisting is offered. Create an IBM Support case if you want to enable IP allowlisting.

For application connections, do not use IP addresses to connect to the {{site.data.keyword.dashdbshort_notm}} instance, as the IP addresses resolved from the hostname may change. 
{: important}

### How to connect to a public endpoint:
{: #pub_endpt_steps}

You can also obtain your host name and credentials in the following way:

1. Log in to {{site.data.keyword.cloud_notm}} and click your service instance.
2. Click **Service credentials**.
3. Click **New credential**, then click **Add**.
4. After the credentials are created, under the `Actions` column, click **View credentials**.
5. In the following JSON document example, note the contents of the hostname, password, and username fields. You use these three components to make the public endpoint connection:


```
   {
    "apikey": "abcdefghijklmnopqrstuvwxyz0123456789",
    "db": "BLUDB",
    "host": "db2w-abcdefg.eu-de.db2w.cloud.ibm.com",
    "hostname": "db2w-abcdefg.eu-de.db2w.cloud.ibm.com",
    "https_url": "https://db2w-abcdefg.eu-de.db2w.cloud.ibm.com",
    "iam_apikey_description": "Auto-generated for key crn:v1:bluemix:public:dashdb:eu-de:a/abc62e1447e5587cfcff971d4aa7d473:c1cac901-755b-489c-a742-f41295cb5dd8:resource-key:11f5e7e5-4759-439e-8291-7febc09382ce",
    "iam_apikey_name": "Service credentials-1",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Manager",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/abc62e1447e5587cfcff971d4aa7d473::serviceid:ServiceId-aecb72c2-b048-4800-a0d3-263d7bfe4e6a",
    "parameters": {
    "role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Manager",
    "serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/abc62e1447e5587cfcff971d4aa7d473::serviceid:ServiceId-aecb72c2-b048-4800-a0d3-263d7bfe4e6a"
    },
    "password": "hereisthepassword123",
    "port": 50001,
    "ssldsn": "DATABASE=BLUDB;HOSTNAME=db2w.abcdefg.eu-de.db2w.cloud.ibm.com;PORT=50001;PROTOCOL=TCPIP;UID=bluadmin;PWD=hereisthepassword123;Security=SSL;",
    "ssljdbcurl": "jdbc:db2://db2w-abcdefg.eu-de.db2w.cloud.ibm.com:50001/BLUDB:sslConnection=true;",
    "uri": "db2://bluadmin:hereisthepassword123@db2w-abcdefg.eu-de.db2w.cloud.ibm.com:50001/BLUDB?ssl=true;",
    "username": "bluadmin"
    }
```

   ![Public network access to {{site.data.keyword.cloud_notm}}](images/public_connection.png "Graphical representation of user to cloud connection"){: caption="Figure 1. Public network access to {{site.data.keyword.cloud_notm}}" caption-side="bottom"}

## Connecting to a private endpoint: IBM Cloud service endpoint
{: #priv_endpt}

{{site.data.keyword.dashdbshort_notm}} supports private connectivity through an [{{site.data.keyword.cloud_notm}} service endpoint](/docs/account?topic=account-service-endpoints-overview). {{site.data.keyword.cloud_notm}} service endpoints securely route network traffic between different {{site.data.keyword.cloud_notm}} services through the {{site.data.keyword.cloud_notm}} private backplane network. When you configure your {{site.data.keyword.dashdbshort_notm}} instance with {{site.data.keyword.cloud_notm}} service endpoint connectivity, traffic between your cloud data warehouse and applications deployed on your {{site.data.keyword.cloud_notm}} account will not traverse any public networks.

For application connections, do not use IP addresses to connect to the {{site.data.keyword.dashdbshort_notm}} instance, as the IP addresses resolved from the hostname may change. 
{: important}

### How to configure IBM Cloud service endpoint connectivity
{: #cfg_endpt}

Complete the following steps to enable {{site.data.keyword.cloud_notm}} service endpoint connectivity for your {{site.data.keyword.dashdbshort_notm}} instance:

1. Enable your {{site.data.keyword.cloud_notm}} account to use virtual routing and forwarding (VRF) and {{site.data.keyword.cloud_notm}} service endpoints. To enable both of these items, see [Enabling VRF and service endpoints](/docs/account?topic=account-vrf-service-endpoint).

2. Configure your {{site.data.keyword.dashdbshort_notm}} instance for service endpoint connectivity.

   - **If you provisioned your {{site.data.keyword.dashdbshort_notm}} instance through the {{site.data.keyword.cloud_notm}} catalog**: [Create a case](https://cloud.ibm.com/unifiedsupport/supportcenter){: external} to request the configuration of your {{site.data.keyword.dashdbshort_notm}} instance for {{site.data.keyword.cloud_notm}} service endpoint connectivity. After this is complete, your {{site.data.keyword.dashdbshort_notm}} instance will be served on a new, non-internet-routable IP address. Information about how to access your {{site.data.keyword.dashdbshort_notm}} instance by using this newly configured private endpoint will be sent to you.

   - **If you purchased your {{site.data.keyword.dashdbshort_notm}} instance through IBM Sales**: If you requested private endpoint connectivity, your {{site.data.keyword.dashdbshort_notm}} instance will be provisioned with {{site.data.keyword.cloud_notm}} service endpoint connectivity. No further action is required.

After you've configured {{site.data.keyword.cloud_notm}} service endpoint connectivity for your {{site.data.keyword.dashdbshort_notm}} instance, it will only be accessible through a private endpoint. You will not be able to access your instance through a public endpoint.
{: note}

To learn more about the {{site.data.keyword.cloud_notm}} service endpoint service, see [Secure access to services using service endpoints](/docs/account?topic=account-service-endpoints-overview).

## Connecting to a virtual private network (VPN) endpoint
{: #vpn}

If you have an application that is deployed on a private network that is outside of the {{site.data.keyword.cloud_notm}} without access to the public internet and you want to connect it to your database over a virtual private network (VPN) connection, you can make the request at the time that you order the service or by opening an IBM Support case. IBM network engineers will assist your network engineers to set up the VPN tunnel between your private network and the {{site.data.keyword.cloud_notm}}.

### How to connect to a VPN endpoint
{: #priv_endpt_vpn_steps}

To establish a VPN connection to your cloud data warehouse behind a public endpoint, [create an {{site.data.keyword.cloud_notm}} Support case](https://cloud.ibm.com/unifiedsupport/cases/add){:external} that includes the following details:

* **Type of support**: Technical 
* **Category**: Databases 
* **Offering**: select your {{site.data.keyword.dashdbshort_notm}} instance 
* **Subject**: VPN Connection Request 
* **Description**: provide the following required information
  * **Customer-side VPN Peer Address** (your VPN endpoint): `<IP Address>`
  * **Customer-side Encryption Domain** (be specific about what is required – 10.0.0.0/8 is unworkable because 10 addressing is also used within the {{site.data.keyword.cloud_notm}} for back-end services): `<Domain>`
  * **Customer-side VPN Hardware & Version**: `<Hardware and Version number>`
  * **Customer-side VPN Contact** (technical contact name and email address): 
    * `<Name>` 
    * `<Title>` 
    * `<Email Address>`

  **Optional** (change only if the following default values are not suitable):

  *IKE/ISAKMP Parameters (Phase I)*

  * **Encryption Method**: IKEv1
  * **IKE Encryption / Encryption Algorithm**: AES-256
  * **Authentication Algorithm**: SHA1
  * **DH-Group**: Group 5
  * **Security Association Lifetime (seconds)**: 1d (86400 seconds)

  *IPSec Parameters (Phase II)*

  * **IPSec Encryption / Encryption Algorithm**: AES-256
  * **Authentication Algorithm**: SHA1
  * **DH-Group** (if using PF-Secrecy): Group 5
  * **Security Association Lifetime (seconds)**: 3600 seconds

After receipt of your request, {{site.data.keyword.cloud_notm}} technicians will open the appropriate firewall ports and allowlist the provided IP address. Communication and resolution to the request is made through the {{site.data.keyword.cloud_notm}} Support case ticket.

![Public network access to {{site.data.keyword.cloud_notm}} through a VPN](images/public_connection_vpn.png "Graphical representation of user to cloud connection"){: caption="Figure 2. Public network access to {{site.data.keyword.cloud_notm}} through a VPN" caption-side="bottom"}

## Connecting to {{site.data.keyword.dashdblong}} with Private Link

IBM Cloud private link gives you the ability to securely and privately connect to a {{site.data.keyword.dashdblong}} instance from your own IBM Cloud VPCs. With the IBM Cloud Private Link, traffic between {{site.data.keyword.dashdblong}} and your IBM Cloud VPCs, it does not traverse the public internet.

Complete the following steps to connect {{site.data.keyword.dashdblong}} with  private link:

1. Create an access to {{site.data.keyword.dashdbshort_notm}} console. The {{site.data.keyword.dashdbshort_notm}} console can be accessed with IAM users, or IAM roles.

2. In the console, navigate to the **Settings** --> **Access restriction** panel then enable private endpoints. You can optionally also disable public endpoints.

3. Navigate to the **Connections** tab in {{site.data.keyword.dashdblong}} console to get private endpoint service name and its details. Connect to DB using the connection details present in the connection’s private tab after creating ‘Virtual Private Endpoint Gateway’.

4. Create ‘Virtual Private Endpoint Gateway’ , navigate to **VPC Infrastructure** -> **Virtual Private Endpoint Gateway** then click on **Create**:


- Region - select the same region in which the VPC is created
- Name - Unique name for the VPE gateway
- Virtual private cloud - The VPC in which the gateway is to be created
- Cloud service offerings - Select “Db2 Warehouse” then opt the endpoint matching with the hostname present in “Private endpoints” tab from db2wh-console connections pages
- Ensure that TCP traffic is allowed through port on the VPC
- When you disable private connectivity, make sure to delete the VPE gateway

Once the [VPE-endpoint-gateway](https://cloud.ibm.com/docs/vpc?topic=vpc-ordering-endpoint-gateway&interface=ui){:external} is created successfully, you can connect to the Db2 database using the private connections details given in the {{site.data.keyword.dashdbshort_notm}} console.

### Consideration and Limitations



- You must create the Virtual private endpoint gateway for accessing {{site.data.keyword.dashdbshort_notm}} through private connectivity.

- The details required for creating Virtual private endpoint gateway will be available on private connections details present in the {{site.data.keyword.dashdbshort_notm}} console.

- You must create the Virtual private endpoint gateway in the same region where the {{site.data.keyword.dashdbshort_notm}} instance is deployed. To access your instance from other regions, you may have to setup VPN network.

## Using IP Allowlists with Your Formation

An **allowlist** is a security mechanism that specifies which IP addresses are allowed to access a resource. Any IP address not on the allowlist is blocked. This approach helps protect your environment by filtering traffic based on trusted sources.

You can use IP allowlists to restrict access to your formation. Once an allowlist is configured, only IP addresses included in the allowlist or within a specified range can connect.

### Key Points:
- Allowlists can be applied **only to public endpoints**.
- If the allowlist is **empty** (no IPs are listed), the restriction is **disabled** and connections from any IP address are allowed.
- Allowlists will regulate traffic **only for DB connectivity** (port `50001`). There is **no impact** on console access over port `443`.

## Setting an Allowlist Configuration

To enable IP allowlisting:

1. Open a support ticket with IBM Cloud.
2. Provide the IP address to be allowlisted.
3. Include a short description for the allowlist entry.

### IP Address Format

You can specify an IP in either of the following formats:

- A single IP address (e.g., `170.225.223.5`)
- A CIDR block (e.g., `192.168.1.0/24` or `170.225.227.6/32`)

### Description

Each allowlist entry requires a description. This should be meaningful for identification—such as a customer name, project code, or employee ID.

