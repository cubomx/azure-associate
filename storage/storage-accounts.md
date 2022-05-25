# Storage

## Storage Accounts
**Azure Storage** Microsoft's *cloud storage solution*. You can store files, messages, tables
, and others. Offers:
- A massively scable object store for data objects
- File system service for the cloud
- Messaging store for reliable messaging
- NoSQL store

Properties:
- **Durable & highly available**: redudancy; replicate data across datacenters or geographical
regions.
- **Secure**: encrypted by the service. Fine-grained control over who has access.
- **Scalable**
- **Managed**: Microsoft handles hardware, and critical issues
- **Accesible**: accesible over HTTP/HTTPS. Many SDKs available. Supports scripting. Azure portal
& Azure Storage Explorer offer easy visual solutions.

Divided into 3 categories:
- **Storage for VMS**: 
    - **Disks** (persistent block storage)
    - **Azure Files** (fully managed file shares). Used the Server Message Block (SMB); multiple VMs can share the same files. Use of REST. Access through URL, includes a shared access signature (SAS)
    token
- **Unstructured Data**: 
    - **Blob**: highly scalbale, REST-based. Ideal for: serving images/docs to a browser,
    distributed files, streaming, backup, data for analysis.
    - **Data Lake Store**: Hadoop Distributed File System as a service
- **Structured Data**: 
    - **Tables**: key/value, autoscaling NoSQL. Now part of Cosmos DB: Azure Cosmos DB Table API,
    optimized tables, global distribution, automatic secondary indexes. Ideal for non-relational data.
    - **Cosmo DB**: globally distributed DB service
    - **Azure SQL DB**: fully managed DBaaS built on SQL

Others:
- **Queue Storage**: store & retrieve messages; up to 64KB per message. Can contain millions. Used to be
processed asynchronously.

Tiers of storage accounts:
- **Standard**: HDD. Bulk storage or data infrequently accesed
- **Premium**: SSD. VM disks with intensive I/O. Low-latency.

## Types of Storage Account
| Storage Account | Recommendend usage |
| --------------- | ------------------ |
| Std general-purpose v2 | Blob, File, Queue, Tale, Data Lake Storage (most scenarios) |
| Premium block blobs | High transactions rates, smaller objects or low storage latency |
| Premium file shares | Enteprise/High-perfomance share apps |
| Premium page blobs | Premium high-performance |

All Storage Accounts are *encrypted* using **Storage Service Encryption** (SSE) for data *at rest*.

## Replication Strategies
Your data in *Azure Storage* is always **replicated** (durability, high availability).

|   | LRS | ZRS | GRS/RA-GRS | GZRS/RA-GZRS |
| - | --- | --- | ---------- | ------------ |
| Node unavailability withih a DC | Yes | Yes | Yes | Yes |
| An entire DC becomes unavailable | No | Yes | Yes | Yes |
| A region-wide outage | No | No | Yes | Yes |
| Read access to your data (geo-replicated region) when a region-wide unavailabiltiy | No | No | Yes (RA-GRS) | Yes (RA-GZRS) |
| Storage Account types | GPv1, GPv2, Blob | GPv2 | GPv1, GPv2, Blob | GPv2 |

**ZRS** replicates you data across 3 storage clusters in a single region. Each one has its own availability zone.

**GRS** replicates your data to a secondary region (using LRS within that region). Durability even if there is a **regional outage**. Provide 99.99999999999999% (16 9's) durability. You cannot read the data from the secondary region (only if the first fails). If you want this, you must select **RA-GRS**.

**GZRS** high availabiltiy of ZRS with protection from region outages as providded by GRS. Replicated across 3 Azure availability zones in the primary region and also replicated to a secondary geographic region.

## Access Storage
Endpoints:
- Container: `<StorageAccountName>.blob.core.windows.net`
- Table: `<StorageAccountName>.table.core.windows.net`
- Queue: `<StorageAccountName>.queue.core.windows.net`
- File: `<StorageAccountName>.file.core.windows.net`

Accesing a object: `<StorageAccountName>.<Type>.core.windows.net/<Location>` where **\<Location>** is something like `mycontainer/myblob`.

### Configure a custom domain
- Direct CNAME mapping: create a CNAME record that points from your URL to the Azure Storage Account:
    `blobs.contoso.con -> contosoblobs.blob.core.windows.net` 
- Intermediary mapping with asverify: prepending your domain with *asverify*, you don't modify the DNS record.

### Secure storage endpoints
You should use the **Firewalls and virtual networks** blade to add VNets that will have access. Allow access to 1+ public IP ranges.
- Subnets & Vnets must exist in the same Azure Region/Region Pair as the Storage Account.