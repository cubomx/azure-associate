# [Azure Backup](https://learn.microsoft.com/en-us/training/modules/configure-file-folder-backups/2-describe-azure-backup-benefits)
Back up & restore your data in Azure. Reliable, secure, cost-competitive. Many offerings (agents) to download 
and deploy in your infrastructure. All Azure Backup components can be used to back up data to a Recovery 
Services vault in Azure. [Benefits](https://learn.microsoft.com/en-us/training/modules/configure-file-folder-backups/2-describe-azure-backup-benefits)
- **+Easy** to implement on-premises.
- **Isolated** backups. (You can backup Azure VMs)
- **Unlimited data transfer**. No limit on in/out transfer, or cost for data that is been transfered.
- **Data secure**. Encryption (key or passphrase)
- **App-consistent**. All required data to restore the backup copy.
- **Short/Long data retain**. Up to 9999 recovery points to any time.
- **Auto-management of storage**. You can store a part of backups on-premises and Azure will handle this.
- **Multiple storage options**:
    - *LRS*: 3 replicas in a storage scale unit in a DC.
    - *GRS*: default. Replicates to a secondary region. Higher level of durability.

## Azure Backup center
Single unified management experience to *govern, monitor, operate, and analyze backups* at scale.
- Manage backups spanning multiple workload types, vaults, subs, regions, and tenants.
- **Datasource-centric management**: provides views & filters to things like VMs & DBs (sub, tags, resource 
group)
- Integration with:
    - Azure Policy (govern)
    - Azure workbook & Azure Monitor Logs (view detailed reports)

Supported:
- Azure VM backup
- SQL in Azure VM backup
- SAP HANA in Azure VM backup
- Azure Files backup
- Azure Blobs backup
- Azure-managed disks backup
- Azure DB for PostgreSQL Servr backup

## Recovery Services vault
Storage entity in Azure that stores data. Makes easy to organize backup data. Stores backups for many services:
- IaaS VMs
- Azure SQL DBs

Can be used to backup:
- Azure file shares
- On-premises files & folders (Hyper-V, VMware, System State, Bare Metal Recovery)

Supports:
- System Center DPM
- WinD Server
- Azure Backup Server

*You can create up to 500 Recovery Services vaults per region*.

## On-premises process
1. *Create the Recovery services vault*
2. *Download the agent & credentials file*
3. *Install & register agent*
4. *Configure the backup*. Use the agent to create a backup policy (when, what to, how to, settings)


### Manage agent
It relies on the Microsoft Azure Recovery Services agent to be installed on the client/server. Features:
- Backup on physical or virtual WinD OS
- No separate backup server required
- App agnostic
- Backup & restore content