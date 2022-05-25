# Azure Files & Azure file sync

## Compare Files to Blobs
**File storage** offers *shared* storage for apps using the **SMB protocol**.

Common uses:
- **Replace** traditional on-premises file servers or NAS devices
- **Access anywhere**: any popular OS can mount
- **Lift & Shift** 
- **Azure File Sync**: shares can be replicated to Windows Servers (performance & catching of the
data)
- **Shared apps**: store shared settings
- **Diagnostic data**: logs, metrics, and crash dumps.
- **Tools & Utilities**: storing them for developing/administering VMs or cloud services.


| Feature | Description | When to use |
| ------- | ----------- | ----------- |
| Azure Files | SMB interface, client libraries, REST interface to allow access anywhere to  stored files | Shared data between applications, store tools to be accesed from many VMs |
| Azure Blobs | Client libraries, REST interface to allow unstructured data to be accesed at massive scale in block blobs | Support streaming & random access scenarios. Access app data from anywhere |

It communicates over TCP port 445. Azure file shares can be mounted in Linux distros using the *CIFS kernel client*; it can be on-demand (mounted at `/etc/fstab`).

**Secure transfer**: allow only requests by secure connection.

## File Share snapshots
Capture a point-in-time, read-only copy of your data, at the file share level. You need to delete all the 
share snapshots first to delete the share. The are incremental: each snapshot is going to store the 
difference between the new and the last snapshot.

When?
- Protect against app error & data corruption.
- Protect against accidental deletions/unintended changes.
- General backup purposes

## File Sync
Centralize your file shares. It transforms Windows Server into a *quick cache* of your **Azure file share**.
Protocols available: SMB, NFS, FTPS.
- **Lift & Shift**: write access to the same data across Windows Servers and Azur Files.
- **Branch offices**: backup files, setup a new server that will connect to Azure
- **Backup and Disaster Recovery**: once implemented, *Azure Backup* will back up your on-premises data.
- **File archiving**: recently accesed data is located on local servers. Non-used moves to *Cloud Tiering*.

**Cloud Tiering** (optional) files that aren't frequently accesed are tiered to Azure Files. Locally, it will be 
replaced with a pointer. It is URL to the file.

## File Sync components
**Storage Sync Service** top-level resource. It is peer of the storage account resource. It is required to create
sync relationships with multiple storage accounts via *multiple sync groups*.

**Sync group** defines the sync topology for a set of files. Endpoints within are kept in sync with each
other.

**Registered server** an objects that represents a *trust relationship* betweem your server (or cluster)
and the Storage Sync Service.

**Azure File Sync agent** it is a downloadable package that enables WinD Server to be synced with an 
Azure file share. Three componets
- *FileSyncSv.exe*: fg WinD service responsible for monitoring changes and initiating sync sessions.
- *StorageSync.sys*: system filter; tiering files to Azure Files
- *PowerShell management cmdlets*: use to interact with *Microsoft.StorageSync* Azure resource provider

**Server endpoint** specific location on a registered server (e.g. folder). Namespaces cannot overlap. 

**Cloud endpoint** Azure file share that is part of a sync group (unique).

## Deploy
Steps:
1. **Deploy the Storage Sync Service**: Name, Subscription, Resource Group, Location.
2. **Prepare WinD Server to use with Azure File Sync**
3. **Install the Azure File Sync Agent**
4. **Register WinD Server**: Subscription ID, Resource Group, Storage Sync Service