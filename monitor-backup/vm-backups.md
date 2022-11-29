# Virtual Machine backups
- **Azure Backup**: running prod workloads. App-consistent backup (Linux/WinD). GRS. Restore all or specific 
files.
- **Azure Site Recovery**: Recover with a click in matter of mins. Protect from major disaster scenario to a 
region.
- **Managed disk snapshots**: for dev/test envs. Quick & simple. Read-only full copy of a managed disk (stored 
as a std managed disk by default). Backup at any point in time. Exist independent. Billed based on the used 
size. No good if it needs to coordinate with another disk.
- **Images** (also uses managed disks): Create a image from your custom VHD in a Storage account or generalized
VM. Contains all disk (OS, data).

## Create snapshots
Process of an Azure backup job:
- VM snapshot take
- VM snapshot transfer to Recovery Services vault.

Recovery point is "snapshot" in the time between the taking of the snapshot and the submission of it. Then, it
wil be marked as "snapshot and vault".

To consider:
- Can be used before is transfer the snapshot.
- Fast: store locally (1 to 5 days, default 2)
- Disk sizes up to 32 TB (Not recommended resizing)
- Support Std SSD, Std HDD, Premium SSD
- Incremental snaps stored as page blobs

## Azure Backup Server
Use a Data Protection Manager (DPM) or Microsoft Azure Backup Server (MABS). Specialized workloads (SharePoint, 
Exchange, SQL Server).

Benefits:
- App-aware backups optimized for common apps.
- You don't need to install the MARS agent on each machine. Each machine runs the DPM/MABS protection agent.
MARS runs on the MABS/DPM only.
- + flexibility & granular scheduling options
- Multiple machines

Steps:
1. Install the DPM or MABS protection agent on machines. Add them to the DPM protection group.
2. If on-premises, DPMS/MABS server must be on-premises
3. If Azure located, on Azure the server.
4. You can protect backup volumes, shares, files and folders. Protect a machine's system state (bare metal).
5. You select to back up to the MARS/DPM local disk for short-term and Azure for online protection.
6. Disk is backed up.
7. 

## MARS vs. MABS
| Component | Benefits | Limits | What is protected? | Where stored? |
| --------- | -------- | ------ | ------------------ | ------------- |
| Azure Backup (MARS) agent |  No separate server; physical & virtual WinD OS | 3x backup/day, not app aware, no Linux, fileDirVol only types | Files & folders | Recovery Services vault |
| Azure Backup Server (MABS) | App aware, + flex, granularity, Hyper-V, VMWare, not System Center license |Not Oracle, no tape backup, req. live Azure sub | Files, folders, volumes, VMs, apps, workloads | RS vault, locally attached disk |

## Soft delete
(For blob objects). When data is erroneously modified/deleted. To delete you need to stop the backup. Preserve 
for 14 additional day (a **red soft delete** icon appears next to it, Vault cannot be deleted). To restore, you 
need to undelete it. 

## Azure Site Recovery
Keep business apps & workloads running during outages. Replicates workloads running on physical/virtual machines
from a primary site to a secondary (failover). If primary is OK, you can fall back to it.

Features:
- Manage replication, failover, fallback (use Portal)
- Reduce cost of maintaining
- Orchestrate replication without intercepting app data.
- Azure VMS, VMWare VMS, replication freq (low as 30secs)
- Can use recovery points with app-consistent snaps.
- Run planned failovers for expected outages. 
- Integrates with networking (IPs, LBs, Azure Traffic Manager for net switchoves)