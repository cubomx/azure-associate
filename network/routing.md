# Network routing & endpoints
Azure implements **system routes** to direct network traffic:
- VMs in the same subnet
- VMs in the same VNet, diff subnet
- Data flow from VMs to the Internet

## User-defined routes
Control net traffic by:
- Defining routes that specify the next hop of the traffic flow
    - VNet Gateway
    - VNet
    - Internet
    - Virtual Appliance

Route tables can be associate to any quantity of subnets.
Traffic routed to the None next hop type isn't routed outside the subnet, but is dropped.

## [Service endpoints](https://learn.microsoft.com/en-us/training/modules/configure-network-routing-endpoints/4-determine-service-endpoint-uses)
Use VNet private addresses as the source IP addresses when accessing the Azure service from a VNet.

Benefits:
- Remove public Internet access (security)
- Optimal routing
- Keep traffic on the Azure backbone network.
- No extra overhead to maintaining the endpoints.

### Services
- Azure AD
- Cosmos DB
- Cognitive Services
- Container Registry
- Event Hub
- Key Vault
- Service Bus
- SQL
- Storage
- Web

## Private Link
Private connectivity from a VNet to Azure PaaS, customer-owned, or Microsoft partner services.
Works across Azure Active Directory (Azure AD) tenants. Bring services delivered on Azure into your 
private virtual network by mapping it to a private endpoint.
- Private, global.
- Integration with on-premises and peered networks
- Protection against data exfiltration for Azure resource
- Services delivered directly to your customers’ virtual networks.