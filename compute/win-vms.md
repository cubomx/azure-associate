# Windows Virtual Machines

## Compute
You can choose from general purpose to massive computing tasks.

## Storage
2 types of disks:
- Hard Disk
- Solid State Drive (Std, Premium)

They use virtual disks (VHDs). Work like page blobs in an Azure Storage account. Default 2 disks:
- **OS Disk**: max to 2048 GB. (C:)
- **Temporary disk**: Windows paging file (D:)

You can create additional disks for data wih 32,767 gibibytes (GiB) maximum capacity.

Types:
- **Unmanaged**: responsible for Storage accounts (rate limit of 20,000 I/O operations/sec.)
- **Managed**: you only specify the type and size