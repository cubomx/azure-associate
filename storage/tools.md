# Storage with tools

## Azure Storage Explorer
Standalone app to work with Azure Storage data (Win, Mac, Linux). Access to multiple accounts and 
manage all your storage content. It requires:
- Management permissions (ARM)
- Data layer permissions

You need Azure AD permissions.

Used to connect to different storage accounts:
- To SA associated with your Azure subscriptions
- To SA & Services that are shared from other Azure subscriptions
- To & Manage local storage by using the Azure Storage Emulator

Work globally and natinal:
- **Connect to an Azure subscription**: manage storage resources of an Azure subscription
- **Work with local development storage**: use Azure Storage Emulator
- **Attach to external storage**: that belong to another subscription ot under national Azure clouds.
- **Attach a SA by using a SAS**
- **Attach a service by using a SAS**
- **Connect to an Azure Cosmos DB by using a connection string**

To create the connection, you need:
- Account name
- Account key

## Import/Export service
**Azure Import/Export** to securely import large amounts of data to *Azure Blob storage* & *Azure Files* by
shipping disk drives to an Azure datacenter. Also, viceversa.

Usage cases:
- **Migrating data to the cloud** quickly and cost effectively
- **Content distribution** quickly send data to your customer sites
- **Backup** of your on-premises data
- **Data recovery** recover blob storage and deliver to on-premises

Import:
1. Create an Azure Storage account
2. Identify # of disks needed to accommodate all the data
3. Identify a computer to perform the data copy, attach physical disks that you will ship and install
the WAImportExport tool.
4. Run the tool to copy the data, encrypt the drive with *BitLocker*, generate journal files
5. Use the Portal to create the job refering the ASA. Specify the destination address.
6. Ship to the destination and update the job by providing the shipment tracking #
7. Azure staff will carry out data copy

Export:
1. Identify the data
2. Identify the # of disks that you will need
3. Use the Portal to create the job 
4. Ship the disks to the Azure region hosting the SA
5. Data will be copy to the disks and send back to you

**WAImportExport** is the drive preparation & repair tool for this. You can:
- Copy data to the HDs
- After an import job, you can repair any blob 
- After received drives from a export job, you can repair any files on the drives

Use of SATA II/III HDDs/SSDs.


## AzCopy
Cmd-line utility for copying data to/from Microsoft Azure Blob & File storage. High-perfomance reliable data
transfers. Copy between storage accounts or between a File systema a SA.

New features:
- Supports Azure Data Lake Storage  Gen2 APIs
- Supports copying an entire account (Blob service only)
- Account-Account copy using new PUT.
- List/Remove files & blobs in a given path
- Supports wildcard patterns in a path
- **Improved resiliency** every instance will create a job order & a related log file.

Authentication options:
- **Azure AD** (Blob & ADLS Gen2 services). Role should be *Storage Blob Data Contributor*.
- **SAS tokens** (Blob & File services). Append the SAS token to the blob path on the cmd.