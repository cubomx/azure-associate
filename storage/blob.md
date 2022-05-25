# Blob Storage
**Azure Blob storage** is a service for storing large amounts of unstructured object data, such as text or binary data. 

Uses:
- Serving images/docs to browser
- Distributed access of files
- Streaming
- Backup
- Data for analysis

Hierarchy:
- Storage Account
- Containers in the storage account
- Blobs in a container

## Container
- Name
    - Lowercae letters
    - Numbers
    - Hyphens
    - Begin with a letter/number
    - 3-63 chars long

- Public access level:
    - **Private** (default): 
    - **Blob**: anon public read access for blobs only.
    - **Container**: anon public read access to the entire container 

## Access tiers
- **Hot (default)**: frequent access.
- **Cool**: storing large amounts of data stored by at leat 30 days. Accesing is more expensive than Hot tier.
- **Archive**: several hours of retrieval latency; remain for at least 180 days. Accesing more expensive than 
the other options.

## Blob lifecycle management rules
Data it will become idle with time. You can create policies to change the tier or delete files:
- Transition blobs to acooler storage tier.
- Delete blobs at the end of their lifecyles.
- Define rules to be run once per day at the SA level.
- Apply rules to containers or a subset of blobs

## Determine blob object replication
Why?
- Minimizing latency; take data closer to other clients.
- Increase effiency for compute workloads: compute the same in different regions
- Optimizing data distro: Replicate the results of processed data.
- Optimizing costs: after replicating, you can move it to a cooler tier.

Things to consider:
- Versioning is enabled (src/dest)
- Snapshots are not replicated
- Available in hot/cool tier
- When replicating, you create a policy. It includes 1+ rules that specifies a src container
and a dest, indicating which blobs to replicate.

## Types of blobs
- **Block(default)**: blocks of data assembled. Storing files, images, and videos.
- **Append**: made up of blocks, but optimized for append operations (loggin scenarios).
- **Page blobs**: up to 8TB, more effiecient RW operations. OS/data disks.

## Upload tools
- **AzCopy** cmd tool for Windows/Linux.
- **Azure Storage Data Movement library** .NET for moving data between Azure Storage services.
- **Azure Data Factory**: copying data to/from Blob by using the account key, SAS, service principal,
managed indentities.
- **Blobfuse** virtual File System driver.  Access your exiting block blob data through the Linux
file system.
- **Azure Data Box Disk** service for transferring on-premises data over where large amounts/network constraints. Request SSD to Microsoft. 
Copy your data to those disks and ship them back to Microsoft.
- **Azure Import/Export** service similar to he previous, just HDD.

## Storage Pricing
- **Perfomance tiers**: amount of data and the cost of storing.
- **Data access costs**: it increases as the tier goes cooler (charge per-GB data access).
- **Transaction costs**: charges increases as the tier gets coolder. Charge per-transaction.
- **Geo-replication data transfer costs**: per-GB charge.
- **Outboud data transfer costs**: bandwidth usage on a per-GB basis. General purpose storage accounts.
- **Changing the storage tier**: charges by reading all the data existing (cool-hot). The other way is only available in GPv2 accounts, the charge is equal to
writing all the data in the cool tier. 