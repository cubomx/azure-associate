# Configure Virtual Machines

## IaaS business scenarios
- Quick testing & development. Scaling,
- Website hosting: less expensive than web hosting
- Sinplify and reduce costs of storage management. Handling demand.
- High-perfomance computing.
- Big data analysis
- Extend Datacenter; add capacity to your datacenter.

## Plan VMs
1. Network: used to provide private connectivity between Azure VMs and other Azure services. By default, 
services outisde the VNet cannot connect to services within the VNet. **Consider topology**

2. Name: meaningful & consistent. 
    - Environment: dev, prod, QA
    - Location: uw (US West), ue (US East)
    - Instance: 01, 02
    - Product/Service: service
    - Role: sql, web, messaging

3. Location: locate your VMs as close as possible to your users.
    - Location limitations: hardware or configuration
    - Prices
4. Size

5. Pricing model:
    - Size / OS
    - Compute:
        - Consumption-based:
        - Reserved VM Instances: purchase for 1 to 3 years. Savings up to 72%

6. Storage: it is separate from VM uses. Even deallocated, storage has a price.

7. OS

## VM sizing
- **General purpose**: balanced CPU-to-memory ratio. (Test/Dev)
- **Compute optimized**: high CPU-to-memory ratio. (Med traffic web)
- **Memory optimized**: high memory-to-CPU ratio. RDB, large caches, in-memory analytics.
- **Storage optimized**: high disk throughput & I/O ideal for Big Data, SQL, NoSQL DBs, data warehouse, 
transactional
- **GPU**: graphic rendering, video editing. Machine learning.
- **High perfomance compute**: RDMA, most powerful CPU

You can resize whenever you want. It may require to restart.

## VM storage
At least 2 disks (VHDs):
- OS disk (preinstalled & selected)
- Temporary disk: data may be lost so, don't put critical data
- Data disks (managed): attached to VM; store app data or data you want to persist 

### Options
**Azure Premium Storage**: SSD, intensive workloads
    - Unmanaged: you manage the SA. VHD files stored as page blobs
    - Managed: it is an abstractiom over page blobs, blob containers, and SAs.

## Connect to VMS
- WinD: Remote Desktop Protocol (RDP).
    - RDP: GUI, port 3389
    - Windows Remote Management (WinRM): establish a cmd-line session (port 5986)
- Linux: SSH, serial port
- Bastion: fully platform-managed PaaS service (provisioned inside your VNet). RDP/SSH. Connectivity over 
SSL. You don't need a public IP address.
