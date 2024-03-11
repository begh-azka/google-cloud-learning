# Firewall
- Firewall Rules let you allow or deny traffic to and from your virtual machine based on configuration that you specify.
- They are defined at the network level, but connections are allowed or denied on a per-instance basis.
- They don't just exist between your instances and other networks, but also between individual instances within the same network.
- Firewalls are stateful.
- **Each Firewall Rule has priority (0-65535) assigned to it. 0 has the highest priority.**
- They can be Allow or Deny Rules.
  
### Default Implied Rules:
- **Every VPC network has two Implied Firewall Rules that block all incoming connections and allow all outgoing connections.**
- These rules exist but are not visible in Console.
- **Default Implied Rule has the lowest priority (65535).** These rules:
  - Allow all Egress
  - Deny all Ingress
  - Cannot be deleted.
  - Can be overriden by defining new rules with priority 0-65535.
 
## Firewall Rules for a Default Network
**Default Network** has **4** pre-populated rules with **priority 65535:**
  - Allow incoming traffic from VM instances in same network (same VPC) - **default-allow-internal**.
  - Allow incoming TCP traffic on port 22 (ssh) - **default-allow-ssh**
  - Allow incoming traffic on port 3389 (RDP) - **default-allow-rdp**
  - Allow incoming ICMP from any source on the network - **default-allow-icmp**

## Firewall Components
1. Direction of Traffic
2. Numerical Priority
3. Action on Match (Determines whether the Rule permits or blocks traffic)
4. Enforcement Status of the Firewall Rule (Enable or Disable F/W Rules)
5. Target (Instance to which a Rule applies)
6. Source for Ingress Rules or Destination for Egress Rules
7. Protocol and Port
   
### Priority of Rules
- If we created an ICMP allow rule with apriority of 1000 and later created a firewall rule with priority of 900 to deny icmp traffic, then icmp will be blocked because deny rule has a higher priority compared to allow rule.

## Configure a Firewall
You can configure your own firewall rules:
1. **Ingress Rules:** Rules for Incoming traffic from outside to GCP targets.
   - **Target (defines the destination):** All instances or instances with Tag/SA
   - **Source (defines where traffic is comingfrom):** CIDR or All instances/instances with TAG/SA.
      
2. **Egress Rules:** Rules for Outgoing traffic to destination from GCP targets
   - **Target (defines the source):** All instances or instances with Tag/SA.
   - **Destination:** CIDR Block
 
Users can use Service Accounts to create Firewall Rules that are more specific in nature. To get strict control over Firewall Rules, use Source and Target Service Accounts instead of Target Tags and Source Tags. Users cannot mix and match service accounts and network tags in any firewall rule. Example: Create a rule and keep source as Network tags. Then all the VMs with those tags will come under that rule.

## Forwarding Rules
- While routes govern traffic leaving an instance, **forwarding rules direct traffic to a Google Cloud resource in a VPC network** based on IP address, protocol, and port.
- Some forwarding rules direct traffic from outside of Google Cloud to a destination in the network; others direct traffic from inside the network.
- **Destinations** for forwarding rules are **target instances**, **load balancer targets** (target proxies, target pools, and backend services), and **Cloud VPN gateways**.
