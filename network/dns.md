# Azure DNS
Host your DNS records for your domains on Azure infra.

## Domain Name
You have a domain name `domainname.onmicrosoft.com`. It cannot be deleted. You can create a custom 
one and route them. You must be a *global administrator*. The custom domain name must be added to 
the directory and verified before. It can be:
- MX
- TXT

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
Collection of records in a zone (same name & type).
- *CNAME* can only contain 1 record

## [Private DNS zones](https://learn.microsoft.com/en-us/training/modules/configure-azure-dns/7-plan-for-private-dns-zones)
Benefits:
- Use Azure infra
- All common types: A, AAAA, CNAME, MX, PTR, SOA, SRV, and TXT records
- Automatic hostname record management
- Hostname resolution between virtual network (shared)
- Split-horizon DNS support
- All Azure regions
