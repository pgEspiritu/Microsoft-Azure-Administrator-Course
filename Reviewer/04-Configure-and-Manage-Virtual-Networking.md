# AZ-104 Reviewer
# Domain: Configure and Manage Virtual Networking

---

# 📚 Exam Coverage

This domain covers:
- Virtual Networks (VNets)
- Subnets
- Network Security Groups (NSGs)
- DNS
- VNet Peering
- Azure Load Balancer
- Application Gateway
- Azure Firewall
- Azure Bastion
- VPN Gateway
- ExpressRoute
- Routing
- Private Link and Endpoints
- Network Watcher

Weight in Exam:
15–20%

---

# 🌐 Azure Networking Overview

Azure networking enables:
- Secure communication
- Internet connectivity
- Hybrid connectivity
- Traffic management
- High availability

---

# 🔹 Networking Components

| Component | Purpose |
|---|---|
| VNet | Private network |
| Subnet | Network segmentation |
| NSG | Traffic filtering |
| Route Table | Custom routing |
| Load Balancer | Traffic distribution |

---

# 🏢 Virtual Network (VNet)

Azure Virtual Network provides private networking in Azure.

---

# 🔹 VNet Features

| Feature | Description |
|---|---|
| Isolation | Private network |
| Communication | Azure resource connectivity |
| Internet Access | Outbound connectivity |
| Hybrid Connectivity | VPN/ExpressRoute |

---

# 🔹 VNet Address Space

Uses CIDR notation.

Example:
```text
10.0.0.0/16
```

---

# 🔹 Private IP Address Ranges

| Range |
|---|
| 10.0.0.0 – 10.255.255.255 |
| 172.16.0.0 – 172.31.255.255 |
| 192.168.0.0 – 192.168.255.255 |

---

# 🔹 Subnets

Subnets divide VNets into smaller segments.

Example:
```text
10.0.0.0/16
 ├── Frontend: 10.0.1.0/24
 └── Backend: 10.0.2.0/24
```

---

# 🔹 Azure Reserved IP Addresses

Azure reserves first 4 and last IP in subnet.

Example:
```text
10.0.1.0/24
```

Reserved:
```text
10.0.1.0
10.0.1.1
10.0.1.2
10.0.1.3
10.0.1.255
```

---

# 🔹 Public IP Addresses

Provides internet connectivity.

---

# 🔹 Public IP SKUs

| SKU | Description |
|---|---|
| Basic | Legacy |
| Standard | Secure and recommended |

---

# 🔹 Public IP Assignment

| Type | Description |
|---|---|
| Static | Fixed IP |
| Dynamic | Changes when restarted |

---

# 🔐 Network Security Groups (NSGs)

Acts as Azure firewall for traffic filtering.

---

# 🔹 NSG Features

| Feature | Description |
|---|---|
| Inbound Rules | Incoming traffic |
| Outbound Rules | Outgoing traffic |
| Allow/Deny | Traffic control |

---

# 🔹 NSG Rule Components

| Component | Description |
|---|---|
| Priority | Rule order |
| Source | Traffic origin |
| Destination | Traffic target |
| Port | Service port |
| Protocol | TCP/UDP |

---

# 🔹 NSG Rule Priority

Lower number = Higher priority.

Example:
```text
100 → Processed before 200
```

---

# 🔹 Default NSG Rules

Azure automatically creates:
- Allow VNet traffic
- Allow Azure Load Balancer
- Deny all inbound internet traffic

---

# 🔹 NSG Association

Can associate to:
- Subnet
- NIC

---

# 🔹 Effective NSG Rules

Combined rules from:
- Subnet NSG
- NIC NSG

---

# 🌍 Azure DNS

Provides DNS hosting and name resolution.

---

# 🔹 DNS Record Types

| Record | Purpose |
|---|---|
| A | Maps hostname to IPv4 |
| AAAA | IPv6 |
| CNAME | Alias |
| MX | Mail |
| TXT | Verification |

---

# 🔹 Public DNS Zones

Internet-facing DNS records.

---

# 🔹 Private DNS Zones

Internal VNet name resolution.

---

# 🔹 Azure-Provided DNS

Default DNS service in VNets.

IP:
```text
168.63.129.16
```

---

# 🔗 VNet Peering

Connects VNets privately using Azure backbone.

---

# 🔹 VNet Peering Features

| Feature | Description |
|---|---|
| Low Latency | Azure backbone |
| Private Communication | No internet |
| High Bandwidth | Fast connectivity |

---

# 🔹 Peering Types

| Type | Description |
|---|---|
| Regional | Same region |
| Global | Different regions |

---

# 🔹 Peering Limitations

- Transitive routing not automatic
- Overlapping IP ranges not allowed

---

# ⚖️ Azure Load Balancer

Layer 4 load balancing (TCP/UDP).

---

# 🔹 Load Balancer Types

| Type | Description |
|---|---|
| Public | Internet-facing |
| Internal | Private traffic |

---

# 🔹 Load Balancer Components

| Component | Purpose |
|---|---|
| Frontend IP | Entry point |
| Backend Pool | Target servers |
| Health Probe | Checks availability |
| Load Balancing Rule | Traffic distribution |

---

# 🔹 Load Balancer Features

- High availability
- Automatic failover
- Zone redundancy

---

# 🌐 Azure Application Gateway

Layer 7 web traffic load balancer.

---

# 🔹 Application Gateway Features

| Feature | Description |
|---|---|
| URL Routing | Route by path |
| SSL Termination | Offload encryption |
| WAF | Web protection |
| Cookie Affinity | Session persistence |

---

# 🔹 WAF (Web Application Firewall)

Protects against:
- SQL Injection
- Cross-site scripting (XSS)
- OWASP attacks

---

# 🔹 Load Balancer vs Application Gateway

| Feature | Load Balancer | App Gateway |
|---|---|---|
| OSI Layer | Layer 4 | Layer 7 |
| URL Routing | ❌ | ✅ |
| WAF | ❌ | ✅ |
| HTTPS Offload | ❌ | ✅ |

---

# 🔥 Azure Firewall

Managed stateful firewall service.

---

# 🔹 Azure Firewall Features

| Feature | Description |
|---|---|
| Centralized Security | Single firewall |
| Application Rules | FQDN filtering |
| Network Rules | IP filtering |
| NAT Rules | Address translation |

---

# 🔹 Firewall Types of Rules

| Rule | Description |
|---|---|
| Application Rule | Web traffic |
| Network Rule | TCP/UDP traffic |
| NAT Rule | Port forwarding |

---

# 🛡️ Azure Bastion

Provides secure RDP/SSH access through browser.

---

# 🔹 Bastion Benefits

- No public IP required
- Secure browser access
- Reduced attack surface

---

# 🔹 Bastion Requirements

Requires dedicated subnet:
```text
AzureBastionSubnet
```

---

# 🔌 VPN Gateway

Encrypted tunnel between Azure and external networks.

---

# 🔹 VPN Types

| Type | Description |
|---|---|
| Site-to-Site (S2S) | Office to Azure |
| Point-to-Site (P2S) | Client to Azure |
| VNet-to-VNet | Azure network connection |

---

# 🔹 VPN Gateway Requirements

Needs:
- Gateway subnet
- Public IP
- Gateway resource

---

# 🔹 GatewaySubnet

Special subnet for VPN gateway.

Name must be:
```text
GatewaySubnet
```

---

# 🚄 ExpressRoute

Private dedicated connection to Azure.

---

# 🔹 ExpressRoute Benefits

| Benefit | Description |
|---|---|
| Private Connection | No public internet |
| Lower Latency | Faster |
| Higher Reliability | Stable |

---

# 🔹 ExpressRoute vs VPN

| Feature | VPN | ExpressRoute |
|---|---|---|
| Uses Internet | ✅ | ❌ |
| Private Circuit | ❌ | ✅ |
| Lower Latency | ❌ | ✅ |

---

# 🛣️ Routing in Azure

Controls packet forwarding.

---

# 🔹 Route Types

| Type | Description |
|---|---|
| System Routes | Default Azure routes |
| User Defined Routes (UDR) | Custom routes |
| BGP Routes | Dynamic routing |

---

# 🔹 User Defined Routes (UDR)

Custom route tables.

Example:
```text
Route traffic to firewall appliance
```

---

# 🔹 Route Table Association

Can associate route table to:
- Subnet

---

# 🔒 Private Link and Endpoints

Secure private access to Azure services.

---

# 🔹 Private Endpoint

Assigns private IP from VNet.

Benefits:
- Private connectivity
- No public internet exposure

---

# 🔹 Service Endpoint

Extends VNet identity to Azure services.

---

# 🔹 Private Endpoint vs Service Endpoint

| Feature | Private Endpoint | Service Endpoint |
|---|---|---|
| Private IP | ✅ | ❌ |
| Most Secure | ✅ | ❌ |
| Public Service Exposure | Minimal | Still public |

---

# 🔍 Network Watcher

Network diagnostic service.

---

# 🔹 Network Watcher Tools

| Tool | Purpose |
|---|---|
| IP Flow Verify | Check NSG rules |
| Connection Troubleshoot | Connectivity issues |
| Packet Capture | Capture traffic |
| NSG Flow Logs | Traffic analysis |

---

# 🔹 Connection Monitor

Monitors network connectivity between endpoints.

---

# 📊 Azure Traffic Manager

DNS-based global traffic distribution.

---

# 🔹 Traffic Manager Routing Methods

| Method | Description |
|---|---|
| Priority | Primary/backup |
| Weighted | Distribution percentage |
| Performance | Lowest latency |
| Geographic | Region-based |

---

# 🌍 Azure Front Door

Global Layer 7 application delivery service.

Features:
- Global load balancing
- CDN
- SSL offload
- WAF

---

# 🔥 Important Exam Concepts

---

# 🔹 NSG Processing

Remember:
- Lower priority number processed first
- Deny overrides later allow rules

---

# 🔹 Subnet Sizing

Azure reserves 5 IP addresses.

---

# 🔹 Connectivity Selection

| Requirement | Solution |
|---|---|
| Secure browser RDP | Bastion |
| Hybrid encrypted tunnel | VPN Gateway |
| Private dedicated connection | ExpressRoute |
| Global DNS load balancing | Traffic Manager |

---

# ⚠️ Common Exam Confusions

---

# Load Balancer vs App Gateway

| Load Balancer | App Gateway |
|---|---|
| Layer 4 | Layer 7 |
| TCP/UDP | HTTP/HTTPS |

---

# NSG vs Azure Firewall

| NSG | Azure Firewall |
|---|---|
| Basic filtering | Advanced centralized filtering |

---

# VPN vs ExpressRoute

| VPN | ExpressRoute |
|---|---|
| Internet-based | Private connection |

---

# Private Endpoint vs Service Endpoint

| Private Endpoint | Service Endpoint |
|---|---|
| Private IP | Public service endpoint |

---

# 🧪 Common Exam Scenarios

---

# Scenario 1

Requirement:
```text
Securely connect on-premises office to Azure over internet.
```

Answer:
```text
VPN Gateway
```

---

# Scenario 2

Requirement:
```text
Provide secure browser-based SSH without public IP.
```

Answer:
```text
Azure Bastion
```

---

# Scenario 3

Requirement:
```text
Load balance HTTPS traffic with WAF protection.
```

Answer:
```text
Application Gateway
```

---

# Scenario 4

Requirement:
```text
Connect VNets privately across regions.
```

Answer:
```text
Global VNet Peering
```

---

# Scenario 5

Requirement:
```text
Provide private access to Azure Storage account.
```

Answer:
```text
Private Endpoint
```

---

# Scenario 6

Requirement:
```text
Diagnose NSG traffic blocking.
```

Answer:
```text
IP Flow Verify
```

---

# 🧠 Memorization Tips

---

# Remember:

## VNet
Private Azure network

## Subnet
Network segmentation

## NSG
Traffic filtering

## Load Balancer
Layer 4

## App Gateway
Layer 7 + WAF

## Bastion
Secure browser RDP/SSH

## VPN Gateway
Encrypted internet tunnel

## ExpressRoute
Private dedicated connection

## Private Endpoint
Most secure service access

---

# 🛠️ Recommended Hands-On Practice

Practice:
- Create VNets and subnets
- Configure NSGs
- Configure DNS zones
- Create VNet peering
- Configure Load Balancer
- Configure Application Gateway
- Configure Azure Firewall
- Deploy Bastion
- Configure VPN Gateway
- Configure route tables
- Create private endpoints
- Use Network Watcher diagnostics

---

# 📖 Official Microsoft Resources

AZ-104 Skills Measured:
https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104/

Azure Networking Documentation:
https://learn.microsoft.com/en-us/azure/networking/

Virtual Network Documentation:
https://learn.microsoft.com/en-us/azure/virtual-network/

Application Gateway Documentation:
https://learn.microsoft.com/en-us/azure/application-gateway/

Azure Firewall Documentation:
https://learn.microsoft.com/en-us/azure/firewall/

VPN Gateway Documentation:
https://learn.microsoft.com/en-us/azure/vpn-gateway/

ExpressRoute Documentation:
https://learn.microsoft.com/en-us/azure/expressroute/
