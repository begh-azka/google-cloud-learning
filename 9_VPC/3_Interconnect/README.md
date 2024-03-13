# Interconnection

Interconnection means connecting your cloud platform with other VPC networks, it could be another cloud network or an on-premise Network.

Google provides three-types of interconnections:
1. Cloud VPN
2. Dedicated Interconnect
3. Partner Interconnect or Peering

## Cloud VPN
- It securely connects your peer network to your Virtual Private Cloud (VPC) network through an **IPsec VPN Tunnel**.
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
  1. **Dedicated Interconnect -** 10 Gbps or 100 Gpbs configurations.
  2. **Partner Interconnect -** 50 Mbps to 10 Gbps configuration.

- Data Exchange happens through a private network:
  - Communication using VPC network's internal IP addresses from on-premise network.
  - Reduces egress cost as public internet is not used
- Supported Google APIs and services can be privately accessed from on-premise.
- Used only for high bandwidth needs:
  - For low bandwidth, Cloud VPN is recommended.

## Direct Peering
- Connect customer network to google network using network peering.
- Not a GCP Service.
- Not recommended.
