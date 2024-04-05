# Network Latency Monitoring 

## Introduction
Network latency plays a pivotal role in the performance and perceived quality of many applications. With the increasing demand for interactive and real-time applications, monitoring latency continuously and efficiently has become crucial. The ePPing tool, leveraging eBPF technology, provides a solution for passive monitoring of network latency on Linux devices.

## Problem Statement
Customers of Azure AKS face challenges in monitoring latency metrics for namespaces and services running in their clusters. The absence of built-in tools tailored for latency monitoring within AKS clusters impedes customers' ability to gain detailed insights into application latency performance.

### Objective
The objective of this project is to measure the latencies of existing TCP traffic using the ePPing tool, integrate it into an Azure AKS cluster, and provide pod-level latency metrics. The project also aims to visualize and monitor these metrics using Prometheus and measure overall system performance.

### Constraints & Assumptions
- TCP traffic must be actively flowing to accurately calculate Round-Trip Time (RTT).
- Explicit network declaration is necessary when executing the ePPing tool.
- ePPing tool runs exclusively on Linux systems due to Windows' lack of native support for TCP timestamps.
### Impact
- Passive monitoring with ePPing minimizes latency introduced by traffic injection, enhancing overall network performance.
- ePPing's integration into Azure AKS clusters provides customers with essential latency monitoring capabilities, improving their ability to ensure quality service delivery.
### Goals
- Install and run ePPing on an AKS cluster.
- Adapt the tool to provide namespace-level metrics.
- Package and integrate metrics into Prometheus and Grafana.
- Measure CPU/memory usage and network performance.

<img width="525" alt="Screenshot 2024-04-06 012337" src="https://github.com/Harshita0008/Network-Latency-Tool/assets/106453092/e5ad8433-fba7-4d95-9fdd-f3fda622705a">

### In Scope
- Assessing latencies of active TCP traffic without performance impact.
- Packaging and integrating ePPing into Azure AKS clusters.
- Visualizing metrics with Prometheus and Grafana.
- Monitoring system performance.
### Out of Scope
- Transforming the tool into a Kubernetes Gadget.
- Expanding tool capabilities beyond latency monitoring.
### Current Design
The ePPing tool, utilizing eBPF, passively monitors TCP traffic to calculate RTTs. It compares responses to previously re!
corded packets, utilizing TCP timestamps for identification.

<img width="480" alt="Screenshot 2024-04-06 012252" src="https://github.com/Harshita0008/Network-Latency-Tool/assets/106453092/e108de72-c5c5-4d90-b590-93ff70a529da">


### Detailed Design
Initial attempts involved deploying ePPing with Cilium on Azure AKS, which proved unsuccessful due to compatibility issues.
Deploying ePPing on a different cluster using Azure networking provided successful integration.
Analyzing pod-level latency metrics provided insights into application performance.
Integrating ePPing metrics with Prometheus and Grafana enables comprehensive monitoring.
### Data Contract
The ePPing tool captures various latency metric attributes including source/destination IPs, ports, timestamps, RTTs, packet counts, and more.

<img width="515" alt="Screenshot 2024-04-06 012314" src="https://github.com/Harshita0008/Network-Latency-Tool/assets/106453092/0751e643-f0f6-4927-a74b-28c2cde02d1b">


## Future Objectives
Explore expanding ePPing capabilities to support additional protocols and data types.
Investigate the impact of passive monitoring on end-to-end latency and optimize accordingly.
## Conclusion
The integration of ePPing into Azure AKS clusters empowers customers with efficient latency monitoring capabilities, facilitating enhanced performance management and optimization.

#### Epping-tool
https://github.com/xdp-project/bpf-examples/tree/master/pping
