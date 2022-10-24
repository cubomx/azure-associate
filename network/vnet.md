# Virtual Networks
Logical isolation.
- **Dedicated private cloud-only VNet**
- **Extend your data center With VNets**
- **Enable hybrid cloud scenarios**

## Subnet
Logical division of VNet. Contains a range of IP addresses that fall within VNet (CIDR).
Take care of:
- A service may require unallocated space to create a subnet
- By default, routing goes through the subnets. You can use Network Virtual Appliance.
- Limit access to Azure resources.

## IP addressing
- Public
- Private

Or:
- Static
- Dynamic

SKU of IP must match the Load Balancer SKU.

SKUS (public):
| Feature | Basic SKU | Standard SKU |
| ------- | --------- | ------------ |
| IP assign | Static/Dynamic | Static |
| Security (default) | Open | Secure & closed to inbound traffic |
| Resources | Net interfaces, VPN Gateways, App Gateways, Internet-facing LB | Net interfaces, Public std LB| 
| Redudancy | No | Yes |

Private can be assigned to:
- VM
- Internet Load Balancer
- App Gateway

If dynamic, next available space. Static can be any.

Azure reserves the first 4 address in each subnet address range.