# VPC
- **A virtual private cloud (VPC) is a secure, isolated private cloud hosted within a public cloud.**
- A VPC is a virtual network that closely resembles a traditional network that you'd operate in your own data center. After you create a VPC, you can add subnets.
- It runs on shared infrastructure like a public cloud does but isolates customers from each other.
- VPC resources are then reserved for use for each specific customer. The isolation creates a private and more secure public cloud.

## Google Cloud VPC
VPC networks have the following properties:
- **VPC networks including their associated Routes and Firewall rules are Global resources. They are not associated with any particular region or zone.**
- **Subnets are Regional resources.** Each subnet defines a range of IP addresses.
- Traffic going in or out of instances can be controlled with network Firewall Rules.
- A Network Administration can be secured by using Cloud IAM roles.
- An organization can use Shared VPC to keep a VPC network in a common host project.
- VPC networks can be securely connected in hybrid environments by using Cloud VPN or Cloud Interconnect.

## Subnets
- Each VPC network consists of one or more useful **IP range partitions** called **subnets**.
- Each subnet is associated with a region.
- A network must have at least one subnet before you can use it.
- VPC networks do not have any IP address ranges associated with them, IP ranges are defined for the subnets. Subnets are regional resources. **Each subnet defines a range of IP addresses.**
![image](https://github.com/begh-azka/gcp/assets/97597065/4d159a6e-f621-4519-a0dd-27a5eeee4c0d)

### Need for VPC Subnets
Different types of resources are created in cloud such as databases, compute, etc. Each type of resource has its own **access needs**. Some of them are **public** and some are **private resources**.
        
1. **Subnets are needed to separate Public Resources from Private Resources inside a VPC**
     - Public resources (Load Balancers) can be accessed from outside and should be kept in public subnets while as resources like database VMs should be kept in private subnets.
2. **We need Subnets in order to distribute resources across multiple regions for High Availability.**

### Creating VPCs and Subnets in GCP
Google Cloud offers three types of VPC networks, determined by their subnet creation mode:
- **Default-mode VPC**
- **Auto-mode VPC**
- **Custom-mode VPC**

1. **Default-mode VPC:**
   - Every project is provided with a Default VPC network with **Preset Subnets and Firewall Rules**.
   - Specifically, a subnet is allocated for each region with non-overlapping CIDR blocks and firewall rules that allow ingress traffic from ICMP, RDP, and SSH traffic from anywhere, as well as ingress traffic from within the default network for all protocols and ports

2. **Auto-mode VPC:**
   - Subnets are **automatically** created in each region.
   - Default VPC created automatically in the project uses auto model.

3. **Custom-mode VPC:**
   - Subnets are **NOT automatically** created.
   - You have complete control over subnets and their IP ranges.
   - *Recommended for Production*.

### Options While Creating a Subnet:
1. **Enable Private Google Access -** Set whether VMs in a subnet can access Google services without assigning external IP addresses. Allows `VMs` to connect to *`Google Services`* using `private IPs`. Using private IPs, communication happens within a network.
2. **Enable FlowLogs -** To troubleshoot any VPC related network issues.
3. **Enable Hybrid Subnets:** Allowing hybrid subnet modifies the VPC network routing behavior to allow overlap between the subnet's IP address range and those of custom dynamic routes.
