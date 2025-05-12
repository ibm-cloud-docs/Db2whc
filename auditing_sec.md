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



# Auditing for IBM Db2 Warehouse as a Service

{{site.data.keyword.at_full_notm}} allows you to forward the Db2 diagnostic log (db2diag.log) from your {{site.data.keyword.cloud_notm}} instances to your own Log Analysis with LogDNA service instance. Choosing to enable log forwarding allows you to use Log Analysis to retain these logs for the time period required by your organization, or to search or analyze the logs.

As a security officer, auditor, or manager, you can use the {{site.data.keyword.at_full}} service to track how users and applications interact with the Db2 Warehouse on Cloud service in {{site.data.keyword.cloud_notm}}. {: shortdesc}

{{site.data.keyword.at_full_notm}} records user-initiated activities that change the state of a service in {{site.data.keyword.cloud_notm}}. You can use this service to investigate abnormal activity and critical actions and to comply with regulatory audit requirements. In addition, you can be alerted about actions as they happen. The events that are collected comply with the Cloud Auditing Data Federation (CADF) standard. For more information, see the getting started tutorial for {{site.data.keyword.at_full_notm}}.

Activity Tracker with LogDNA integration is available for {{site.data.keyword.dashdblong}} deployments in the regions according to the following table: 

| Deployment region | Activity Tracker region |
|----------|-----------|
| Dallas | us-south |
| Washington | us-east |
| Frankfurt | eu-de |
| London | eu-gb | 
| Sydney | au-syd |
| Tokyo | jp-tok |
| Toronto | ca-tor |
{: caption="Table 1. Activity Tracker regions" caption-side="top"}


## Activity Tracker with LogDNA provisioning
{: #at_log_analysis}

After you provision the service, events are automatically forwarded from all of your {{site.data.keyword.dashdblong}} deployments in the same region.

The service can be provisioned from its [catalog page](https://cloud.ibm.com/catalog/services/logdnaat?callback=%2Fobserve%2Factivitytracker%2Fcreate){: external} or from an existing [Observability Dashboard](https://cloud.ibm.com/observe/activitytracker){: external}.

The Activity Tracker with LogDNA service has a Lite plan that is free to use, but it only offers streaming events. To take advantage of the tagging, export, retention, and other features, you need to use one of the [paid plans](/docs/activity-tracker?topic=activity-tracker-service_plan).


## Event fields
{: #at_ev_fields}

A description of the common fields for an Activity Tracker event is on the [Event fields](/docs/activity-tracker?topic=activity-tracker-event) page.

## List of events
{: #at_list_ev}

The following table lists the events that get sent to Activity Tracker from {{site.data.keyword.dashdblong}} deployments:

| Action | Description |
|-------|-------|
| `<service_id>.backup-scheduled.create`| A scheduled backup of your deployment was created. If the backup failed, a "-failure" flag is included in the message. |
| `<service_id>.backup.create`| A backup of your deployment was created. If the backup failed, a "-failure" flag is included in the message. |
| `<service_id>.backup.restore`| A restore from backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.restore.start`| A restore from backup was created. If the attempted restore failed, a "-failure" flag is included in the message. |
| `<service_id>.user-password.update`| A user's password was updated. A "-failure" flag is included in the message if the attempt to update a user's password failed. |
| `<service_id>.user.create`| A user was created. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.user.delete`| A user was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.table.delete`| A table was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.token.create`| A token was created. A "-failure" flag is included in the message if the attempt to create a user failed. |
| `<service_id>.token.delete`| A token was deleted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.privilege.update`| A privilege was granted. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.privilege.revoke`| A privilege was revoked. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.database-connection.list`| Lists active database connections. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.database-connection.stop`| Terminates a database connection. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.lock.enable`| Locks a user account indefinitely. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.lock.disable`| Unlocks a user account. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.policy.list`| Lists available policies. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.policy.update`| A policy was updated. A "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.policy.delete`| A policy was deleted. "-failure" flag is included in the message if the attempt to delete a user failed. |
| `<service_id>.schema.create`| A schema was created. A "-failure" flag is included in the message if the attempt to delete a user failed. |

The `<service_id>` field indicates the type of {{site.data.keyword.databases-for}} deployment. For example, `dashdb` or `messages-for-rabbitmq`.
## Viewing events
You can access Activity Tracker with LogDNA through the **Observability** tab of your deployment's **Manage** page. The **Manage Activity Tracker** button links to the main list of all Activity Tracker instances in your {{site.data.keyword.cloud_notm}} account. Select the instance where you set your database logs to be forwarded. {{site.data.keyword.at_full_notm}} can have only one instance per location. Click **View Activity Tracker** to view the events.

After the event activity is forwarded to the service, each event can be expanded to a detailed view by clicking the arrow to the left of the time stamp.

The Activity Tracker with LogDNA service offers [searching](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step6), [filtering](/docs/log-analysis?topic=log-analysis-view_logs#view_logs_step5), and [export](/docs/log-analysis?topic=log-analysis-export#export) of events so you can customize retention for your use case. You can also use it to configure [alerts](/docs/log-analysis?topic=log-analysis-alerts).

## Database Auditing using Db2 Audit Facility 

You can monitor data access in your {{site.data.keyword.dashdblong}} instance with the built-in Db2 audit facility. This features provides database-level auditing in addition to the audit capability described earlier. Use the Db2 audit facility to generate and maintain an audit trail for a series of predefined database events, including attempts to access or manipulate database objects, user authentication, SQL statement execution, and even access to the audit log. Use the audit log to reveal usage patterns that would identify system misuse, and in turn, take action to eliminate such misuse.
{: shortdesc}

It is highly recommended that your COS bucket is configured in the same region and platform (IBM Cloud Object Storage or AWS S3) as your Db2WoC instance. {: Attention}

Before initial configuration, you must collect the following information:

**Note:** It is highly recommended that your COS bucket is configured in the same region and platform (IBM Cloud Object Storage or AWS S3) as your Db2WoC instance.

## Cloud Object Storage credentials

*IBM COS*

* [IBM Cloud Object Storage](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-uhc-hmac-credentials-main)
* The endpoint can be collected upon initial configuration or in the instance detail. See available [endpoints](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-endpoints). 


Example, 

    cos_hmac_keys:
      access_key_id:      7exampledonotusea6440da12685eee02
      secret_access_key:  8not8ed850cddbece407exampledonotuse43r2d2586


*AWS S3*

* [Amazon Simple Storage Service (S3)](https://docs.aws.amazon.com/IAM/latest/UserGuide/security-creds.html)
* The endpoint can be collected upon initial configuration or in the instance detail. See available [endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html).


Example,

		access key ID: AKIAIOSFODNN7EXAMPLE
		secret access key: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY

## Cloud Object Storage bucket name

You must create a bucket that will store the audit records. You will need to save the bucket name during initial configuration. It is recommended that you do not use this bucket for other purposes. Consider securely configuring the bucket with appropriate encryption, access management, and data retention.

For cost control measures, you should set a quota to the [relevant bucket](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-quota) and set an [expiration rule](https://cloud.ibm.com/docs/cloud-object-storage?topic=cloud-object-storage-expiry).

Once the audit records have been successfully uploaded to the cloud object storage bucket, you can preview the files in the Console. To review larger subsets of the audit logs, refer to [Audit Policy](https://www.ibm.com/docs/en/db2woc?topic=features-audit-policy-guidelines). The [format](https://www.ibm.com/docs/en/db2/11.5?topic=format-example-del-file) of the archived audit logs is DEL which separates the text with commas. You can reformat and process this file in your system for further analysis.

## Enable auditing 

In the updated auditing method, you will transition from maintaining audit tables to archiving audit logs in a Cloud Object Storage (COS) bucket. This change signifies a shift towards a more scalable and flexible approach to managing audit data.

To configure and manage auditing, you can now access the Audit tab within the IBM Cloud console. This centralized location allows for the creation, modification, and deletion of defined and active audit policies. By utilizing the Audit tab, you can efficiently oversee their auditing configurations and p### olicies.

One of the key benefits of this new method is the ability to preview audit files directly within the chosen COS bucket. This feature enables you to monitor their archived logs, ensuring that the data is being stored and organized as intended.

Additionally, you can continue to manage their audit policies using the SQL Editor, providing a familiar and powerful tool for fine-tuning and customizing their auditing configurations.

The automatic upload of audit logs to the COS bucket occurs in two scenarios:
* When the internal audit buffer reaches its maximum capacity.
* Approximately every 15 minutes, if there are records to be uploaded.

This new method ensures that audit logs are consistently and reliably stored in a scalable and easily accessible location, enhancing overall data management and compliance capabilities within the IBM Cloud environment.


### Enabling Database Auditing to Cloud Object Storage (COS) Bucket
1. **Create a Storage Alias**: Establish a storage alias for your COS bucket.
    1. **Navigate to Object Storage Aliases tab**: Access "Object Storage Aliases" tab under "Storage Objects" within the IBM Cloud console
    2. **Create Object Storage Alias**: Click “Create Object storage alias” to configure your COS bucket access information into a Db2 Storage Alias
    3. **Enter alias details**: Object Storage Alias name, endpoint type, endpoint URL of your bucket, S3 key ID and access key.
    4.  **Test connection to ensure details are valid**: Click “Test Connection” and click “Next”.
    5.  **Select COS bucket**: From the dropdown menu, choose the the bucket and click “Next”.
    6. **Review and Confirm**: Verify your settings and click “Connect” to finalize the configuration.
2. **Navigate to the Audit Tab**: Access the Audit tab within the IBM Cloud console.
3. **Initiate Audit**: Click "Enable Audit" to begin the process.
4. **Select Audit Tables Option**: Decide whether to Keep or Remove your existing AUDIT tables. It's advisable to migrate your audit data to the COS bucket prior to enabling audit through the console.
5. **Assign Storage Alias**: From the dropdown menu, choose the storage alias linked to your audit logs.
6. **Review and Confirm**: Verify your settings and click "Enable" to finalize the configuration.

### Configuring Audit Policies in IBM Cloud Database

To configure audit policies in your IBM Cloud database, follow the steps below based on your use case:

#### Policy Templates

To facilitate testing and prototyping of the auditing feature in your IBM Cloud database, the following policy templates are available:

**Audit a User Role**: This template is designed to monitor and log activities related to a specific user role. It captures events such as login attempts, data modifications, and privilege changes for the selected role.

**Audit All Logins**: This template provides a broad overview of all login activities within the database. It records successful and failed login attempts, user identities, and timestamps, enabling comprehensive tracking of access patterns.

**Audit Data Modification**: This template focuses on capturing changes made to the database's data. It logs events such as INSERT, UPDATE, and DELETE operations, along with the affected tables and records, offering insights into data manipulation activities.

These test/prototype policy templates are intended to help you evaluate the auditing feature's capabilities and tailor your configurations to meet your organization's specific needs. Once you have validated the feature's performance and suitability, you can transition to creating custom policies for production environments.

1. **Create Audit Policy**: Click "Create audit policy".
2. **Select Template**: From the dropdown menu, choose "Template".
3. **Enter Policy Name**: Input a name for your policy.
4. **Choose Template**: Select a policy template tile, such as "Audit a user role", "Audit all logins", or "Audit data modification".
5. **Activate Audit Policies**: Enable the defined policies by selecting the database entity (table, group, role, user, etc.) from the dropdown menu.
6. **Review and Confirm**: Verify your settings and click "Save" to finalize the configuration.

#### Custom-Defined Policies

When defining custom audit policies in your IBM Cloud database, it's essential to consider your specific use cases to control the size of data downloaded into the Cloud Object Storage (COS) bucket. By tailoring your policies to focus on critical events and entities, you can effectively manage the volume of audit data and optimize storage costs.

Here are some best practices for creating custom audit policies based on your use cases:

1. **Identify Critical Events**: Determine the events that are most relevant to your organization's compliance and security requirements. For example, if data privacy is a concern, prioritize auditing events related to data access, modification, or deletion.

2. **Select Relevant Entities**: Focus on the database entities (tables, users, groups, roles) that are most critical to your use cases. By narrowing the scope of audited entities, you can reduce the overall data volume and storage requirements.

3. **Configure Error Handling**: Decide whether to return or ignore audit errors based on your organization's needs. Choosing AUDIT will log errors, while NORMAL will suppress them, allowing you to control the amount of data generated.

4. **Set Appropriate Status**: For each audit category (BOTH, SUCCESS, FAILURE, NONE), select the status that best aligns with your use case. This helps ensure that you capture the necessary events without overwhelming your COS bucket with unnecessary data.

5. **Regularly Review and Adjust**: Periodically assess the performance and effectiveness of your custom policies. Make adjustments as needed to maintain an optimal balance between data coverage and storage efficiency.

By following these best practices, you can create custom audit policies that effectively address your use cases while controlling the size of data downloaded into the COS bucket. This approach ensures that your auditing configuration is both comprehensive and cost-effective.

1. **Create Audit Policy**: Click "Create audit policy".
2. **Select Custom**: From the dropdown menu, choose "Custom".
3. **Define Policy Details**:
    1. **Enter Policy Name**: Input a name for your policy.
    2. **Choose Error Type**: Specify whether audit errors are to be returned or ignored (AUDIT or NORMAL, respectively).
    3. **Choose Categories**: Click the switch for each category you want audited and select the corresponding Status (BOTH, SUCCESS, FAILURE, NONE). Click "Next".
4. **Activate Audit Policies**:
    1. **Enable Policy**: Click the switch to "Enable policy" and click "Select database entities".
    2. **Select Database Entities**: Choose each database entity tab (Tables, Users, Groups, Roles) and click each checkbox of the desired entity name.
5. **Review and Confirm**: Verify your settings and click "Save" to finalize the configuration.
6. **Validate Policies**: Click the "Policies" tab and review the audit policy list.

#### Configure Policy with SQL Editor
Alternatively, you can use the SQL editor to define and activate policies. This method allows you to configure policies for any available database entity. For detailed guidance, refer to the [Audit policy guidelines](https://www.ibm.com/support/knowledgecenter/SS6NHC/com.ibm.swg.im.dashdb.security.doc/doc/audit_policy_guidelines.html).

By following these steps, you can effectively configure audit policies in your IBM Cloud database, ensuring comprehensive monitoring and compliance with your organization's requirements.
