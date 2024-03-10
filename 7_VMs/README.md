# Cloud Compute Engine

Google Compute Engine is a virtual machine (VM) service that allows users to create and run VMS on Google’s infrastructure. Compute Engine provides a variety of VM types, including standard, high-memory, high-CPU, and custom machine types. A default Compute Service Account is associated with VMs when we create them.

## Machine Types
- There are several types of machine families:
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
gcloud compute instances create instance-20240310-105520 --zone=us-central1-a --machine-type=e2-micro 
```
We can also checkout the equivalent code section in Google Cloud. It gives us commands that we can run as well as Terraform code and REST API calls


