# Cloud Compute Engine

Google Compute Engine is a virtual machine (VM) service that allows users to create and run VMS on Google’s infrastructure. Compute Engine provides a variety of VM types, including standard, high-memory, high-CPU, and custom machine types. A default Compute Service Account is associated with VMs when we create them.

## Machine Types
There are several types of machine families:
1. **General purpose machine types:**
   - Machines with a general purpose are the most prevalent and can handle a variety of workloads.
   - They come in various sizes and offer a balance of CPU and memory resources.
   - **n1-standard**, **e2-standard**, and **e2-highcpu** are some examples.
2. **Compute-optimized machine types:**
   - These are made to handle workloads that demand on a lot of memory.
   - Compared to general-purpose computers, they feature a larger memory-to-CPU ratio.
   - **N1-highmem** and **e2-highmem** are two examples.
3. **CPU-optimized machine types:**
   - These are developed for applications like video transcoding, gaming, and simulation that demand a lot of CPU power.
   - They have more virtual CPUs per unit of RAM than general-purpose computers.
   - **N1-highcpu** and **e2-highcpu** are two examples.
4. **Accelerated computing machine types:**
   - These are produced for activities that call for **specialized hardware**, such GPUs or TPUs.
   - They are enhanced for scientific computing, machine learning, and deep learning.
   - Examples include **n1-highmem-96** and **n1-standard-gpu**.
- There are storage and memory optimised machines as well.
![image](https://github.com/begh-azka/google-cloud-learning/assets/97597065/2699f457-026d-47ab-9abd-384876e55d4e)

### Machine Configuration
Options available are:
- General Purpose
- Compute Optimized
- Memory Optimised
- GPUs (Graphic Processor Units)
- Storage Optimized

### Machine Type
- Machine type can be **Preset** or **Custom** (where you can set no of vCPU and Memory)
- In preset, you have **Shared Core**, **High CPU**, **High Memory** and **Standard** options.
  
### VM Provisioning Models
VM Provisioning Models are of two types:
1. **Standard**
2. **Spot**: Preemptive machines that can be terminated at any time by Google.

### Boot Disk
- Here you can select what kind of machine image you want: **public** or **custom**.
- Snapshots, Archive Snapshots and Existing Disks are some of the other options available.
- In public image, you can select the **Operating System** of your VM, its version, its disk size and boot disk type.

### Access Scopes
- We can select the type and level of API access to grant the VM.
- It can have default access. Default contains Read-only access to Storage and Service Management, Write access to Stackdriver Logging and Monitoring, Read/Write access to Service Control.
- It can have full access to all Cloud APIs
- It can have access to selective APIs

### Observability - Ops Agent
- To collect more metrics, ops agent can be installed on our VMs.

## Create VMs
1. Through Console
2. Via Google sdk or shell
3. Terraform
4. REST API Calls

### Commands using Cloud SDK
Once Cloud SDK is installed on your system, you will be able
```
gcloud compute instances create instance-name --zone=us-central1-a --machine-type=e2-micro 
```
We can also checkout the equivalent code section in Google Cloud. It gives us commands that we can run as well as Terraform code and REST API calls

### Advanced Configuration
- VMs can be attached with an addition boot disk. This can be done in Advanced Options of google console while creating a VM.
- We can also attach a snapshot of another VM's disk to a new VM.
- Boot Disk that can be attached can be **blank** or an **image** or **archive snapshot** or just a **snapshot**.
- **Disk Type can be Balanced Persistent Disk, Extreme Persistent Disk, SSD Persistent Disk and Standard Persistent Disk.**
- **Standard has fewest read and write IOPS per second and Extreme/SSD has the most and Balanced is in the middle.**
- VMs can be put in a custom VPC and a subnet of your choice. **This is done in Advanced Options -> Networking -> Network Interfaces.**
- We can add labels (tags) to our VMs and Disks.
- We can specify if we want to keep the disk or delete it (default) after we delete a VM in advanced options.

### Snapshots
- To take snapshots of your VM's Disk, go to the toggle on the RHS in Compute Engine and there you can select Snapshots.
- Snapshots can be simple Snapshots (Standard backup and disaster recovery; stored in a separate location from your disk), Instant Snapshots (Rapid restoration; stored in the same location as your disk) or Archive Snapshots (for long-term storage).

### Spot Instances
- Preemptive
- Cheaper that standard
- Ideal for fault-tolerant workload (Those that don't lose data if a node or resource fails - GKE)
- GKE can use this.
- We can use Managed Instance Groups in Compute Engine for spot instances. They are a collection of identical nodes. If one fails other has similar set up (so HA) so the other is used if google takes away a spot instance.

## Managed Instance Groups

### Instance Group:
- Collection of Instances that are managed as a single entity.
- **Two Types:**
  - Managed Instance Group
  - Unmanaged Instance Group
    
### Managed Instance Group
- Multiple Identical VMs
- Configuration defined in instance template
- Types: Stateful and stateless
- Features include:
  - Autoscaling
  - Autohealing
  - Multi-zone Deployment
  - Auto-updating (Patching)

### Unmanaged Instance Group
- Multiple (possibly Heterogenous VMs)
- Used to apply load balancing across heterogeneous group of instances.
- In general, recommended for legacy clusters only
- No autoscaling, autohealing, or auto-patching

### To Create Instance Groups
- Go to RHS of compute cloud and select instance groups.
- Create a Launch Template with the required Configuartion.
- We can keep it in multi-zone or single zone
- Autoscaling can be turned on or off. If On then max and min can be set. Target utilization can be set as well which will indicate when instances can be scaled out or down. Target Utilization -> CPU utilization, HTTP load balancing servicing capacity, Stackdriver metrics.
  - Cool Down Period is allowed for instances to finish initializing before metrics are taken.
  - Stabilization period is time autoscaler uses to calculate MIGs recommended target size.
  - Avoids thrashing i.e rapidly adding and removing instances.
- Healthcheck can be configured and protocol/port can be specified. Check interval and Healthy Threshold need to be specified with a timeout.
