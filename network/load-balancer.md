# Load Balancer
HA, net performance. **Distributes inbound traffic** to backend resources using:
- **Load-balacing rules**: determines how traffic is distributed.
- **Health probes**: ensure the resources in the backend are healthy.

## Types
**Public**: maps the public IP address & port # of incoming traffic to the private IP address & port # of a VM.


**Internal**: directs traffic to resources withina a VNet or that use a VPN.
Types:
- Within a VNet
- Cross-premises VNet
- Multi-tier apps
- Line-of-business apps

## SKUs
- **Basic**
- **Standard** (newer, expaned and + granular)

| Feature | Basic | Std |
| ------- | ----- | --- |
| Backend pools (instances) | Up to 300 | Up to 100 |
| Health probes | HTTP, TCP | HTTPS, HTTP, TCP |
| AZs | Not | Zone-red & zonal frontends |
| Multiple front ends | Inbound | In and out |
| Secure (default) | Open | Closed to inbound, internal allowed |
| SLA | No | 99.99% |

## Backend ppols
Contains Ip addreses of the virtual NICs connected to the LB. 

Endpoints:
- Basic: VMs in a single Availability Set or VM Scale Set
- Std: Any VM in a single VNet. Blend of VMs, availability sets and VMs scale sets.

## Load Balancer rules
It maps a given frontend IP and port combination to a set of backend IP addresses and port
combination. First create:
- Health probe
- Frontend
- Backend

Distributes equally. 5-tuple hash to map traffic:
- Source IP
- Source Port
- Destination IP
- Destination Port
- Protocol Type

Session persistence:
- None: by any
- Client IP: same client IP -> same VM
- Client IP & Protocol: same client IP & protocol -> same VM

## Health probe
Monitor the status of your app. Dynamically add/remove VMs from the LB rotation based on their response to
health checks. If a probe fails to respond, the LB stops sending new connections to unhealthy instances.

Two ways:
- **HTTP custom probe**: Probes your endpoint (default, every 15 secs). It should respond with an HTTP 200
within the timeout period (31 secs). Port, URI, interval, # of failures.
- **TCP custom probe**: Establishing a successful TCP session to a defined probe port. Port, Interval, Unhealthy
threshold.