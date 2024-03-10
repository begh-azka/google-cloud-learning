# Cloud Compute Engine

Google Compute Engine is a virtual machine (VM) service that allows users to create and run VMS on Google’s infrastructure. Compute Engine provides a variety of VM types, including standard, high-memory, high-CPU, and custom machine types.

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

### VM Provisioning Models
- VM Provisioning Models are of two types:
1. Standard
2. Spot: Preemptive machines that can be terminated at any time by Google.


