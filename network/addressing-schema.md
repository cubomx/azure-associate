# Addressing schema
Non-routable IP addresses (internal), you have full control of:
- 10.0.0.0 to 10.255.255.255
- 172.16.0.0 to 172.31.255.255
- 192.168.0.0 to 192.168.255.255

It all depends on the Classless Inter-Domain Routing (CIDR). 

Improved isolation if you deploy:
- Network Security Groups
- Firewall (+ capabilites at network and app layer filtering)

By default, all subnets can communicate. Smallest subnet is /29. Largest is /2.

[Subnet cheatsheet](https://www.freecodecamp.org/news/subnet-cheat-sheet-24-subnet-mask-30-26-27-29-and-other-ip-address-cidr-network-references/)

## Public IP
- **Dynamic**: change over lifespan. Create or start a VM, when is stopped or deleted. Default.
- **Static**: Released only when deleted the resource or changed the allocation method.

SKUs (both have default in originated flow idle timeout of 4 mins, up to 30 & fixed out originiated flow idle
timeout of 4 mins):
- **Basic**: open, only for inbound traffic, using meta data service (IMDS), no support for AZs neither routing
preferences.
- **Standard**: use static allocation, closed to inbound, zone-redudant (optional zonal), routing preference, 
can be used as anycast frontend IPs for cross-region LBs.

### Address prefix
A reserved, static range of public IP addresses assigned from a pool of available addresses unique to a region.

## Private IP
Can be:
- Dynamic (DHCP lease)
- Static (DHCP reservation). Persist even if the resource is stopped or deallocated.

## Azure
For all subnets, first 3 addresses are reserved by default. Also, the first & last for protocol conformance.
The number of possible addresses on an Azure subnet is (2^n)-5, where n represents the number of host bits.