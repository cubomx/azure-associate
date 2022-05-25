# Configure Virtual Machine Availability

## Plan
**Unplanned Hardware Maintenance**: Azure predits a failure on physical machine. Uses Live Migration to migrate VMs to a healthy one.
**Unexpected Downtime**: hardware or physical infra fails unexpectedly. Azure platform automatically 
migrates your VM to a healthy physical machine.
**Planned Maintenance**: periodic updates made by Microsoft to improve reliability, perfomance, and security.

## Setup Availability sets
Group of related VMs deployed that should perform an identical set of functionalities and have the same 
software. Across physical servers, compute racks, storage units, and network switches. 

SLAs:
- 2+ instances acrosss 2+ availability zones in the same region: 99.99%
- 2+ instances in the same avialbility set: 99.95%
- Using Premium Storage, all OS & Data Disks: 99.9

## Update & Fault domains
**Update domain** group of nodes that are upgraded together during a rollout. Contains a set of VMs & 
associated physical hardware, updated & rebooted at the same time. Default: 5, up to 20. Only 1 domain is 
reboote at a time in a planned maintenace.

**Fault domain** group of nodes that represent a physical unit of failure. They share a single point of failure.
Node belonging to the same physical rack.

## Availability zones
In an Azure region, is a combination of a fault domain and update domain. It protects from datacenter failures.
They are *unique physical locations* within an Azure region. Each zone is made up of 1+ datacenters equipped
with independent power, cooling, and net. For resiliency, min of 3 separate zones. Zone-redudant replicates
your apps. It offers 99.99% VM uptime SLA. Two offerings:
- **Zonal services**: pins the resource to a specific zone.
- **Zone-redudant services**: replicates across zones.

## Scaling
**Vertical** (scale up/down): increasing/decreasing VM sizes in response to a workload. Make VM more/less
powerful. More limitations due to availability or having to stop and restart.

**Horizontal** (scale out/in): # of VMs is altered depending on the workload.

## Scale sets
Deploy and manage a set of identical VMs. True autoscale. *NO pre-provisioning* required. Created from the 
same base OS image & configuration. No additional management. Run multiple instances of your app. 
Automatically scaling. Up to 1000 instances; custom images up to 600.

Parameter:
- instance count
- instance size
- spot instance (reduce cost of Azure compute excess)
- use manage disks
- scaling beyond 100 (if yes, more than 1 placement)
- spreading algorithm

## Autoscale
- Adjust according to performance thresholds
- schedule autoscaling
- reduces monitoring