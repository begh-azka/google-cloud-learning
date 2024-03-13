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
  
