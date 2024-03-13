# Networking

## IP Addressing and CIDR Blocks

### IP
- IPv4 (32-bit) and IPv6 (128-bit)
- Address of device on an IP network.
- 4 octet notation
  - 192.168.2.1
- 2 parts
  - Routing Prefix
  - Device Identifier
- Routing prefix specified in CIDR notation
  - 192.168.2.1/24
  - 24 bits used for routing prefix/subnet - represented by CIDR
  - 8 bits used for device address - Hosts

### CIDR
- Classless Inter-Domain Routing
- Represents block of addresses
- Number after slash in IP address determines number of available address in block.
- Examples:
  - 192.168.1.0/20 -> 2^(32-20) = 2^12 = 4096 hosts or addresses
  - Larger the CIDR block, lesser are the addresses.

## Load Balancers
- Three main types:
  1. **Application Load Balancer (HTTP/HTTPS):** Layer 7 load balancing for HTTP and HTTPS applications
  2. **Network Load Balancer (TCP/SSL):** Layer 4 load balancing or proxy for applications that rely on TCP/SSL protocol 
  3. **Network Load Balancer (UDP/Other Protocols):** Layer 4 load balancing for applications that rely on UDP protocol
 
### Frontend Configuration:
Configure the load balancer's frontend IP address, port, and protocol. Configure an SSL certificate if using HTTPS.
### Backend Configuration
Create or select a backend service for incoming traffic. You can add multiple backend services and backend buckets to serve different types of content. Backend service can be an instance group. A health check can be configured for backend service.

### Load Balancing Characteristics
1. Global vs Regional
2. External vs Internal
3. Traffic Type

### Global Load Balancers
- Used when workload is distributed globally or across multiple regions.
- All global load balancers are external facing.
- Requires Premium Tier Networking.

- 3 Global Load Balancers:
  - **HTTP(S)** for HTTP and HTTPS Traffic
  - **TCP Proxy** for other TCP Traffic
  - **SSL Proxy** for non-HTTPS SSL/TLS traffic
    
### Regional Load Balancers
- Used when workload is distributed within a region.
- 2 Regional Load Balancers:
  - **Internet TCP/UDP** balances TCP and UDP traffic on private networks in GCP.
  - **Network TCP/UDP** balances SSL and TCP traffic not supported by SSL Proxy or TCP Proxy.
 
### How to Set up a Load Balancer
- We need an Instance Group First.
- Then in Network Services, create a Load Balancer (Application one).
- It can be global or regional or classic
- Regional requires you to reserve a subnet
- Create frontend config and in backend config, set a backend service containing the instance group we created earlier.

## Cloud DNS
- Cloud DNS is a high-performance, resilient, global Domain Name System (DNS) service that publishes your domain names to the global DNS in a cost-effective way.
- Cloud DNS lets you publish your zones and records in DNS without the burden of managing your own DNS servers and software.
- Cloud DNS offers both public zones and private managed DNS zones. A public zone is visible to the public internet, while a private zone is visible only from one or more Virtual Private Cloud (VPC) networks that you specify.

- When you create a DNS, two records are automatically created: NS and SOA
- NS is for keeping track of name servers.
- SOA is authority record.

- First we create a zone either public or private.
- Then we can choose which record to create once we have created our Domain.
- If we want to map an ip to this domain, then A record.
- If we want to map a canonical name to this domain, then CNAME.
