# Azure Container Instances
Features:
- **Persistent storage** with Azure File Shares
- Custom Sizes
- IP address and FQDN
- Linux & WinD
- Isolated

Managed service, serverless.

## Container group
Collection of containers that get scheduled on the same host machine. They share
- Lifecycle
- Resources
- Local net
- Storage volumes

Aggregated allocation.

### Deploymen option
- ARM template (to deploy additional Azure resources)
- YAML (Only container instances)

--------

# Azure Kubernetes Service

## Architecture
**Azure-managed node**: K8s core services

An AKS cluster **contains 1+ Nodes** (VMs)to run K8s node components & container runtime:
- **kubelet**: processes the orchestration requests and scheduling of containers
- **kubeproxy**: handles VNet; routes traffic & manages IP addressing
- **container runtime**: allows the container to run & interact with add resources (VNet/Storage)

## Networking
### Services
- **Cluster IP**: internal IP address
- **NodePort**: port mapping 
- **LoadBalancer**
- **ExternalName**: DNS

### Pods
- Logical
- Ephemeral

Usually deployed & managed by K8s controllers.

## Storage
- **Volumes**: store and retrieve data.
    - **Azure Disks**: RWOnce, K8s DataDisk resource
    - **Azure Files**: SMB 3.O share (Azure SA)

- **PersistentVolume**: exist beyond the lifetime of an individual pod. Can be dynamically created by the
K8s API server.


### Storage Classes
- **default**: Azure StdSSD. Deleted storage on termination.
- **managed-premium**: Azure Premium storage. Deleted storage on termination.
- **azurefile**: Azure File Share...
- **azurefile-premium** Premium Storage for Azure File Share...

### PersistentVolumeClaim
Specify the storageclass, access mode, size. Bound to a PersistentVolume.

## Scaling
- Manually
- Monitor with the **Horizontal Pod Scaler (HPA)**. It checks the *Metrics API* every 30 secs. (K8s 1.8+). Min, Max of replicas.
    - You can set an amount of time between 2 scale events. Default, scale up is 3 mins & scale down
    is 5 mins.
- **Cluster autoscaler**: checks every 10 secs the API server. Adjust based on the requested 
compute resources. Works with RBAC (K8s 1.10x+)
    - If large demand, you can scale with virtual nodes and Azure Container instances.
        - With this, you avoid the infra overhead.
        - ACI will become a virtual K8s node.
        - The Virtual Kubelet is installed in the cluster.
        - Work in the same VNet, another subnet.
    - If after 10 mins a node is not required, it is scheduled to deletion.