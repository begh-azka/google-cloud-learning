# GCP Regions and Zones

- GCP is organized into **Regions** and **Zones**.
- Any Resource in Google Cloud can either be **Regional**, **Zonal** or **Global**.
  
### Zones
- **They are isolated locations in a region.**
- They have high bandwidth, low-latency network connections to other zones in the same region.
- Zonal resources operate within a single zone. Zonal outages can affect some or all of the resources in that zone.
- For High Availability of an application, resources should be deployed in multiple zones within a region.
  
### Regions
- **They are independent geographic areas that are made up of one or more zones.**
- Regional Resources are redundantly deployed across multiple zones within a region.

### Global Resources
- Resources that can be accessed regardless of zone or location.
