# Interconnection of Networks (Hybrid Cloud computing)
[VPC Peering GCP](https://cloud.google.com/vpc/docs/using-vpc-peering)

Interconnection means connecting your cloud platform with other VPC networks, it could be another cloud network or an on-premise Network.

Google provides three-types of interconnections:
1. Cloud VPN
2. Dedicated Interconnect
3. Partner Interconnect or Peering

## Cloud VPN
- It securely connects your peer network to your Virtual Private Cloud (VPC) network through an **IPsec VPN Tunnel**. Upto 3Gbps.
- Traffic through **Internet** (public) but it is encrypted using **Internet Key Exchange Protocol**. Latency issue as internet is involved.
- Traffic travelling between two networks is encrypted by one VPN Gateway and then decrypted by the other VPN Gateway.
- This protects your data as it travels over the internet. You can also connect two instances of cloud VPN to each other.
- Google Cloud offers two types of Cloud VPN Gateway: **HA VPN** and **Classic VPN**

### 1. HA VPN
- HA VPN is a high availability (HA) Cloud VPN solution that lets you securely connect your on-premises network to your cloud VPC through an IPsec VPN connection in single region.
- It provides an SLA of 99.99% service availability with two external IP addresses.
- Users do not need to create any forwarding rules for HA VPN Gateways.
- Only dynamic routing (BGP) supported.

### 2. Classic VPN
- Classic VPN Gateways have a single interface, a single external IP address, and uses dynamic or static routing.
- Slow compared to HA Cloud VPN

## Cloud Interconnect
- High speed physical connection between on-premise and VPC networks:
- This provides high availability and high throughput.
- Two types of communications possible:
  1. **Dedicated/Direct Interconnect -** min 10 Gbps.
  2. **Partner Interconnect -** min 50 Mbps.

- Data Exchange happens through a private network:
  - Communication using VPC network's internal IP addresses from on-premise network.
  - Reduces egress cost as public internet is not used
- Supported Google APIs and services can be privately accessed from on-premise.
- Used only for high bandwidth needs:
  - For low bandwidth, Cloud VPN is recommended.

## Direct Peering
- Connect customer network to google network using network peering.
- Not a GCP Service.
- Not recommended. Low level.


## Shared VPC
- **Scenario:** Your organization has multiple projects. You want resources in different projects to talk to each other. How to allow resources in different projects to talk with internal IPs securely and efficiently?
  - **This is done by a Shared VPC.**
    
- Created at **organization** or **shared folder** level (Access Needed: Shared VPC Admin)
- Allows VPC network to be shared between projects in the same organization.
  
- Shared VPC contains one **host project** and **multiple service projects**
  - **Host Project:** Contains Shared VPC network.
    
  - **Service Projects:** Attached to Host projects.
 
- Helps you achieve **separation of concerns:** 
  - **Network Administrators** are responsible for Host Projects and **Resource Users** use Service Projects.
 
## VPC Peering

- **Scenario:** How to connect VPC networks across different organizations?
  - **This is done by VPC Peering.**

- Networks (VPCs) in same project, different projects and across projects in different organizations can be peered.
- **All communications happen using Internal IPs.** This is:
  - Highly efficient because all communication happens inside Google Network.
  - Highly secure because it is not accessible from the internet.
  - No charges for data transfer between services.

- **Network Administration is NOT changed.**
  - Admin of one VPC does not automatically assume the same role in the peered network.
