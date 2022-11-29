# Azure DNS
Host your DNS records for your domains on Azure infra. Name resolution.

## What is DNS?
Domain Name System, protocol within the TCP/IP std. Translate human-readable domain names to a known IP address.
It uses a global directory on servers around the world.

Functions: 
- **Local cache**: of recently accesed or used DN & their addresses (faster response). If doesn't match the 
request, it will pass it to another DNS server. Finally, it will return *domain cannot be found* error.
- **KV pair DB** of IP addresses and any host/subdomain over which the DNS server has authority.

## Domain Name
You have a domain name `domainname.onmicrosoft.com`. It cannot be deleted. You can create a custom 
one and route them. You must be a *global administrator*. The custom domain name must be added to 
the directory and verified before. It can be:
- MX (Mail Exhange). Maps mail requests to your mail server.
- TXT (Text). Associaye test strings with a DN.

## IPs
IPv4 -> 4 sets of numbers (0 to 255).
IPv6 -> 8 groups of hexadecimal numbers separated by a colon: "fe80:11a1:ac15:e9gf:e884:edb0:ddee:fea3"

## Azure DNS Zone
Hosts the DNS records for a domain. It must be:
- Name: unique within the RG
- If shared name, different name server addresses
- Root/parent domain is registered at the registrar & pointed to Azure DNS
- Child domains are registered in AzureDNS directly.

## Delegate DNS domains
Each time a DNS zone is created Azure DNS allocates names servers from a pool. Once assigned, 
Azure DNS auto-creates authoritative NS records in your zone.

You must replace the registrar NS records with the ones from your Azure DNS zone.

## DNS record sets
Collection of records in a zone (same name & type). Allows for multiple resources to be defined in a single 
record.
- *CNAME* can only contain 1 record. Alias from 1 DN to another.
- *A*: host record. 
- Wildcards
- CAA (Certificate authority)
- NS (name server)
- SOA (Start of Authority). Only 1 record as CNAME. Azure DNS is one of this.
- SPF (Sender Policy Framework)
- SRV (Server Localtions)

SOA & NS records created by default in Azure DNS.

## Apex Domain
Highest level of your domain. Root apex. Represented by the @ symbol in the DNS zone records.

### Alias records
Enable a zone apex domain to reference other Azure resources from the DNS zone. Also, route all traffic through
Traffic Manager. Lifecylce tracking of target resources.
- Traffic Manager profile
- Azure CDN endpoints
- Public IP resource
- Front door profile

Use for: LBs, auto update DNS record.

## [Private DNS zones](https://learn.microsoft.com/en-us/training/modules/configure-azure-dns/7-plan-for-private-dns-zones)
Benefits:
- Use Azure infra
- All common types: A, AAAA, CNAME, MX, PTR, SOA, SRV, and TXT records
- Automatic hostname record management
- Hostname resolution between virtual network (shared)
- Split-horizon DNS support (can have the dame DN in both private and public zones)
- All Azure regions

- You could use name resolution for things within a VNet without having to create a custom DNS solution. 
- You need
to specify which VNets are allowed to resolve records within the zone. 
- Auto-maintained.


## Benefits
- Improved security
    - RBAC
    - Activity of logs
    - Resource locking
- Ease of use
- Alias record sets
    - Point to an Azure resource.
        - A
        - AAAA
        - CNAME
- Private DNS domains