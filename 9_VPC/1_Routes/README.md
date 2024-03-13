# Routes in GCP
- Route is a mapping of an IP address to a Destination. It tells the network where to send the traffic.
- **Routes govern the traffic leaving a resource like a VM and going to other destinations.** Destinations can be inside your GCP VPC or outside it.

- **The default VPC has a default Route to the internet and individual Routes to each subnet.**
- Routes are considered "network resources" and cannot be shared between projects or networks.
- **The existence of route does not mean that a packet will get to the destination. Firewall has to be configured to allow the traffic through.**
- In a VPC network, a route consists of a single destination and a single next hop. When an instance in a VPC network sends a packet, Google Cloud delivers the packet to the route's next hop if the packet's destination address is within the route's destination range.
- Google is not using any physical device for Routing.
- VPC Routing is completely software based and managed by **Routing Table** defined at VPC level.
- In GCP each instance has a Controller that is kept informed of all applicable Routes from network's Routing Table.
- Each packet leaving an instance is delivered to the appropriate next hop of an applicable Route based on a routing order. Any addition or deletion in routes is automatically propagated in VM's Controller.
- **In VPC, user can have System Generated Routes or Custom Routes.**
### System Generated Routes:
**Default VPC has two types of System Generated Routes: Default Route and Subnet Route**
#### Default Route: 
Path out of VPC network including path to Internet.
- System Generated Default Route has a priority of 1000.
- To isolate the network from Internet, user needs to delete the default Route in VPC.
- Default Routes have a Next Hop that is **Default Internet Gateway.**
#### Subnet Route:
These are system-generated routes that define paths to each subnet in the VPC network.
- Each subnet has at least one subnet route whose destination matches the primary IP range of the subnet.
- User cannot delele a subnet route unless taht subnet is modified or deleted.

### Custom Routes:
Custom Routes are either static routes that you create manually or dynamic routes that are maintained automatically by one or more of your Cloud Routers.

## Cloud Router
**Google Cloud Router is a fully managed, software-defined router that enables dynamic routing between your Virtual Private Cloud (VPC) network and other networks. It uses the Border Gateway Protocol (BGP) to advertise and learn IP prefixes.**

### Dynamic Routing with Google Cloud Router 
- It allows you to automatically configure routes between your VPC network and other networks, based on Border Gateway Protocol (BGP) advertisements. This can simplify your network configuration and make it more flexible and scalable.
- To use dynamic routing with Google Cloud Router, you must first create a Cloud Router and enable dynamic routing. Once you have done this, you can configure peering connections between your Cloud Router and other BGP routers, such as on-premises routers or routers in other cloud providers’ networks.
- Once you have configured peering connections, your Cloud Router will start exchanging BGP advertisements with the other routers. This will allow your Cloud Router to learn about the IP prefixes that are available on the other networks. Your Cloud Router will then automatically create routes to these IP prefixes.

[Cloud Router in Detail](https://bgiri-gcloud.medium.com/google-cloud-networking-part-2-0a262b226f9b)
