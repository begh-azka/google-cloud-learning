# Google Kubernetes Engine

- Managed Service
- Provides Kubernetes Clusters

## Features of GKE
- Load Balancing of Workloads
- **Node pools to Segment Nodes within a Cluster**. Example: One pool contains nodes equipped with build agents and another pool contains nodes equipped with deployment tools.
- **Automatic Scaling and Updating:** Based on the particular user’s CPU utilization and other custom metrics, Google provides **horizontal pod autoscaling** (adjusting the number of machines based on requirements) and based on CPU and memory usage, **vertical pod autoscaling** (varying the power of available machines).
- Autohealing
- Cloud Monitoring and Cloud Logging
- **Standard and Autopilot Modes.** In Autopilot, GCP will take responsibilty for figuring out what is an optimal configuration of nodes for us and allocate pods accordingly.

## Kubernetes Architecture
![image](https://github.com/begh-azka/google-cloud-learning/assets/97597065/eb63b3a6-e14e-47ab-9a6d-78678d5e2827)

