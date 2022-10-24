# Azure Firewall
Managed, cloud-based net security service to protect VNet resources. Centrally create, enforce & log
app and net connectivity policies across subs and VNets.
- Stateful
- Buit-in HA, unrestricted cloud scalability (span multiple AZs).
- App Fully Qualified Domain Names (FQDN) filtering rules
- Threat intelligence

It uses a static public IP address for your VNet resources to let know you to outside firewalls. 
Fully integrated with Azure Monitor (logging & analytics).

## [Hub-Spoke Network](https://learn.microsoft.com/en-us/training/modules/configure-azure-firewall/3-create-azure-firewalls)
- Hub is a VNet that acts as a central point of connectivity.
- **Spokes**: VNets to peer with the hub (isolate workloads)

![Hub-Spoke Network Topology](img/hub-spoke.png)

## [Rules](https://learn.microsoft.com/en-us/training/modules/configure-azure-firewall/4-create-firewall-rules)

### NAT Rules
Translate firewall public IP and port to private.
Config:
- Name: label
- Protocol (TCP/UDP)
- Source Address (Internet, CIDR block, internet address)
- Destination Address
- Destination Ports
- Translated Address
- Translated Ports

### Network Rules
Any Non-HTTP/S. 
- Name
- Protocol (TCP, UDP, ICMP, *)
- Source Address 
- Destination Address
- Destination Ports

### Application Rules
Define FQDN.
- Name
- Protocol:Port -> HTPP/HTTPS
- Source Address 
- Target FQDNs (DNS)